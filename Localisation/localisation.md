---
layout: default
title: Localisation
nav_order: 1
has_children: false
permalink: /localisation
---


# Localisation
---

Discourse includes an intuitive, incremental and manageable localisation workflow out of the box. This system revolves around the LocalisedText class, which holds a unique ID to key a string across an arbitrary number of languages (each in turn keyed by their corresponding language code [e.g. 'en-us']).

---

To export an Event's strings for localisation, follow these steps:
1. Select the graph asset you want to localise in the project view
1. Right click the asset and select Discourse/Localisation/Export CSV
1. Choose a directory to export the .csv file to.
1. Once the export is complete, open the csv file in your spreadsheet editor of choice (e.g. Microsoft Excel).
1. By default, any language codes listed on your ReferencesDatabase will appear as columns in the file, with rows keyed by a unique ID, containing the localised string for that language. These will be empty unless you have changed between languages in the Editor and edited the text in the PropertyPanel.
1. Make any modifications to the text you see fit, or send it off for localisation.
1. Once the text has been localised, save the CSV, then navigate back to the project.
1. Select the Event asset you exported from, right click it and select Discourse/Localisation/Import CSV.
1. Navigate to where you saved the localised CSV, select it and confirm the file dialogue.
1. The import will shortly complete, and the next time you open the Event Graph you should find your strings have been localised! You can test this by changing the Source Language dropdown on the ReferencesDatabase asset.

---

## Batch Export / Import

To automate the export and import of strings, you can make use of the ReferenceIO class, in `Montebearo.Discourse.DataExport`, which handles the exporting and importing of CSV string collections.

Exactly how you do this is up to you; every project works differently, and you may have a preferred way of automating tools.

Below is an example of a batch export / import tool that finds all DiscourseEvent assets in the project, and exports or imports CSV files to a directory of your choosing.

This is an Editor script, so must be placed inside an Editor folder in your project.

```c#
using System;
using System.IO;
using Montebearo.Discourse;
using Montebearo.Discourse.DataExport;
using UnityEditor;
using UnityEngine;

namespace SampleCode.Editor
{
	public static class BatchImportExport
	{
		// In this example, we assume all DiscourseEvents have unique names. If they don't, you will want to
		// edit this to ensure you can export/import unique files per-event.
		//
		// One way of doing that would be to export the CSVs using the event's project GUID as the file name,
		// and match events to their CSV files based on their guid in the import step.
		// Or you could export to sub-folders matching your project structure.
		//
		// We leave that decision up to you.
		
		private static string FormatEventFileName(DiscourseEvent eventAsset) => $"{eventAsset.name}.csv";

		private static bool TryGetFileDialogDirectory(string title, out string directory)
		{
			// Open the dialog to the Desktop by default.
			string defaultDirectory = Environment.GetFolderPath(Environment.SpecialFolder.Desktop);
			
			directory = EditorUtility.OpenFolderPanel(title, defaultDirectory, "ExportDirectory");
			return directory.Length > 0;
		}
		
		[MenuItem("Tools/Discourse/Batch Export Event Strings")]
		public static void BatchExport()
		{
			// Select a directory to export to
			if(!TryGetFileDialogDirectory("Select Export Directory", out string exportDirectory)) return;

			DiscourseEvent[] eventAssets = GetProjectEvents();

			int failed = 0;
			foreach (DiscourseEvent eventAsset in eventAssets)
			{
				// Export the event's strings to a CSV file with the same name.
				
				string path = Path.Combine(exportDirectory, FormatEventFileName(eventAsset));
				
				if (!TryExportEventStrings(eventAsset, path)) failed++;
			}
			
			Debug.Log($"<color=cyan>Exported {eventAssets.Length} event strings to {exportDirectory} - {failed} failures.</color>");
		}
		
		[MenuItem("Tools/Discourse/Batch Import Event Strings")]
		public static void BatchImport()
		{
			// Select a directory to import from
			if(!TryGetFileDialogDirectory("Select Import Directory", out string importDirectory)) return;

			DiscourseEvent[] eventAssets = GetProjectEvents();

			int failed = 0;
			foreach (DiscourseEvent eventAsset in eventAssets)
			{
				//Check if a CSV file exists in the import directory with this event's name, if so, attempt to import it.
				
				string filePath = Path.Combine(importDirectory, FormatEventFileName(eventAsset));
				if(!File.Exists(filePath)) continue;
				
				if (!TryImportEventStrings(eventAsset, filePath)) failed++;
			}
			
			Debug.Log($"<color=cyan>Imported {eventAssets.Length} event strings to {importDirectory} - {failed} failures.</color>");
			
			// Save the project to write the modifications to disk.
			AssetDatabase.SaveAssets();
		}
		
		private static bool TryImportEventStrings(DiscourseEvent discourseEvent, string csvFilePath)
		{
			if (discourseEvent == null) return false;

			// Import the CSV text and then set the asset dirty, to ensure changes are serialized.
			ReferenceIO.ReadLocalisedTextFromCsv(discourseEvent.StringLocaliser, csvFilePath);
			EditorUtility.SetDirty(discourseEvent);
			return true;
		}
		
		private static bool TryExportEventStrings(DiscourseEvent discourseEvent, string exportPath)
		{
			if (discourseEvent == null) return false;
			
			//Export the event's strings to the CSV file path.
			ReferenceIO.WriteLocalisedTextToCsv(discourseEvent.StringLocaliser, exportPath);
			return true;
		}

		private static DiscourseEvent[] GetProjectEvents()
		{
			// Find all DiscourseEvent asset guids. If you want to limit this to specific folders, FindAssets()
			// optionally takes an array of folder paths to limit the search to.
			
			string[] guids = AssetDatabase.FindAssets("t:DiscourseEvent");

			DiscourseEvent[] eventAssets = new DiscourseEvent[guids.Length];

			for (int i = 0; i < guids.Length; i++)
			{
				string path = AssetDatabase.GUIDToAssetPath(guids[i]);

				eventAssets[i] = AssetDatabase.LoadAssetAtPath<DiscourseEvent>(path);
			}

			return eventAssets;
		}
	}
}

```
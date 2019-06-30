---
layout: default
title: Localisation
nav_order: 1
has_children: false
permalink: /localisation
---


# Localisation

Discourse includes an intuitive, incremental and manageable localisation workflow out of the box. This system revolves around the LocalisedText class, which holds a unique ID to key a string across an arbitrary number of languages (each in turn keyed by their corresponding language code [e.g. 'en-us']).

To export an Event's strings for localisation, follow these steps:
1) Select the graph asset you want to localise in the project view
2) Right click the asset and select Discourse/Localisation/Export CSV
3) Choose a directory to export the .csv file to.
4) Once the export is complete, open the csv file in your spreadsheet editor of choice (e.g. Microsoft Excel).
5) By default, any language codes listed on your ReferencesDatabase will appear as columns in the file, with rows keyed by a unique ID, containing the localised string for that language. These will be empty unless you have changed between languages in the Editor and edited the text in the PropertyPanel.
6) Make any modifications to the text you see fit, or send it off for localisation.
7) Once the text has been localised, save the CSV, then navigate back to the project.
8) Select the Event asset you exported from, right click it and select Discourse/Localisation/Import CSV.
9) Navigate to where you saved the localised CSV, select it and confirm the file dialogue.
10) The import will shortly complete, and the next time you open the Event Graph you should find your strings have been localised! You can test this by changing the Source Language dropdown on the ReferencesDatabase asset.

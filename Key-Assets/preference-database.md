---
layout: default
title: Preference Database
parent: Key Assets
nav_order: 1
---

# PreferenceDatabase

The PreferenceDatabase stores various values that can be modified to suit a player's or developer's preference, both at runtime and in the editor. A good example of a runtime preference is the TextCharactersPerSecond (int) which the Typewriter ITextWriter uses to inform the speed of text display when the Typewriter mode is active on an ITextDisplay.

Some preferences are exposed in the inspector - such as TextCharactersPerSecond - but any arbitrary preference of the types Float, Int, String and Flag can be get / set through code using the explicit methods (e.g. Int(string key)) or via the generic GetPref<T>(string key) and SetPref<T>(string key) methods. Global variables can be of the types Float, Int, Flag and String. As with any variable collection, if you request a variable that does not exist in the collection, the default value for that type will be returned. Methods exist for each of the variable types to check if a preference is stored; these are named Has[TypeName] - e.g. HasInt(string key).

---
layout: default
title: Reference Database
parent: Key Assets
nav_order: 1
---

# ReferenceDatabase

The ReferenceDatabase serializes your game's languages, genders and  global variables, and allows you to retrieve information about your Actors. Whilst methods can be called directly on a ReferenceDatabase, the intended means of accessing an instance of a database is through the `References` class, which has several pass-through properties and methods to shorten common calls to a Database, as well as allowing you to swap to a different Database.

The References class points to an instance of a Database that has been registered by a ReferenceLocator - an object responsible for retrieving an instance of a database - which are sorted by Priority (int), allowing you to load databases by any means necessary for your project. The DefaultReferenceLocator loads the first ReferenceDatabase found in any Resources folder, and the RuntimeReferenceLocator loads a database from Resources before Duplicating it; ensuring any changes made in playmode are not carried back into the Editor.

Whilst you can change the loaded database via ReferenceLocators, it is recommended you only work with one database in the editor / project, reserving locator functionality to select between save files or different game-templates. However, should you require multiple databases, you will need to create a custom ReferenceLocator class with a higher priority than the default locators that appropriately loads the correct database according to your needs.  

Global variables can be of the types Float, Int, Flag and String. As with any variable collection, if you request a variable that does not exist in the collection, the default value for that type will be returned and you can optionally add the new Key-Value pair.

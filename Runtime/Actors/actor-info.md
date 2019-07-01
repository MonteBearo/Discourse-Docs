---
layout: default
title: ActorInfo
parent: Actors
nav_order: 1
---

# ActorInfo


```
Montebearo.Discourse.ActorInfo : ScriptableObject, IVariableProvider, IStringDropdownElement
```
---


## Public Static Fields

| Field | Type | Description |
|:------|:-----|:------------|
| NARRATOR | ActorInfo | Returns an ActorInfo that should be used to reference a "Narrator" character (for special styling in dialogue text). |

## Public Properties

| Property | Returns | Description |
|:---------|:--------|:------------|
| Id | string | A unique identifier used to reference this Actor in a name-agnostic way. |
| FullName | string | A formatted version of this character's full title; '[Title] [Forename] [Surname]'. If no Title is specified, it will be stripped to leave just '[Forname] [Surname]'. |
| Forename | string | Returns the character's forename, as specified in the inspector. |
| Surname | string | Returns the character's surname, as specified in the inspector. |
| Title | string | Returns the character's title, as specified in the inspector (e.g. 'Dr.'). |
| TitledSurname | string | Returns the character's title and surname in the format '[Title] [Surname]', or just surname if no title is specified. |
| NickName | string | Returns the character's nickname, as specified in the inspector. If none is specified, will return the Forename. |
| GenderId | string | The Id reference associated with this character's Gender. |
| Gender | Gender | The full Gender reference as specified in the inspector. |
| Actor | Actor | Retrieves an instance of an Actor component registered with this ActorInfo's Id at runtime. |

## Public Methods

| Method | Returns | Description |
|:-------|:--------|:------------|
||||
| **Variables** | | |
||||
| Flag(string flagName, bool addIfNotFound) | Flag | Retrieves a Flag variable in this ActorInfo's variable collection with the key 'flagName'. If 'addIfNotFound' is set to true and no variable was found with that key, a new Flag with this key will be added to the collection (this should usually be set to true). Returns the default value if not found. |
| Float(string floatName, bool addIfNotFound) | Float | Retrieves a Float variable in this ActorInfo's variable collection with the key 'floatName'. If 'addIfNotFound' is set to true and no variable was found with that key, a new Float with this key will be added to the collection (this should usually be set to true). Returns the default value if not found. |
| Int(string intName, bool addIfNotFound) | Int | Retrieves an Int variable in this ActorInfo's variable collection with the key 'intName'. If 'addIfNotFound' is set to true and no variable was found with that key, a new Int with this key will be added to the collection (this should usually be set to true). Returns the default value if not found. |
| String(string stringName, bool addIfNotFound) | String | Retrieves a String variable in this ActorInfo's variable collection with the key 'stringName'. If 'addIfNotFound' is set to true and no variable was found with that key, a new String with this key will be added to the collection (this should usually be set to true). Returns the default value if not found. |
||||
| **Portraits** | | |
||||
| SetPortrait(string portraitId, Sprite portrait) | void | Set the Sprite value of the Portrait listed on this ActorInfo with the Id 'portraitId'. |
| GetPortrait(string portraitId, bool defaultIfNotFound) | Sprite | Returns the stored portrait Sprite with the Id 'portraitId'. If 'defaultIfNotFound' is set to true, returns the first portrait sprite found on this ActorInfo, otherwise returns null. |
||||
| **Animation** | | |
||||
| AnimationName(string animationId) | string | Attempts to return the name of an animation clip stored in this ActorInfo's RuntimeAnimatorController with the Id 'animationId'. |
||||
| **Names / Reference** |||
||||
| SetForename(string forename) | void | Set's the character's forename value. |
| SetSurname(string surname) | void | Set's the character's surname value. |
| SetNickname(string nickname) | void | Set's the character's nickName value. |
| SetTitle(string title) | void | Set's the character's title value. |
| SetGender(string genderId) | void | Set's the character's gender (Id) value. |
| SetRuntimeReference(Actor actor) | void | Stores a reference to the character's runtime Actor component. |
||||
| **Debug** | | |
||||
| DebugId() | void | Logs this ActorInfo's FullName and Id to the console, for debugging purposes. |
| NewID() | void | Forces this ActorInfo's Id to regenerate. Note: calling this can be very dangerous, as it will break all existing references to this Actor, use with caution. |

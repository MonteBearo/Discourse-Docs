---
layout: default
title: IOptionsDisplay
parent: Display
grand_parent: Components
nav_order: 1
---

# IOptionsDisplay

```
public interface Montebearo.Discourse.IOptionsDisplay : IEventComponent
```

---

## EventHandlers

| EventHandler | Arguments | Description |
|:--|:--|:--|
| OptionSelected | Option | Subscribe for events when an Option currently being displayed has fired its own "Selected" event. Passes the selected Option as the argument. |

## Methods

| Method | Returns | Description |
|:--|:--|:--|
| DisplayOptionList(IOptionList list) | void | Display a list of Options to the screen to be selected by the player.  |

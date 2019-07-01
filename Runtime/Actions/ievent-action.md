---
layout: default
title: IEventAction
parent: Actions
nav_order: 1
---

# IEventAction

```
public interface Montebearo.Discourse.IEventAction
```
---


The base interface for all DiscourseActions. Actions should not explicitly implement this, but rather one of the two child interfaces: ISyncEventAction or IAsyncEventAction.

## Properties

| Property | Returns | Description |
|:--|:--|:---|
| Id | string | A unique Id used for referencing this action. |
| State | ActionState | The runtime state of the Action (Inactive, Running, Complete). |

## Methods

| Method | Returns | Description |
|:--|:--|:--|
| OnEnter(IEventContextLog contextLog) | void | Called as the StateMachine sets this Action to be the ActiveAction. Use for initialisation and subscribing to Events. |
| OnExit(IEventContextLog contextLog) | void | Called immediately before this Action is un-set as the StateMachine's ActiveAction.  Use for cleanup and un-subscribing from Events. |

---
layout: default
title: Multi-Link Nodes
parent: Custom Nodes
grand_parent: Editor
nav_order: 1
---

# Multi-Link Nodes

Sometimes you may want an Action to move between a selection of different Actions depending on some logic, in which case you probably need a Multi-Link node. The simplest way of doing this is to create a [Custom Node](custom-nodes.md) with a fixed set of Link points; similar to the Branch node that Discourse ships with. 

---

There are two key parts to a multi-link node; its NodeSettings and the Link_ConnectionChanged callback.

---

### NodeSettings: LinkPoints Array

When you override the `SettingsTemplate` property on a Node, you can pass in an array of floats to the `NodeSettings` struct called 'linkPoints'. The length of this array determines the number of links that are drawn, and each value corresponds to the visual position the Link will be drawn at.

By default, these values should be normalised for the height of the node (e.g. a value of 0.7f will be drawn at 70% of the node's height). You can set `linkPositionsRelative` to false when constructing your NodeSettings if you need to supply absolute pixel positions.

The Branch node implements its SettingsTemplate as follows, resulting in 2 link points at 30% and 70% of the Node's height:

```c#
protected override NodeSettings SettingsTemplate => new NodeSettings(new Vector2(96, 64), Colours.DCGreen, new[] {0.3f, 0.7f}, false);
```

---

### Link_ConnectionChanged Callback

A Node gets a callback whenever a connection changes on one of its Link points, and uses this to set the LinkedAction of its embedded Action. This callback has the following signature:

```c#
protected virtual void Link_ConnectionChanged(INodeConnectionPoint link, DiscourseAction action) 
```

This passes through the link that changed as an `INodeConnectionPoint`, and the [`DiscourseAction`](../Runtime/Actions/discourse-action.md) it is now connected to; it will be null if it was disconnected.

Typically, you will want to use this callback to store the Actions that were connected in some way that you can select between at runtime. This needs to be stored in the Action your Node represents, not the Node itself. It is also important that you use this callback to record an Undo step at the start of the method, so that state is managed correctly in the Editor.

An example of how this method might look in a custom Node, where its Action is of type `MyAction`:

```c#
protected override void Link_ConnectionChanged(INodeConnectionPoint link, DiscourseAction action)
{
    //Record an Undo step so Editor state is managed correctly
    Undo.RecordObject(this, "MyNode modified");

    //The index of the link that changed in this Node's list of Links
    int linkIndex = Links.IndexOf(link as NodeLink);

    //Set this connection on the embedded Action, 
    MyAction.SetAction(linkIndex, action);
}
```

And the implementation in `MyAction`:
```c#
[HideInInspector, SerializeField] private DiscourseAction[] _linkedActions = new DiscourseAction[4];

public void SetAction(int index, DiscourseAction action)
{
    _linkedActions[index] = action;
}
```

At runtime, you could then pass in one of these actions to MoveToAction() to branch your graph, depending on some logic. 

---
layout: default
title: Search Widget
parent: Editor
nav_order: 1
---

# Search Widget
---

The Search Widget is a small helper element that allows you to search for and add any nodes in the project (including [Custom Nodes](custom-nodes.md)). To open the Search Widget, simply press the spacebar whilst your mouse is hovering the Discourse work view.

To navigate the Search Widget, use the arrow keys; up/down to select between folders, right/left to enter or back out of those folders, and Return/Enter to add the final selected Node.

---

### Customising the location of Custom Nodes in the Search Widget

If you've added a [Custom Node](custom-nodes.md) to your project, it's really easy to customise where that Node appears in the list. To do so, simply override the `Path` property on your Node.

```c#
protected override string Path => $"Discourse/Dialogue/{ActionName}";
```

Here, forward slashes indicate folder breaks, so you can organise any custom nodes into subcategorise as you please. Whatever is written after the final slash will be used as the name for the node in the list, but you can use the `ActionName` property for convenience, which will correctly format the name and keep the Path updated if you ever rename the class.

---
> Here, we've used string interpolation (available in C# 6) to conveniently format our path, as indicated by the '$' symbol. For more information on string interpolation, please refer to the [.NET documentation.](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/tokens/interpolated)

---

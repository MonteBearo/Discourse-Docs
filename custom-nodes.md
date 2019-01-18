# Custom Nodes
---

Discourse comes packed with just about everything you'd need to get a dialogue or cutscene event up and running, but it can't handle _everything_ - you might want to hook into the specifics of your game. That's where custom nodes come in.


### Creating a custom node:

1. Create a [Custom Action](custom-action).
1. Create a new class inside an **Editor** folder (typically, Node class names are prefaced with 'Node').
1. Inherit the class from [`Node`](node.md).
1. Make sure you include `using Montebearo.Discourse.Editor;` at the top of the file.
1. Override the ActionType property to point to your Action:
`protected override Type ActionType => typeof(YourCustomAction);`.
1. That's it! Just open the [Search Widget](search-widget.md) and it'll appear under  **Custom/YourCustomAction**.

###### Example:

```
using System;
using Montebearo.Discourse.Editor;

public class NodeCustomAction : Node
{
    protected override Type ActionType => typeof(CustomAction).
}
```


### Changing the appearance of your Node

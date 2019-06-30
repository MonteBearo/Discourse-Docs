# Custom Nodes
---

Discourse comes packed with just about everything you'd need to get a dialogue or cutscene event up and running, but it can't handle _everything_ - you might want to hook into the specifics of your game. That's where custom nodes come in.

---

### Creating a custom node:


1. Create a [Custom Action](discourse-action.md).
2. Create a new class inside an **Editor** folder (typically, Node class names are prefaced with 'Node').
3. Inherit the class from [`Node`](node.md).
4. Make sure you include `using Montebearo.Discourse.Editor;` at the top of the file.
5. Override the **ActionType** property to point to `typeof(YourCustomAction)`
6. That's it! Just open the [Search Widget](search-widget.md) and it'll appear under  **Custom/YourCustomAction**.

---

### Example:

```c#
using System;
using Montebearo.Discourse.Editor;

public class NodeCustomAction : Node
{
    protected override Type ActionType => typeof(CustomAction).
}
```
---

> **Note:** Typically, you will want to add a pass-through property for your Action that casts it to the appropriate type. This is useful if you want to pass a property of your Action into the Subtitle of your node, for instance. To do this, you will need to cast the 'EmbeddedAction' field.
For example: `private CustomAction MyCustomAction => EmbeddedAction as CustomAction;`

---

### Changing the appearance of your Node

To change the appearance of your node, such as its dimensions, tab colour or whether its title should appear on its body, you must override the `SettingsTemplate` property to point to a new [`NodeSettings`](node-settings.md) struct. Don't worry about caching this, that's taken care of behind the scenes.

In this example, we'll just override the colour:

```c#
using System;
using Montebearo.Discourse.Editor;

public class NodeCustomAction : Node
{
    protected override Type ActionType => typeof(CustomAction).
    protected override NodeSettings SettingsTemplate => new NodeSettings(new Colour(0.35f, 0.65f, 0.75f));
}
```
---
> For more information on customising the appearance of a node, please refer to the [NodeSettings](node-settings.md) page.

---

### Changing the Title and Subtitle of the Node

 The Title of a node is the text that will appear in bold at the top of the Node's body, whereas the Subtitle is a smaller line at the bottom of the body, used to summarise the state of that Action. Both the Title and Subtitle can be overridden. For example, in the [Speech](speech.md) node the Title is used to indicate the Speaker of that line, and the Subtitle shows a preview of its text.

 Here we override Title and Subtitle:

 ```c#
 using System;
 using Montebearo.Discourse.Editor;

 public class NodeCustomAction : Node
 {
     protected override Type ActionType => typeof(CustomAction).
     protected override NodeSettings SettingsTemplate => new NodeSettings(new Colour(0.35f, 0.65f, 0.75f));

     protected override string Title => "New Title!";
     protected override string Subtitle => "Some Subtitle..."
 }
 ```

 ---

---
export_on_save:
  html: true
---  



# Custom Nodes

Custom nodes allow you to extend Discourse to meet the specific needs of your game, often in ways that would be too bespoke to do generally. Creating a custom node requires two short steps:

- [Create a custom DiscourseAction](discourseAction.md)
- Create a new class, structured as follows:

```
using Montebearo.DiscourseWiki

public class CustomNode : Node
{
    //Replace CustomAction with your own CustomAction type.
    protected override ActionType => typeof(CustomAction);
}
```


Where CustomAction is your own [DiscourseAction](discourseAction.md).

# DiscourseAction

```
Montebearo.Discourse.DiscourseAction : ScriptableObject
```
---

Actions are containers for logic that are housed within Nodes and run in sequence at runtime, according to the order of nodes laid out in a [Graph](graph.md). All Nodes must have an Action they are responsible for managing.

The stock Actions include:

- Entry (begin running the graph)
- Exit (stop the graph, exit to a scene)
- Speech (have an Actor speak a line, with subtitled text and audio)
- OptionSet (display a set of choices to the player, which can each link to other actions)
- SetValue (set a Global or Actor-specific variable at runtime; Flag, Int, Float or String)
- Branch (split the flow of Actions depending on the result of a set of conditions)
- ActorAnimation (play an animation on an Actor, or set a value on an AnimatorController)

...and many more!


A huge part of Discourse's power in comparison to other dialogue & cutscene tools however, is its extensibility, allowing you to weave in your own gameplay logic between dialogue nodes.


### Creating a custom action:

1. Create a new class (C# script, removing the MonoBehaviour inheritance)
2. Inherit the class from `DiscourseAction`.
3. Make sure you include `using Montebearo.Discourse;` at the top of the file.
4. If the Action should run immediately, with no yielded instructions, it should also inherit ISyncEventAction. If it must yield (like a Coroutine), it should inherit IAsyncEventAction. Depending on which of these you choose, it will need to implement a public method with the signature 'Run(EventContextLog contextLog)', with a return type of void or IEnumerator depending on it being Sync or Async, respectively. Using the IEnumerator keyword will require you include a 'using System.Collections;' statement at the top of the file. For more information on the context log, please see: [EventContextLog](event-context-log.md).
6. That's it! Now, to be able to add your Action to a graph in the editor, you'll need to create a [Custom Node](custom-nodes.md). Actions don't need Node counterparts in order to be run, just to be configured in the editor.

---

> **Note:** In most cases, you will want your action to link to the next one in the graph. In order to do this, you must call 'MoveToAction(LinkedAction)' somewhere in the Action's Run() method.

---


---

### Example:

Here's an example Action that gets an Int variable named "Cash" on an Actor (referenced in the inspector) and logs it to the console for debugging.

```c#
using Montebearo.Discourse;
using UnityEngine;

public class DebugActorCash : DiscourseAction, ISyncEventAction
{
    //-----------------------------------------------------------------------------------------
    // Inspector Variables
    //-----------------------------------------------------------------------------------------

    [ActorNamesDropdown("Actor", false)] [SerializeField] private ActorReference _actor = null;

    //-----------------------------------------------------------------------------------------
    // Interface Methods
    //-----------------------------------------------------------------------------------------

    void ISyncEventAction.Run(EventContextLog contextLog)
    {
        int cash = References.ActorInfo(_actor).Int("Cash", true).Value;

        Debug.Log($"{_actor.Info.FullName} has {cash} cash.");

        MoveToAction(LinkedAction);
    }
}

```

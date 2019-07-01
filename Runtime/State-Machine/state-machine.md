---
layout: default
title: State Machine
nav_order: 1
has_children: true
permalink: /state-machine
---

# State Machine

```
Montebearo.Discourse.EventContextLog : class
```
---

The State Machine is responsible for running all DiscourseActions in the sequence laid out in the Graph.

## Public Properties

| Property | Returns | Description |
|:---------|:--------|:------------|
| ActiveAction | IEventAction | The Action currently executing. Setting this property Calls OnExit on the existing ActiveAction, stops its coroutine if it's an IAsyncEventAction, sets the ActiveAction to the given Action, then calls OnEnter(), switches the active Camera if the Action is an ICameraSwitchInstruction, then calls the action's Run() method. |

## Public Methods

| Method | Returns | Description |
|:-------|:--------|:------------|
| ClearStack(bool update) | void | Clear the entire stack. Update dictates whether to update the ActiveAction (in this case, just calling OnExit() on the currently ActiveAction). |
| PopStack(bool update) | void | Pop the top Action in the stack. Update dictates whether the next Action in the stack should be made the ActiveAction. Leave Update at false if you wish to pop several Actions in a row before setting a new ActiveAction. Use ExitCurrent if you wish to immediately execute the underlying Action. |
| ExitCurrent() | void | Exit the current action and run the enxt action below it in the Stack. (Shorthand, more readable version of PopStack(true)). |
| PushAction(IEventAction action, bool update) | void | Push an Action to the stack. Update dictates whether the action is run. This should usually be set to true, however if you are pushing multiple Actions as a set, you may want to delay their execution. |
| UpdateActiveAction() | void | Force update the ActiveAction to the action now at the top of the stack. This calls OnExit() on the currently active action, replaces it with the stack's top item, then calls OnEnter(), changes the Camera if the Event is an ICameraSwitchInstruction, and finally the Event's Run() method. |

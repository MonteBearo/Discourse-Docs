---
layout: default
title: Event Context Log
parent: State Machine
grand_parent: Components
nav_order: 1
---


# EventContextLog

```
Montebearo.Discourse.EventContextLog : class, IEventContextLog
```
---

The EventContextLog is an object passed between Actions that should be used to access commonly referenced Behaviours and data (e.g. the EventBehaviour, AudioHandlers etc). You should use this object to reference such behaviours at runtime, during an Action's Run() method (implemented as part of either ISyncEventAction or IAsyncEventAction).

The default EventContextLog implements the necessary members of IEventContextLog. Should you wish to append more information to this packet, it is recommended you create your own IEventContextLog.

---

# IEventContextLog

```
public interface Montebearo.Discourse.EventContextLog
```
---

# Properties

| Property    | Returns     | Description       |
|:------------|:------------|:------------------|
| EventBehaviour | DiscourseEventBehaviour | The EventBehaviour responsible for handling the event. |
| StateMachine   | StateMachine            | The StateMachine all IEventActions are run through. Use this to move between actions.  |
| TextDisplay | ITextDisplay | The behaviour responsible for display text to the screen (subtitled text). |
| ActorInfoDisplay | IActorInfoDisplay |  The behaviour responsible for displaying the Actor's name and portrait to the screen when they are engaged in dialogue. |
| OptionsDisplay | IOptionsDisplay | The behaviour responsible for displaying a list of Options to the screen. |
| AudioHandler | IAudioHandler | The behaviour responsible for playing Audio explicitly on the Event object (generic AudioActions).  |

# Methods

| Method | Returns | Description |
|:-------|:--------|:------------|
| GetSceneObject(string id) | Transform | Get a referenced Scene Object on the EventBehaviour, by reference id. |
| SwitchCamera(ICameraSwitchInstruction switchInstruction) | void | Switch the active Camera via the EventBehaviour's ICameraTransitionHandler. |

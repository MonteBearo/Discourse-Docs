# DiscourseEventBehaviour


The EventBehaviour holds a reference to an Event that can be played at runtime.

## EventHandlers

| Event              | Description |
|:------------------|:------------|
| OnEventStart      | Subscribe to get notifications immediately before the Event pushes its Entry action. |
| OnEventExit       | Subscribe to get notifications when the Event is about to exit (Called by Exit actions immediately before they would switch scenes).|
| Advance           | Subscribe to get notifications when an `IEventAdvancer` has indicated the Event should "move forward" (e.g. to skip blocks of text). |

## Public Properties

| Property          | Returns | Description |
|:------------------|:--|:------------|
| StateMachine      | StateMachine  | The StatMachine used to run the Event's Actions |
| TextDisplay       | ITextDisplay  | The display responsible for showing dialogue text to the screen.|
| ActorInfoDisplay  | IActorInfoDisplay | The display responsible for showing an Actor's name and portrait to the screen |
| OptionsDisplay    | IOptionsDisplay | The display responsible for showing a list of Options to the screen, and allowing the player to select between them. |
| CameraTransitionHandler | ICameraTransitionHandler | The component responsible for referencing and switching between Unity Cameras throughout the lifetime of the Event. |
| SceneObjectHandler      | ISceneObjectHandler   | The component responsible for referencing and providing access to various Scene Objects (Transforms) in the scene. |
| AudioHandler            | IAudioHandler         | The component responsible for playing any audio that should eminate from the EventBehaviour itself. |


## Protected Virtual Properties

| Property          | Returns | Description |
|:------------------|:--|:------------|
| ContextLogTemplate      | IEventContextLog  | Should return a new instance of an IEventContextLog to create the StateMachine's context log from (override if you need to extend the references accessible in the stock context log by providing your own type). |


## Public Methods

| Method          | Returns | Description |
|:------------------|:--|:------------|
| StartEvent()      | void  | Invokes the OnEventStart EventHandler and the runs the Event's Entry action.  |
| ForceQuitEvent() | void | Immediately exit the current action and move to a new instance of an Exit action |
| InvokeOnEventExit() | void | Invoke the EventBehaviour's OnEventExit EventHandler. (Called by the Exit action; if you wish to force exit the Event, call ForceQuitEvent() instead). |
| ForceInvokeAdvance() | void | Invoke the EventBehaviour's Advance EventHandler (used by IEventAdvancers) |
| ListenForAdvances() | void | Start listening for 'Advance' EventHandler invocations from any registered IEventAdvancers. |
| StopListeningForAdvances() | void | Stop listening for 'Advance' EventHandler invocations from any registered IEventAdvancers.
		/// (Useful if you wish to temporarily 'pause' an input that would otherwise trigger the 'Advance' invocation on an IEventAdvancer). |

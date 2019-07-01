---
layout: default
title: Actor Info Display
parent: Display
grand_parent: Components
nav_order: 1
---

# Actor Info display

New release [v1.1.0]
{: .label .label-purple }

```
Montebearo.Discourse.ActorInfoDisplay : MonteBehaviour, IActorInfoDisplay
```

---

The ActorInfoDisplay component is used for displaying an Actor's Name and Portrait at runtime, above relevant dialogue text, such as via the Speech action.


## Protected Virtual Properties

| Property | Returns | Description |
|:---------|:--------|:------------|
| VisibilityHandler | IVisibilityTransitionHandler | The IVisibilityTransitionHandler responsible for transitioning the display's visibility. |

---

# IActorInfoDisplay

```
public interface Montebearo.Discourse.IActorInfoDisplay
```
---

## Methods

| Method | Returns | Description |
|:-------|:--------|:------------|
| DisplayActorInfo(ActorInfo actorInfo, Sprite portrait, bool changePortrait) | void | Display the given actor information. If 'changePortrait' is set to true, switch to the supplied 'portrait', otherwise, leave it set to its current value. |
| Hide(bool immediate) | void | Hide the display from the screen. Immediate indicates whether an IVisibilityTransitionHandler should set the 'Instant' flag. |

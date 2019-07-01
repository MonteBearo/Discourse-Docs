---
layout: default
title: IVisibilityTransitionHandler
parent: Visibility
grand_parent: Components
nav_order: 1
---

# IVisibilityTransitionHandler


```
public interface Montebearo.Discourse.IVisibilityTransitionHandler
```

---

## EventHandlers

| EventHandler | Description |
|:-------------|:------------|
| VisibilityChanged | Subscribe to this to get notifications when the visibility of this element changes in any way. |
| BecameVisible | Subscribe to this to get notifications when this element has become visible |
| BecameHidden | Subscribe to this to get notifications when this element has become hidden. |

## Properties

| Property | Returns | Description |
|:---------|:--------|:------------|
| Visible | bool | Returns true if this element is (100%) visible. |
| IsTransitioning | bool | Returns true if this element is transitioning between visibilities. |


## Methods

| Method | Returns | Description |
|:-------|:--------|:------------|
| Transition(VisibilityTransition transition, Action onComplete) | void | Transition this element's visibility. Transition:  The transition to perform. The 'Instant' flag indicates whether the behaviour should transition the visibility immediately, i.e not over time. OnComplete: Pass an Action to be invoked when the transition has completed. |

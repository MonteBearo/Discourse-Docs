---
layout: default
title: VisibilityBehaviour
parent: Visibility
grand_parent: Components
nav_order: 1
---

# VisibilityBehaviour


```
Montebearo.Discourse.VisibilityBehaviour : IVisibilityTransitionHandler
```

---

The VisibilityBehaviour is an abstract base class for behaviours implementing the IVisibilityTransitionHandler interface, in turn making them serializable. It implements all members within the interface, and allows invocation of the various EventHandlers through protected methods.

## Protected methods

| Method | Returns | Description |
|:-------|:--------|:------------|
| InvokeVisibilityChanged() | void | Invokes the VisibilityChanged EventHandler. |
| InvokeBecameVisible() | void | Invokes the BecameVisible EventHandler. |
| InvokeBecameHidden() | void | Invokes the BecameHidden EventHandler. |

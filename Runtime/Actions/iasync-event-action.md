---
layout: default
title: IAsyncEventAction
parent: Actions
nav_order: 1
---

# IAsyncEventAction

```
public interface Montebearo.Discourse.IAsyncEventAction : IEventAction
```
---

## Methods

| Method | Returns | Description |
|:--|:--|:--|
| Run(IEventContextLog contextLog) | IEnumerator | Run an action's logic over time in a coroutine. |

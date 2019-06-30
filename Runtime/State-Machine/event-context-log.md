# EventContextLog

```
Montebearo.Discourse.EventContextLog : class
```
---

The EventContextLog is an object passed between Actions that should be used to access commonly referenced Behaviours and data (e.g. the EventBehaviour, AudioHandlers etc). You should use this object to reference such behaviours at runtime, during an Action's Run() method (implemented as part of either ISyncEventAction or IAsyncEventAction).

---
layout: default
title: Custom Scene Reference Handlers
parent: Scene Reference Handlers
grand_parent: Components
has_children: false
nav_order: 1
---


# Writing a Custom SceneReferenceHandler

You may want to access instances of your own components from your Actions at runtime. One way of doing this is with a custom [SceneReferenceHandler](scene-reference-handlers.md). You can only reference types that inherit Unity.Object, [so they can be serialized](https://docs.unity3d.com/Manual/script-Serialization.html). 

Custom SceneReferenceHandlers require three pieces of data:
1. A type to reference; such as your own MonoBehaviour component
2. A SceneReferenceLookup for this type
3. The actual SceneReferenceHandler, which you will add to the EventBehaviour

--- 

### 1. The Type to Reference
 
For this example, we will use a custom component 'MyCustomComponent':
```c#
public class MyComponent : MonoBehaviour { }
```

---

### 2. SceneReferenceLookup

SceneReferenceLookup is a generic class that allows you to wrap a Serializable Dictionary for a given Type, such that it can be stored for use in the SceneReferenceHandler. This is done simply by implementing a class that inherits SceneReferenceLookup, with your component as the generic type. **Note: You must add the System.Serializable Attribute to this class**.

```c#
[Serializable] 
public class MyComponentLookup : SceneReferenceLookup<MyComponent> { }
```

---

### 3. SceneReferenceHandler

With the above two constituents, you can now implement your own SceneReferenceHandler. As this is a MonoBehaviour, it must exist in a file with the same name as the class, or Unity will not serialize it. 

```c#
public class MyComponentReferenceHandler : SceneReferenceHandler<MyComponentLookup, MyComponent> { }

```

---

You can then add `MyComponentReferenceHandler` to your EventBehaviour, and you will be able to assign instances of `MyComponent` to it in the inspector.

---
layout: default
title: OptionsDisplay
parent: Display
grand_parent: Components
nav_order: 1
---

# OptionsDisplay

```
Montebearo.Discourse.OptionsDisplay : MonteBehaviour, IOptionsDisplay
```

---

## Protected Virtual methods

| Method | Returns | Description |
|:---|:---|:----|
| AwaitKeyboardInput(IOptionList options) | IEnumerator | Coroutine that awaits numeric keyboard input for selecting Options by index (i.e if the player pressed the "2" key, Option 2 will be Selected. |
| GetButton(int index) | IOptionButton | Get an IOptionButton behaviour for a given index. If the index is higher than the count of the list, spawn a new one. |

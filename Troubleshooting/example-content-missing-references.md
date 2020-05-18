---
layout: default
title: Example Content - Missing References
parent: Troubleshooting
nav_order: 1
---

# Example Content: Missing References
---

> Discourse 1.3
---

### Symptoms

Sometimes Unity fails to resolve prefab references to scripts imported from the Prebuild Discourse DLL, which can lead to several missing reference errors and warnings as you attempt to view the Example Content scene.

---

### Fix

Fortunately, this is straightforward to fix:

1. Navigate to Montebearo.Discourse/Montebearo.Discourse.dll
2. Select the dll, right click it and select "Reimport".
3. Navigate to Montebearo.Discourse/Example Content. Select just the Example Content folder, right click it and select "Reimport".

This should resolve all missing reference errors in the Example scene.
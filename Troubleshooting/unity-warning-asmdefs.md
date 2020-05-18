---
layout: default
title: Asmdef DLL Warnings
parent: Troubleshooting
nav_order: 1
---

# Example Content: Asmdef DLL Warnings
---

> Discourse 1.3

---

### Symptoms

In some Unity releases, users have reported warnings of conflicting asmdef / dll files in the third party libraries supplied with Discourse.

---

### Fix

Fortunately, this is straightforward to fix. Delete the .asmdef files at the following paths:

- 'Montebearo.Discourse/Libraries/Jace'
- 'Montebearo.Discourse/Libraries/CsvHelper'

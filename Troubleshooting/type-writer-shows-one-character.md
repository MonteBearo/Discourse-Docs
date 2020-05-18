---
layout: default
title: Typewriter shows only one character
parent: Troubleshooting
nav_order: 1
---

# Typewriter mode displays only one character
---

> Version agnostic

---

### Symptoms

When using the _Typewriter_ mode on the _TextDisplay_ component, only one character of text is revealed, rather than the entire string.

---

### Fix

The TextMeshPro reference you have assigned to your TextDisplay likely doesn't have its **Overflow** mode set to **Page**, which is a requirement for the Typewriter mode.

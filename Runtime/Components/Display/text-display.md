---
layout: default
title: Text Display
parent: Display
grand_parent: Components
nav_order: 1
---

# Text display

New release [v1.1.0]
{: .label .label-purple }

```
Montebearo.Discourse.TextDisplay : MonteBehaviour, ITextDisplay
```
---

The TextDisplay component is responsible for displaying dialogue text to the screen. It uses an ITextWriter to display this text on the TextMeshPro Text component, of which the active writer is stored in the ActiveWriter property. You can override this in a child class if you wish to supply your own writer.  

Text can be displayed in a number of modes that can be modified with flags:

| Flag | Description |
|:-----|:------------|
| Immediate | Displays text immediately to the screen with no form of transition. |
| ChangeOnDip | Indicates whether the TextVisibilityBehaviour should transition between Hidden and Visible as lines are displayed to the screen. |
| Typewriter | Reveals the given text character-by-character, at a rate specified on the PreferencesDatabase as TextCharactersPerSecond. Can be accelerated by calling ActiveWriter.Accelerate(float speed) on the TextDisplay component [Note: this should be returned to 1 when acceleration input has stopped].
| DippedTypewriter | Combines Typewriter with ChangeOnDip, softly fading between lines as they begin to be written. |

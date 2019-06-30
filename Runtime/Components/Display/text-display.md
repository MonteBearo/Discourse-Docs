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

> **Note:** Developers wishing to implement a custom TextDisplay should consult the interface ITextDisplay; as described below.

---

The TextDisplay component is responsible for displaying dialogue text to the screen. The TextMeshPro reference used for the text should be set to the Page overflow mode for Discourse to appropriately display text that is too long for the on-screen display. Text can also be deliberately split into pages within a single Speech node by using the '<page>' tag at the start of a new page. The TextDisplay uses an ITextWriter to display this text on the TextMeshPro Text component, of which the active writer is stored in the ActiveWriter property. You can override this in a child class if you wish to supply your own writer.  

Text can be displayed in a number of modes that can be modified with flags:

| Flag | Description |
|:-----|:------------|
| Immediate | Displays text immediately to the screen with no form of transition. |
| ChangeOnDip | Indicates whether the TextVisibilityBehaviour should transition between Hidden and Visible as lines are displayed to the screen. |
| Typewriter | Reveals the given text character-by-character, at a rate specified on the PreferencesDatabase as TextCharactersPerSecond. Can be accelerated by calling ActiveWriter.Accelerate(float speed) on the TextDisplay component [Note: this should be returned to 1 when acceleration input has stopped].
| DippedTypewriter | Combines Typewriter with ChangeOnDip, softly fading between lines as they begin to be written. |

---

## Protected Virtual Properties

| Property | Returns | Description |
|:---------|:--------|:------------|
| Typewriter | ITextWriter | The ITextWriter that should be used when Transition has the Typewriter flag set. |
| ImmediateWriter | ITextWriter | The ITextWriter that should be used when Transition does not have the Typewriter flag set. |
| PanelVisibilityHandler | IVisibilityTransitionHandler | The IVisibilityTransitionHandler responsible for transitioning the visibility of the text area's background area (with the text contained as a child). |
| TextVisibilityHandler | IVisibilityTransitionHandler | The IVisibilityTransitionHandler responsible for transitioning the visibility of the dialogue text itself - used if Transition has the ChangeOnDip flag set. |

## Protected Virtual Methods

| Method | Returns | Description |
|:-------|:--------|:------------|
| WritePages(string allText, FontStyle globalStyle) | IEnumerator | Invoked via StartCoroutine() in the ITextDisplay's DisplayText() method, passing across the necessary arguments. Override should you need to run your own text displaying logic in an explicit order. Should set FinishedDisplayingText to true on finish.

---

# ITextDisplay

ITextDisplay is the interface an EventBehaviour uses to display text to the screen, the display it uses can be overriden should you wish to create your own.

## Properties

| Property | Returns | Description |
|:---------|:--------|:------------|
| FinishedDisplayingText | bool | Should return false for as long as the display has not finished displaying (paginated) text. |

## Methods

| Method | Returns | Description |
|:-------|:--------|:------------|
| DisplayPanel(bool immediate) | void | Display the background panel for the text area. Immediate indicates whether the necessary IVisibilityTransitionHandler should transition with the 'Instant' flag set. |
| DisplayText(string text, IVariableProvider parsedVariableProvider, FontStyle globalStyle) | void | Display a string of text on top of the display panel. The parsedVariableProvider should be the object responsible for parsing any self-referenced variables in the text (for example, an ActorInfo) and globalStyle indicates any tags that should be wrapped around the entirety of the string (Normal, Italic, Bold, or BoldItalic). |
| AdvancePage() | void | Invoke to either complete the page being written, or to continue to the next page in any paginated text |
| HidePanel(bool immediate) | void | Hide the text area. Immediate indicates whether the necessary IVisibilityTransitionHandler should transition with the 'Instant' flag set.  |

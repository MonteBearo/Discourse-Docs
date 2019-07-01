---
layout: default
title: Text Parsing
nav_order: 1
has_children: true
permalink: /text-parsing
---

# Text Parsing

To parse text for variables, case-matched text, math, global variables, and Int/Float expressions, use the TextUtility class.

---

# Text Utility

```
Montebearo.Discourse.TextUtility : class [static]
```
---


Static class used for parsing various parts of text.


## Methods

| Methods | Returns | Description |
|:--|:--|:--|
| ParseString(string text, IVariableProvider selfProvider, bool parseMath) | string | Parse all aspects of an incoming string. Parsing occurs in the following order: GlobalVariables, Variables, Math expressions (if 'parseMath' is set to true) and finally replacement of case-matched text. The IVariableProvider 'selfProvider' sets the provider to use when the first self-referencing variable syntax is found ('$.' format). |
| ParseAsInt(string text, bool evaluateExpression) | int | Attempts to parse a string as an int. If 'evaluateExpression' is set to true, it will attempt to resolve a calculation within the text. First parses the string using ParseString(), then optionally evaluates expressions, before using int.TryParse() to retrieve the final result. |
| ParseAsFloat(string text, bool evaluateExpression) | float | Same as ParseAsInt(), but with the float data type.|
| StyleText(string sourceText, FontStyle style) | string | Wraps sourceText in the rich-text tags appropriate for the given FontStyle (Bold: \<b>, Italic: \<i> and BoldItalic: \<b>\<i>). |

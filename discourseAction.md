---
export_on_save:
  html: true
---  



# Discourse Action

Actions are simple bundles of instructions that are run during [Events](event.md). Actions are represented in [Graphs](graph.md) by a corresponding Node, which acts as an inspector for its fields.

Creating a custom action takes only three steps:

- Create a new class
- Add "using Montebearo.Discourse;" to the top of the file
- Inherit the class from 'DiscourseAction'

`using Montebearo.Discourse`
`public class CustomAction : DiscourseAction { }`


//Changes

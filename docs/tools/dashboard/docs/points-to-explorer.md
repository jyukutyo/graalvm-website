# Points-to Exploration

The Points-to Explorer component allows exploring the points-to analysis process
of a native image to find out why a certain method was included, to see how the
sequence of calls to that method (or the sequence of data flows) can be
interrupted, to avoid this method possible inclusion in the future. For example,
if a method is included into a native image, then Points-to Explorer allows a
user to ask questions like "Where was this method called", "Why is exactly this
implementation of the method called" for virtual calls. The search expands the
graph recursively until reaching the entry-point into the application.

<!-- <img src="/docs/tools/dashboard/resources/img/points-to-exploration.png" alt="points-to-explorer" width="850" height=500/> -->
![points-to-explorer](/docs/tools/dashboard/resources/img/points-to-exploration.png)

## PointTo-SourceLine ([VS Code extension](https://marketplace.visualstudio.com/items?itemName=oracle-labs-graalvm.dashboard))

Allows the user to quickly navigate to source line from Points-to Exploration. Every node with source line information prompts to open (.gds) file when already explored. When opened in VS Code with installed PointTo-SourceLine extension, this tries to navigate to a respectful source line in the opened workspace.

<!-- <img src="/docs/tools/dashboard/resources/img/pointto-sourceline.png" alt="pointto-sourceline" width="850" /> -->
![pointto-sourceline](/docs/tools/dashboard/resources/img/pointto-sourceline.png)

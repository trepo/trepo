# nPipes
Based in part off of Tinkerpop's [Pipes](https://github.com/tinkerpop/pipes/wiki), nPipes is a [vGraph](https://github.com/genealogysystems/vgraph) specific graph query and traversal framework. It supports transparent cross-repository traversals, the execution of traversals in parallel, and multiple execution strategies.

You can read a conceptual introduction [here](intro.md).

# Version
0.3.0

# Specification

### [Traversal](definition/traversal.md)
A path through the graph determined by a set of instruction along with any information collected along that path.

When a traversal is [executed](execution/traversal.md), each [Step](definition/steps.md) is executed in sequence until the traveral is complete (stopped, paused, redirected, errored, etc).

### [Steps](definition/steps.md)
An action to take during a traversal.

When a step is executed, it modifies the traversal in some way. See each step for the specific actions it takes.

* [get](step/get.md) - Traverse directly to an Element.
* [node](step/node.md) - Traverse from a node to an adjoining Node.
* [toedge](step/toedge.md) - Traverse from a node to an adjoining Edge.
* [fromedge](step/fromedge.md) - Traverse from an edge to a connected Node.
* [mark](step/mark.md) - Mark the current element to allow for backtracking.
* [back](step/back.md) - Backtrack to the element that was previously marked.
* [exists](step/exists.md) - From a node, if an edge exists, goto step X, else go to step Y.
* [if](step/if.md) - If expression is true, goto step X, else goto step Y.
* [goto](step/goto.md) - Go to step X.
* [pause](step/pause.md) - Set the status to Paused.
* [stop](step/stop.md) - Set the status to Stopped.
* [save](step/save.md) - Save element properties to the traversal payload.
* [set](step/set.md) - Set values in the traversal payload.
* [inc](step/inc.md) - Increment a value in the traversal payload.

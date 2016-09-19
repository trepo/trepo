# getNodes(Direction, [Labels])
Get Nodes connected to this Node in the specified Direction, optionally filtered by Edges having one of the specified Labels.

## Parameters

* [Direction](../definition/direction.md) - The Direction.
* [Labels](../definition/element-label.md) - An optional Array of Labels.

## Actions

1. If [Status](../definition/element-status.md) is greater than or equal to `4` (Deleted), [Error](../definition/error.md).
1. If [Direction](../definition/direction.md) is invalid, [Error](../definition/error.md).
1. For all of the [Edges](../definition/edge.md) in the [Direction](../definition/direction.md):
    1. If [Edge's](../definition/edge.md) [Status](../definition/element-status.md) is greater than or equal to `4` (Deleted), continue.
    1. If [Labels](../definition/element-label.md) is set and not empty and [Edge's](../definition/edge.md) [Label](../definition/element-label.md) is NOT in [Labels](../definition/element-label.md), continue.
    1. For the [Node](../definition/node.md) connected to [Edge](../definition/edge.md) that is not this [Node](../definition/node.md):
        1. If [Node's](../definition/node.md) [Status](../definition/element-status.md) is less than `4` (NOT Deleted), return it.


## Returns

An Array or Iterable  of [Nodes](../definition/node.md).
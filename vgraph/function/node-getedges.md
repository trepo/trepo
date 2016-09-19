# getEdges(Direction, [Labels])
Get Edges connected to this Node in the specified Direction, optionally filtered by Edges having one of the specified Labels.

## Parameters

* [Direction](../definition/direction.md) - The Direction.
* [Labels](../definition/element-label.md) - An optional Array of Labels.

## Actions

1. If [Status](../definition/element-status.md) is greater than or equal to `4` (Deleted), [Error](../definition/error.md).
1. If [Direction](../definition/direction.md) is invalid, [Error](../definition/error.md).
1. Get all of the [Edges](../definition/edge.md) in the [Direction](../definition/direction.md) and return them if:
    1. [Edge's](../definition/edge.md) [Status](../definition/element-status.md) is less than `4` (Not Deleted) and:
        1. If [Labels](../definition/element-label.md) is NOT set/is empty or
        1. [Labels](../definition/element-label.md) is set and [Edge's](../definition/edge.md) [Label](../definition/element-label.md) is in [Labels](../definition/element-label.md).


## Returns

An Array or Iterable  of [Edges](../definition/edge.md).
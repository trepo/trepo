# addEdge(Label, From, To)
Add an Edge.

## Parameters

* [Label](../definition/element-label.md) - The Label.
* [From](../definition/node.md) - The From Node.
* [To](../definition/node.md) - The To Node.

## Actions

1. If [Label](../definition/element-label.md) is invalid, [Error](../definition/error.md).
1. If [From](../definition/element-label.md) is invalid or [Status](../definition/element-status.md) is greater than or equal to `4` (Deleted), [Error](../definition/error.md).
1. If [To](../definition/element-label.md) is invalid or [Status](../definition/element-status.md) is greater than or equal to `4` (Deleted), [Error](../definition/error.md).
1. If [From](../definition/element-label.md) is equal to [To](../definition/element-label.md), [Error](../definition/error.md).
1. Generate a new [ID](../definition/element-id.md).
1. Create a new [Edge](../definition/edge.md) from [From](../definition/element-label.md) to [To](../definition/element-label.md)
    * Set [ID](../definition/element-id.md).
    * Set [Label](../definition/element-label.md).
    * Set [Status](../definition/element-status.md) to `1`.

## Returns

The new [Edge](../definition/edge.md).
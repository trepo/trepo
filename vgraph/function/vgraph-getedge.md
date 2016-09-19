# getEdge(ID)
Get an Edge.

## Parameters

* [ID](../definition/element-id.md) - The ID.

## Actions

1. If [ID](../definition/element-id.md) is invalid, [Error](../definition/error.md).
1. If [Edge](../definition/edge.md) identified by [ID](../definition/element-id.md) does not exist, [Error](../definition/error.md).
1. If [Label](../definition/element-label.md) is `__meta`, [Error](../definition/error.md).
1. If [Status](../definition/element-status.md) is greater than or equal to `4` (Deleted), [Error](../definition/error.md).

## Returns

The [Edge](../definition/edge.md).
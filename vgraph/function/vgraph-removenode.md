# removeNode(ID)
Add a Node.

## Parameters

* [ID](../definition/element-id.md) - The ID.

## Actions

1. If [ID](../definition/element-id.md) is invalid, [Error](../definition/error.md).
1. If [Node](../definition/node.md) identified by [ID](../definition/element-id.md) does not exist, [Error](../definition/error.md).
1. If [Status](../definition/element-status.md) is greater than or equal to `4` (Already Deleted), return.
1. Set [Status](../definition/element-status.md) to existing [Status](../definition/element-status.md) plus `4`.
1. For each connected [Edge](../definition/edge.md) where [Status](../definition/element-status.md) is less than `4` (Not Already Deleted):
    1. Set [Status](../definition/element-status.md) to existing [Status](../definition/element-status.md) plus `4`.

## Returns

`nothing`
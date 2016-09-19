# Edge.getNode(Direction)
Get the From or To Node attached to this Edge.

## Parameters

* [Direction](../definition/direction.md) - The Direction.

## Actions

1. If [Status](../definition/element-status.md) is greater than or equal to `4` (Deleted), [Error](../definition/error.md).
1. If [Direction](../definition/direction.md) is invalid or is [BOTH](../definition/direction.md), [Error](../definition/error.md).
1. If [Direction](../definition/direction.md) is [FROM](../definition/direction.md), return the [FROM](../definition/direction.md) [Node](../definition/node.md).
1. Else return the [TO](../definition/direction.md) [Node](../definition/node.md).

## Returns

The [Node](../definition/node.md).
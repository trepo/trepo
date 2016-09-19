# isBoundary()
True if this Node is a Boundary.

## Parameters

`none`

## Actions

1. If [Status](../definition/element-status.md) is greater than or equal to `4` (Deleted), [Error](../definition/error.md).
1. Get [Node Repo](../definition/node-repo.md).

## Returns

True if `Node Repo` is set, False otherwise.
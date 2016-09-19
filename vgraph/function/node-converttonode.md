# convertToNode()
Make this Boundary Node a Node.

## Parameters

`none`

## Actions

1. If [Status](../definition/element-status.md) is greater than or equal to `4` (Deleted), [Error](../definition/error.md).
1. If [Node Repo](../definition/node-repo.md) is NOT set, [Error](../definition/error.md).
1. If [Status](../definition/element-status.md) is `0`:
    1. Set [Original Repo](../definition/node-original-repo.md).
    1. Set [Status](../definition/element-status.md) to `2`.
1. Remove [Node Repo](../definition/node-repo.md).


## Returns

`nothing`
# convertToBoundary(Repo)
Make this Node a Boundary Node.

## Parameters

* [Repo](../definition/node-repo.md) - The repo to set.

## Actions

1. If [Repo](../definition/repo.md) is invalid, [Error](../definition/error.md).
1. If [Repo](../definition/node-repo.md) is the same as [vGraph Repo](../definition/repo.md), [Error](../definition/error.md).
1. If [Status](../definition/element-status.md) is greater than or equal to `4` (Deleted), [Error](../definition/error.md).
1. If [Node Repo](../definition/node-repo.md) is set, [Error](../definition/error.md).
1. If [Status](../definition/element-status.md) is `0`:
    1. Set [Original Properties](../definition/element-original-properties.md).
    1. Set [Status](../definition/element-status.md) to `2`.
1. Remove [Properties](../definition/element-properties.md).
1. Set [Node Repo](../definition/node-repo.md) to `Repo`.


## Returns

`nothing`
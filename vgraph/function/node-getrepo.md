# getRepo()
Get the Repo.

## Parameters

`none`

## Actions

1. If [Status](../definition/element-status.md) is greater than or equal to `4` (Deleted), [Error](../definition/error.md).
1. Get [Node Repo](../definition/node-repo.md).

## Returns

The [Node Repo](../definition/node-repo.md) if set, or the vGraph's [Repo](../definition/repo.md).
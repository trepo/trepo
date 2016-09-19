# info()
Get Information about this vGraph instance.

## Parameters

`none`

## Actions

1. Get the [Root Node's Repo](../definition/root-node.md).
1. Get the [Version](../README.md).
1. Get the [Latest Commit ID](../definition/commit-id.md) by following the incoming [Commit Edge](../definition/commit-edge.md) from the [Root Node](../definition/root-node.md) to the latest [Commit Node](../definition/commit-node.md).
1. Determine if there are any uncommitted changes.

## Returns

The [Info](../definition/info.md).
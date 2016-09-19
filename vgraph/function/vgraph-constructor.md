# Constructor(Repo, Graph)
Create or initialize a new instance of vGraph.

**Note:** In implementations where constructors should be light, a secondary required initialization function can be used to perform the actions.

## Parameters

* [Repo](../definition/node-repo.md) - The repo to use.
* Graph - The underlying directed property graph.

## Actions

1. If [Repo](../definition/node-repo.md) is invalid, [Error](../definition/error.md).
1. Initialize/Load/Ready `Graph`.
1. Get [Root Node](../definition/root-node.md).
1. If [Root Node](../definition/root-node.md) does not exist, create it.
    * Set [Meta](../definition/root-node.md).
    * Set [Version](../definition/root-node.md) to the [Data Version](../README.md).
    * Set [Repo](../definition/root-node.md) to [Repo](../definition/node-repo.md).
1. If [Root Node's Version](../definition/root-node.md) does NOT equal the [Data Version](../README.md), [Error](../definition/error.md).
1. If [Root Node's Repo](../definition/root-node.md) does NOT equal [Repo](../definition/node-repo.md), [Error](../definition/error.md).

**Note:** It can be helpful to keep a pointer to the last commit node. From the [Root Node](../definition/root-node.md), follow the incoming [Commit Edge](../definition/commit-edge.md) to the latest [Commit Node](../definition/commit-node.md).

**Note:** It can be helpful to keep a flag that tracks of this vGraph instance has any uncommitted changes (i.e., is `Dirty`). To initialize this, do the following:

1. For each [Node](definition/node.md):
    1. If [Status](../definition/element-status.md) does NOT equal `0`, set `Dirty` to `True` and break.
1. If NOT `Dirty`:
    1. For each [Edge](definition/edge.md):
        1. If [Status](../definition/element-status.md) does NOT equal `0`, set `Dirty` to `True` and break.

## Returns

`nothing`
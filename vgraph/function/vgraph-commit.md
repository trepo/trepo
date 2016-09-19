# commit(Author, Email, Message)
Commit all of the changes to the graph.

## Parameters

* [Author](../definition/commit-author.md) - The author of this Commit.
* [Email](../definition/commit-email.md) - The email of the author of this Commit.
* [Message](../definition/commit-message.md) - The message associated with this Commit.

## Actions

**Note:** Order is important. Edges must be updated before Nodes.

1. If [Author](../definition/commit-author.md), [Email](../definition/commit-email.md), or [Message](../definition/commit-message.md) is invalid, [Error](../definition/error.md).
1. Call [vGraph.status([Author, Email, Message])](vgraph-status.md) to get a [Commit](../definition/commit.md).
1. Create a [Commit Node](../definition/commit-node.md) with the information in [Commit](../definition/commit.md).
1. Create a [Commit Edge](../definition/commit-edge.md) from the latest [Commit Node](../definition/commit-node.md) (or the [Root Node](../definition/root-node.md) if this is the first commit) to the new [Commit Node](../definition/commit-node.md).
1. Create a [Commit Edge](commit_edge.md) from the new Commit Node to the [Root Node](../definition/root-node.md).
1. For each [Commit's Edge](../definition/commit.md) in the [Commit](../definition/commit.md) where the [Action](../definition/commit-action.md) is equal to `create`, get and update the [Edge](../definition/edge.md).
    * Set [Status](../definition/element-status.md) to `0`.
1. For each [Commit's Edge](../definition/commit.md) in the [Commit](../definition/commit.md) where the [Action](../definition/commit-action.md) is equal to `update`, get and update the [Edge](../definition/edge.md).
    * Remove [Original Properties](../definition/element-original-properties.md) if set.
    * Set [Status](../definition/element-status.md) to `0`.
1. For each [Commit's Edge](../definition/commit.md) in the [Commit](../definition/commit.md) where the [Action](../definition/commit-action.md) is equal to `delete`, remove [Edge](../definition/edge.md) from the graph.
1. For each [Commit's Node](../definition/commit.md) in the [Commit](../definition/commit.md) where the [Action](../definition/commit-action.md) is equal to `create`, get and update the [Node](../definition/node.md).
    * Set [Status](../definition/element-status.md) to `0`.
1. For each [Commit's Node](../definition/commit.md) in the [Commit](../definition/commit.md) where the [Action](../definition/commit-action.md) is equal to `update`, get and update the [Node](../definition/node.md).
    * Remove [Original Properties](../definition/element-original-properties.md) if set.
    * Remove [Original Repo](../definition/node-original-repo.md) if set.
    * Set [Status](../definition/element-status.md) to `0`.
1. For each [Commit's Node](../definition/commit.md) in the [Commit](../definition/commit.md) where the [Action](../definition/commit-action.md) is equal to `delete`, remove [Node](../definition/node.md) from the graph.
1. If there is an earlier [Commit Node](../definition/commit-node.md), remove the [Commit Edge](../definition/commit-edge.md) that was pointing from that [Commit Node](../definition/commit-node.md) to the [Root Node](../definition/root-node.md).

## Returns

The [Commit](../definition/commit.md).

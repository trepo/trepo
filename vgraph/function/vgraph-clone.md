# clone()
Clone the graph. Note that this preserves history.

## Parameters

`none`

## Actions

1. If there are uncommitted changes, [Error](../definition/error.md).
1. Create an Array or List of [Commits](../definition/commit.md) called `Commit List`.
1. For each [Current Commit Node](../definition/commit-node.md) starting at the [Root Node](../definition/root-node.md), following each incoming [Commit Edges](../definition/commit-edge.md) to the previous [Commit Node](../definition/commit-node.md), and ending at the last [Commit Node](../definition/commit-node.md):
    1. Create a new [Commit](../definition/commit.md) and add it to `Commit List`.
        * Set [id](../definition/commit-id.md) to the [Current Commit Node's ID](../definition/commit-node.md).
        * Set [prev](../definition/commit-prev.md) to the last [Commit](../definition/commit.md) or Null if `Commit List` is empty.
        * Set [timestamp](../definition/commit.md) to the [Current Commit Node's Timetamp](../definition/commit-node.md).
        * Set [repo](../definition/commit.md) to the [Current Commit Node's Repo](../definition/commit-node.md).
        * Set [author](../definition/commit-author.md) to the [Current Commit Node's Author](../definition/commit-node.md).
        * Set [email](../definition/commit-email.md) to the [Current Commit Node's Email](../definition/commit-node.md).
        * Set [message](../definition/commit-message.md) to the [Current Commit Node's Message](../definition/commit-node.md).
        * Set [nodes](../definition/commit.md) to the [Current Commit Node's Nodes](../definition/commit-node.md).
        * Set [edges](../definition/commit.md) to the [Current Commit Node's Edges](../definition/commit-node.md).
1. Return `Commit List`.

## Returns

An Array or List of [Commits](../definition/commit.md).
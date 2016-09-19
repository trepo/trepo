# Commit Node
A `Commit Node` in the underlying graph, storing a single vGraph Commit.

## ID
If the underlying graph supports setting the id on nodes, set it to the [ID](../definitions/commit-id.md) of the `vGraph Commit`.

## Label
If the underlying graph supports setting a label on nodes, set it to `__meta`.

## Properties

### __meta
Marks that this Node is a meta node.

**Value:** `__commit`.

**Note:** Set on creation.

**Note:** This property is immutable.

### __id
The ID of the `vGraph Commit`.

**Value:** [ID](../definitions/commit-id.md).

**Note:** Set on creation.

**Note:** This property is immutable.

### __repo
The repo this commit originated from.

**Value:** [Repo](../definitions/repo.md).

**Note:** Set on creation.

**Note:** This property is immutable.

### __timestamp
When this commit was made.

**Value:** [Timestamp](../definitions/timestamp.md).

**Note:** Set on creation.

**Note:** This property is immutable.

### __author
The Commit's Author.

**Value:** [Author](../definitions/commit-author.md).

**Note:** Set on creation.

**Note:** This property is immutable.

### __email
The Commit Author's Email.

**Value:** [Email](../definitions/commit-email.md).

**Note:** Set on creation.

**Note:** This property is immutable.

### __message
The Commit Message.

**Value:** [Message](../definitions/commit-message.md).

**Note:** Set on creation.

**Note:** This property is immutable.

### __nodes
The JSON Serialized String of all the Commit Nodes.

**Value:** [JSON Serialized Commit Nodes](../definitions/commit.md).

**Note:** Set on creation.

**Note:** This property is immutable.

### __edges
The JSON Serialized String of all the Commit Edges.

**Value:** [JSON Serialized Commit Edges](../definitions/commit.md).

**Note:** Set on creation.

**Note:** This property is immutable.
# Commit Edge
A `Commit Edge` in the underlying graph.

Commit Edges go from earlier Commit Nodes to later Commit Nodes. There is at most ONE Commit Edge going from the Root Node to the first Commit Node, and ONE Commit Edge going from the last Commit Node to the Root Node.

## ID
If the underlying graph supports setting the id on edges, set it to a new [UUIDv4](../definitions/uuidv4.md).

## Label
If the underlying graph supports setting a label on edges, set it to `__meta`.

## Properties

### __meta
Marks that this Node is a meta node.

**Value:** `__commit_edge`.

**Note:** Set on creation.

**Note:** This property is immutable.
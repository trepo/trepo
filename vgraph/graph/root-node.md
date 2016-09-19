# Root Node
A `Root Node` in the underlying graph.

**Note:** There must only be ONE Root Node.

## ID
If the underlying graph supports setting the id on nodes, set it to `__root`.

## Label
If the underlying graph supports setting a label on nodes, set it to `__meta`.

## Properties

### __meta
Marks that this Node is a meta node.

**Value:** `__root`.

**Note:** Set on creation.

**Note:** This property is immutable.

### __version
The version of this spec that the graph implements.

**Value:** The current [Data Version](../README.md).

**Note:** Set on creation.

**Note:** This property is immutable.

### __repo
The repository identifier for this vGraph instance.

**Value:** [Repo](../definitions/repo.md).

**Note:** Set on creation.

**Note:** This property is immutable.
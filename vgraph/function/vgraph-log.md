# log(Number, Offset)
Get Number of log entries, starting at Offset.

## Parameters

* Number - The Number of Log Entries. Must be > 0.
* Offset - How many Log Entries to skip. Must be >= 0.

## Actions

1. Starting from the [Root Node](../definition/root-node.md), follow incoming [Commit Edges](../definition/commit-edge.md) 
1. For each [Commit Node](../definition/commit-node.md) starting at the [Root Node](../definition/root-node.md) and following incoming [Commit Edges](../definition/commit-edge.md) until we return `Number` of [Log Entries](../definition/log-entry.md) or run out of [Commit Nodes](../definition/commit-node.md):
    1. If we haven't skipped `Offset` number of [Commit Nodes](../definition/commit-node.md), continue.
    1. Create [Log Entry](../definition/log-entry.md) from [Commit Node](../definition/commit-node.md) and return it.

## Returns

An array or Iterable of [Log Entries](../definition/log-entry.md).
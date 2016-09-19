# toedge
Traverse from a node to an adjoining edge.

**Parameters**

* `direction` - The direction to travel. `IN`, `OUT`, or `BOTH`.
* `labels` - An array of edge labels to filter by.
* `limit` - The maximum number of edges to follow.

**Actions**

1. Create a list called `Branched Traversals`.
1. If [Element](../definition/element.md) is not a `Node`:
    1. Set [Status](../definition/status.md) to `53`.
    1. If [Logging](../definition/logging.md), append "invalid element" to [Log](../definition/log.md).
    1. Return `null`.
1. For each `edge` in the given `direction` having a `label` in `labels` for a maximum of `limit` nodes (if `limit` is set):
    1. If `edge` is the first edge:
        1. Set [Element](../definition/element.md) to `edge`.
        1. Increment [Step](../definition/step.md) by 1.
        1. If [Logging](../definition/logging.md), append "traversed to edge {edge.id}" to [Log](../definition/log.md).
    1. Else:
        1. Copy the current traversal to `Copied Traversal`.
        1. On `Copied Traversal`:
            1. Change [Traversal Id](../definition/traversal-id.md) to a newly generated UUIDv4.
            1. Change [Element](../definition/element.md) to `edge`.
            1. Change [Status](../definition/status.md) to `11`.
            1. If [Logging](../definition/logging.md), change last entry and set message to "traversed to edge {edge.id} [branched]" in [Log](../definition/log.md).
        1. Add `Copied Traversal` to `Branched Traversals`.
1. If there were no edges in the given direction:
    1. Set [Status](../definition/status.md) to `21`.
    1. If [Logging](../definition/logging.md), append "no outgoing edges" to [Log](../definition/log.md).
    1. Return `null`.
1. Return `Branched Traversals`.
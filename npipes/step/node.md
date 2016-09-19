# node
Traverse to an adjoining node.

**Parameters**

* `direction` - The direction to travel. `IN`, `OUT`, or `BOTH`.
* `labels` - An array of edge labels to filter by.
* `limit` - The maximum number of edges to follow.

**Actions**

1. If `direction` is invalid:
    1. Set [Status](../definition/status.md) to `52`.
    1. If [Logging](../definition/logging.md), append "invalid direction" to [Log](../definition/log.md).
    1. Return `null`.
1. If `labels` is invalid:
    1. Set [Status](../definition/status.md) to `52`.
    1. If [Logging](../definition/logging.md), append "invalid labels" to [Log](../definition/log.md).
    1. Return `null`.
1. If `limit` is invalid:
    1. Set [Status](../definition/status.md) to `52`.
    1. If [Logging](../definition/logging.md), append "invalid limit" to [Log](../definition/log.md).
    1. Return `null`.
1. If [Element](../definition/element.md) is not a `Node`:
    1. Set [Status](../definition/status.md) to `53`.
    1. If [Logging](../definition/logging.md), append "invalid element" to [Log](../definition/log.md).
    1. Return `null`.
1. Create a list called `Branched Traversals`.
1. For each `node` in the given `direction` having a `label` in `labels` for a maximum of `limit` nodes (if `limit` is set):
    1. If `node` is the first node:
        1. If [Logging](../definition/logging.md), append "traversed to node {node.id}" to [Log](../definition/log.md).
        1. Set [Element](../definition/element.md) to `node`.
        1. If `node` is a boundary:
            1. Set [Status](../definition/status.md) to `30`.
            1. If [Logging](../definition/logging.md), append "node {id} is a boundary" to [Log](../definition/log.md).
        1. Increment [Step](../definition/step.md) by 1.
        1. Append `node` to the [Path](../definition/path.md).
    1. Else:
        1. Copy the current traversal to `Copied Traversal`.
        1. On `Copied Traversal`:
            1. Change [Traversal Id](../definition/traversal-id.md) to a newly generated UUIDv4.
            1. Change [Element](../definition/element.md) to `node`.
            1. Change [Status](../definition/status.md) to `11`.
            1. Change last [Path](../definition/path.md) element to be `node`.
            1. If [Logging](../definition/logging.md), remove last 1-2 entries.
            1. If [Logging](../definition/logging.md), append "traversed to node {node.id} [branched from {traversal.id}]" in [Log](../definition/log.md).
            1. If `node` is a boundary:
                1. Set [Status](../definition/status.md) to `30`.
                1. If [Logging](../definition/logging.md), append "node {id} is a boundary" to [Log](../definition/log.md).
        1. Add `Copied Traversal` to `Branched Traversals`.
1. If there were no nodes in the given direction:
    1. Set [Status](../definition/status.md) to `21`.
    1. If [Logging](../definition/logging.md), append "no outgoing edges" to [Log](../definition/log.md).
    1. Return `null`.
1. Return `Branched Traversals`.
# fromedge
Traverse from an edge to a connected node.

**Parameters**

* `direction` - The direction to travel. `IN`, `OUT`, or `BOTH`.

**Actions**

1. If `direction` is invalid:
    1. Set [Status](../definition/status.md) to `52`.
    1. If [Logging](../definition/logging.md), append "invalid direction" to [Log](../definition/log.md).
    1. Return `null`.
1. If [Element](../definition/element.md) is not an `Edge`:
    1. Set [Status](../definition/status.md) to `53`.
    1. If [Logging](../definition/logging.md), append "invalid element" to [Log](../definition/log.md).
    1. Return `null`.
1. Create a list called `Branched Traversals`.
1. Increment [Step](../definition/step.md) by 1.
1. If `direction` equals `OUT`:
    1. Set [Element](../definition/element.md) to the from node.
    1. Append `node` to the [Path](../definition/path.md).
    1. If [Logging](../definition/logging.md), append "traversed to from node {node.id}" to [Log](../definition/log.md).
    1. If `node` is a boundary:
        1. Set [Status](../definition/status.md) to `30`.
        1. If [Logging](../definition/logging.md), append "node {id} is a boundary" to [Log](../definition/log.md).
1. Else If `direction` equals `IN`:
    1. Set [Element](../definition/element.md) to the to node.
    1. Append `node` to the [Path](../definition/path.md).
    1. If [Logging](../definition/logging.md), append "traversed to to node {node.id}" to [Log](../definition/log.md).
    1. If `node` is a boundary:
        1. Set [Status](../definition/status.md) to `30`.
        1. If [Logging](../definition/logging.md), append "node {id} is a boundary" to [Log](../definition/log.md).
1. Else:
    1. Copy the current traversal to `Copied Traversal`.
    1. On `Traversal`:
        1. Set [Element](../definition/element.md) to the from node.
        1. Append `node` to the [Path](../definition/path.md).
        1. If [Logging](../definition/logging.md), append "traversed to from node {node.id}" to [Log](../definition/log.md).
        1. If `node` is a boundary:
            1. Set [Status](../definition/status.md) to `30`.
            1. If [Logging](../definition/logging.md), append "node {id} is a boundary" to [Log](../definition/log.md).
    1. On `Copied Traversal`:
        1. Change [Traversal Id](../definition/traversal-id.md) to a newly generated UUIDv4.
        1. Set [Element](../definition/element.md) to the to node.
        1. Append `node` to the [Path](../definition/path.md).
        1. Change [Status](../definition/status.md) to `11`.
        1. If [Logging](../definition/logging.md), append "traversed to to node {node.id} [branched]" to [Log](../definition/log.md).
        1. If `node` is a boundary:
            1. Set [Status](../definition/status.md) to `30`.
            1. If [Logging](../definition/logging.md), append "node {id} is a boundary" to [Log](../definition/log.md).
1. Return `Branched Traversals`.
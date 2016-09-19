# get
Go directly to an element.

**Parameters**

* `id` - The id of the element.
* `type` - The type of element. `node` or `edge`.

**Actions**

1. If `id` is invalid:
    1. Set [Status](../definition/status.md) to `52`.
    1. If [Logging](../definition/logging.md), append "invalid id" to [Log](../definition/log.md).
    1. Return `null`.
1. If `type` is invalid:
    1. Set [Status](../definition/status.md) to `52`.
    1. If [Logging](../definition/logging.md), append "invalid type" to [Log](../definition/log.md).
    1. Return `null`.
1. Get the `element` identified by `id` and `type` from vGraph.
1. If `element` does not exist:
    1. Set [Status](../definition/status.md) to `53`.
    1. If [Logging](../definition/logging.md), append "{type} {id} not found" to [Log](../definition/log.md).
    1. Return `null`.
1. If [Logging](../definition/logging.md), append "{type} {id} retrieved" to [Log](../definition/log.md).
1. If `element` is a `Boundary Node`:
    1. Set [Status](../definition/status.md) to `30`.
    1. If [Logging](../definition/logging.md), append "{type} {id} is a boundary" to [Log](../definition/log.md).
1. Append `element` to the [Path](../definition/path.md).
1. Set [Element](../definition/element.md) to `element`.
1. Increment [Step](../definition/step.md) by 1.
1. Return `null`.

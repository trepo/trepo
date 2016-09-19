# exists
From a node, if an edge exists, then goto step X, else go to step Y.

**Parameters**

* `then` - The step to go to if an edge exists.
* `else` - The step to go to if an edge does not exist.
* `direction` - The direction to travel. `IN`, `OUT`, or `BOTH`.
* `labels` - An array of edge labels to filter by.

**Actions**

1. If `direction` is invalid:
    1. Set [Status](../definition/status.md) to `52`.
    1. If [Logging](../definition/logging.md), append "invalid direction" to [Log](../definition/log.md).
    1. Return `null`.
1. If `labels` is invalid:
    1. Set [Status](../definition/status.md) to `52`.
    1. If [Logging](../definition/logging.md), append "invalid labels" to [Log](../definition/log.md).
    1. Return `null`.
1. If `then` is invalid:
    1. Set [Status](../definition/status.md) to `52`.
    1. If [Logging](../definition/logging.md), append "invalid then" to [Log](../definition/log.md).
    1. Return `null`.
1. If `else` is invalid:
    1. Set [Status](../definition/status.md) to `52`.
    1. If [Logging](../definition/logging.md), append "invalid else" to [Log](../definition/log.md).
    1. Return `null`.
1. If [Element](../definition/element.md) is not a `Node`:
    1. Set [Status](../definition/status.md) to `53`.
    1. If [Logging](../definition/logging.md), append "invalid element" to [Log](../definition/log.md).
    1. Return `null`.
1. If at least one `edge` exists in the given `direction` having a `label` in `labels`:
    1. If [Logging](../definition/logging.md), append "edges exist: setting step to {then}" to [Log](../definition/log.md).
    1. Set [Step](../definition/step.md) to `then`.
1. Else:
    1. If [Logging](../definition/logging.md), append "edges do not exist: setting step to {else}" to [Log](../definition/log.md).
    1. Set [Step](../definition/step.md) to `else`.
1. Return `null`.
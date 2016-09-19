# mark
Mark an element so we can backtrack to it later.

**Parameters**

* `marker` - The marker value.

**Actions**

1. If [Element](../definition/element.md) is not a `Node` or `Edge`:
    1. Set [Status](../definition/status.md) to `53`.
    1. If [Logging](../definition/logging.md), append "invalid element" to [Log](../definition/log.md).
    1. Return `null`.
1. Add `marker` to `markers` in the last element in [Path](../definition/path.md).
1. If [Logging](../definition/logging.md), append "marked element {element.id} as {marker}" to [Log](../definition/log.md).
1. Increment [Step](../definition/step.md) by 1.
1. Return `null`.
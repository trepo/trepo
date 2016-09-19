# back
Backtrack to a marked element.

**Parameters**

* `marker` - The marker to backtrack to.

**Actions**

1. For each element in [Path](../definition/path.md) starting at the last element:
    1. If `marker` is in `markers`:
        1. Add element to the [Path](../definition/path.md) (`markers` should be empty in the new element).
        1. If `repo` is this repo:
            1. If `element does not exist in this repo:
                1. Set [Status](../definition/status.md) to `53`.
                1. If [Logging](../definition/logging.md), append "{type} {id} not found" to [Log](../definition/log.md).
                1. Return null.
            1. Set [Element](../definition/element.md) to `element`.
            1. If [Logging](../definition/logging.md), append "{type} {id} retrieved" to [Log](../definition/log.md).
        1. Else:
            1. Set [Status](../definition/status.md) to `31`.
            1. If [Logging](../definition/logging.md), append "{type} {id} is in repo {repo}" to [Log](../definition/log.md).
        1. Finally:
            1. Increment [Step](../definition/step.md) by 1.
            1. Break.
1. If there was no element in [Path](../definition/path.md) that contained `marker`:
    1. Set [Status](../definition/status.md) to `53`.
    1. If [Logging](../definition/logging.md), append "marker not found" to [Log](../definition/log.md).
1. Return `null`.
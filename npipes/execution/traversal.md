# Traversal Execution


**Actions**

1. Create a list called `New Traversals`.
1. If [Path](../definition/path.md) has elements in it:
    1. Get the last element of [Path](../definition/path.md).
    1. Retrieve that element from vGraph.
    1. If element does not exist:
        1. Set [Status](../definition/status.md) to `53`.
        1. If [Logging](../definition/logging.md), append "{type} {id} not found" to [Log](../definition/log.md).
        1. Return `New Traversals`.
    1. Else If element is a boundary:
        1. Add that element to [Path](../definition/path.md).
        1. Set [Status](../definition/status.md) to `30`.
        1. If [Logging](../definition/logging.md), append "{type} {id} is a boundary" to [Log](../definition/log.md).
        1. Return `New Traversals`.
    1. Else, set [Element](../definition/element.md) to the vGraph element.
1. Set [Status](../definition/status.md) to `13`.
1. While [Step](../definition/step.md) is less than the length of [Steps](../definition/steps.md):
    1. If [Status](../definition/status.md) does NOT equal `13`, Return `New Traversals`.
    1. If [Step name](../definition/step.md) is invalid:
        1. Set [Status](../definition/status.md) to `52`.
        1. If [Logging](../definition/logging.md), append "invalid step name" to [Log](../definition/log.md).
    1. Else:
        1. Execute the `Step` in [Steps](../definition/steps.md) identified by [Step](../definition/step.md).
        1. Add any returned traversals to `New Traversals`.
1. Set [Status](../definition/status.md) to `20`.
1. Return `New Traversals`.

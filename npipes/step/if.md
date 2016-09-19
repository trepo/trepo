# if
If expression is true, goto step X, else goto step Y.

**Note:** variables referenced but not existing in payload are assumed to be null. 

**Parameters**

* `left` - The left variable referring to a key in the payload.
* `operator` - The operator. One of `>`, `<`, `==`, `!=`, `>=`, `<=`.
* `right` - The right variable referring to a key in the payload.
* `then` - The step to go to if an edge exists.
* `else` - The step to go to if an edge does not exist.

**Actions**

1. If `left` is invalid:
    1. Set [Status](../definition/status.md) to `52`.
    1. If [Logging](../definition/logging.md), append "invalid left" to [Log](../definition/log.md).
    1. Return `null`.
1. If `operator` is invalid:
    1. Set [Status](../definition/status.md) to `52`.
    1. If [Logging](../definition/logging.md), append "invalid operator" to [Log](../definition/log.md).
    1. Return `null`.
1. If `right` is invalid:
    1. Set [Status](../definition/status.md) to `52`.
    1. If [Logging](../definition/logging.md), append "invalid right" to [Log](../definition/log.md).
    1. Return `null`.
1. If `then` is invalid:
    1. Set [Status](../definition/status.md) to `52`.
    1. If [Logging](../definition/logging.md), append "invalid then" to [Log](../definition/log.md).
    1. Return `null`.
1. If `else` is invalid:
    1. Set [Status](../definition/status.md) to `52`.
    1. If [Logging](../definition/logging.md), append "invalid else" to [Log](../definition/log.md).
    1. Return `null`.
1. If `left` `operator` `right` evaluates to true:
    1. If [Logging](../definition/logging.md), append "{left} {operator} {right} is true: setting step to {then}" to [Log](../definition/log.md).
    1. Set [Step](../definition/step.md) to `then`.
1. Else:
    1. If [Logging](../definition/logging.md), append "{left} {operator} {right} is false: setting step to {else}" to [Log](../definition/log.md).
    1. Set [Step](../definition/step.md) to `else`.
1. Return `null`.
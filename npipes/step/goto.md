# goto
Go to step X.

**Parameters**

* `step` - The step to go to.

**Actions**

1. If `step` is invalid:
    1. Set [Status](../definition/status.md) to `52`.
    1. If [Logging](../definition/logging.md), append "invalid step" to [Log](../definition/log.md).
    1. Return `null`.
1. If [Logging](../definition/logging.md), append "going to step {step}" to [Log](../definition/log.md).
1. Set [Step](../definition/step.md) to `step`.
1. Return `null`.
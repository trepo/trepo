# inc
Increment a value in the traversal payload.

**Parameters**

* `key` - The payload value to add to. 
* `amount` - The amount to add. Must be a number. 

**Actions**

1. If `key` is invalid:
    1. Set [Status](../definition/status.md) to `52`.
    1. If [Logging](../definition/logging.md), append "invalid key" to [Log](../definition/log.md).
    1. Return `null`.
1. If `amount` is invalid:
    1. Set [Status](../definition/status.md) to `52`.
    1. If [Logging](../definition/logging.md), append "invalid amount" to [Log](../definition/log.md).
    1. Return `null`.
1. If `key` in [Payload](../definition/payload.md) is not a number:
    1. Set [Status](../definition/status.md) to `51`.
    1. If [Logging](../definition/logging.md), append "{key} is not a number" to [Log](../definition/log.md).
    1. Return `null`.
1. Set the key identified by `key` in [Payload](../definition/payload.md) to the value of that key plus `amount`.
1. If [Logging](../definition/logging.md), append "{amount} added to {key}" to [Log](../definition/log.md).
1. Increment [Step](../definition/step.md) by 1.
1. Return `null`.
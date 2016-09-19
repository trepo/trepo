# set
Set values in the traversal payload.

**Parameters**

* `values` - A Map between payload keys and values. 

**Actions**

1. If `values` is invalid:
    1. Set [Status](../definition/status.md) to `52`.
    1. If [Logging](../definition/logging.md), append "invalid values" to [Log](../definition/log.md).
    1. Return `null`.
1. For each `key`, `value` in `values`:
    1. Set the key identified by `key` in [Payload](../definition/payload.md) to the `value`.
    1. If [Logging](../definition/logging.md), append "{key} set in payload" to [Log](../definition/log.md).
1. Increment [Step](../definition/step.md) by 1.
1. Return `null`.
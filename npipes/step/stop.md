# stop
Stop the traversal.

**Parameters**

`none`

**Actions**

1. If [Logging](../definition/logging.md), append "stopping" to [Log](../definition/log.md).
1. Set [Status](../definition/status.md) to `23`.
1. Return `null`.
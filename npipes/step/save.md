# save
Save element properties in the traversal payload.

**Parameters**

* `meta` - A Map between payload keys and meta properties (id, label, repo, boundary). 
* `props` - A Map between payload keys and properties. 

**Actions**

1. If `meta` is invalid:
    1. Set [Status](../definition/status.md) to `52`.
    1. If [Logging](../definition/logging.md), append "invalid meta" to [Log](../definition/log.md).
    1. Return `null`.
1. If `props` is invalid:
    1. Set [Status](../definition/status.md) to `52`.
    1. If [Logging](../definition/logging.md), append "invalid props" to [Log](../definition/log.md).
    1. Return `null`.
1. For each `payload key` `meta property key` pair in `meta`:
    1. If `meta property key` is invalid:
        1. Set [Status](../definition/status.md) to `52`.
        1. If [Logging](../definition/logging.md), append "invalid meta property key {meta property key}" to [Log](../definition/log.md).
1. For each `payload key` `property key` pair in `props`:
    1. If `property key` is invalid:
        1. Set [Status](../definition/status.md) to `52`.
        1. If [Logging](../definition/logging.md), append "invalid property key {property key}" to [Log](../definition/log.md).
1. If [Status](../definition/status.md) is not `13`:
    1. Return `null`.
1. If [Element](../definition/element.md) is not a `Node` or `Edge`:
    1. Set [Status](../definition/status.md) to `53`.
    1. If [Logging](../definition/logging.md), append "invalid element" to [Log](../definition/log.md).
    1. Return `null`.
1. For each `payload key` `meta property key` pair in `meta`:
    1. Retrieve the meta property identified by `meta property key`.
    1. Set the key identified by `payload key` in [Payload](../definition/payload.md) to the meta property.
    1. If [Logging](../definition/logging.md), append "{payload key} set to meta property {meta property key}" to [Log](../definition/log.md).
1. For each `payload key` `property key` pair in `props`:
    1. Retrieve the property identified by `property key`.
    1. If property does not exist, property is set to null.
    1. Set the key identified by `payload key` in [Payload](../definition/payload.md) to the property.
    1. If [Logging](../definition/logging.md), append "{payload key} set to property {property key}" to [Log](../definition/log.md).
1. Increment [Step](../definition/step.md) by 1.
1. Return `null`.
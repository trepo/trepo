# setProperties(Properties)
Sets the properties to Properties.

## Parameters

* [Properties](../definition/element-properties.md) - The properties to set.

## Actions

1. For each [Key](../definition/element-properties.md) and [Value](../definition/element-properties.md) in `Properties`:
    1. If [Key](../definition/element-properties.md) is invalid, [Error](../definition/error.md).
    1. If [Value](../definition/element-properties.md) is invalid, [Error](../definition/error.md).
1. If [Status](../definition/element-status.md) is greater than or equal to `4` (Deleted), [Error](../definition/error.md).
1. If [Element Properties](../definition/element-properties.md) are equal to `Properties`, return. This is to prevent meaningless updates from generating actual changes.
1. If [Status](../definition/element-status.md) is `0`:
    1. Set [Original Properties](../definition/element-original-properties.md).
    1. Set [Status](../definition/element-status.md) to `2`.
1. Set [Element Properties](../definition/element-properties.md) to `Properties`.

## Returns

`nothing`
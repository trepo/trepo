# setProperty(Key, Value)
Sets the property value identified by Key.

## Parameters

* [Key](../definition/element-property.md) - The property key to set.
* [Value](../definition/element-property.md) - The property value to set.

## Actions

1. If [Key](../definition/element-properties.md) is invalid, [Error](../definition/error.md).
1. If [Value](../definition/element-properties.md) is invalid, [Error](../definition/error.md).
1. If [Status](../definition/element-status.md) is greater than or equal to `4` (Deleted), [Error](../definition/error.md).
1. If `Key` is already set to `Value`, return. This is to prevent meaningless updates from generating actual changes.
1. If [Status](../definition/element-status.md) is `0`:
    1. Set [Original Properties](../definition/element-original-properties.md).
    1. Set [Status](../definition/element-status.md) to `2`.
1. Set `Key` to `Value`.

## Returns

`nothing`
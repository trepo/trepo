# getProperty(Key)
Returns the property value identified by Key.

## Parameters

* [Key](../definition/element-property.md) - The property key to retrieve.

## Actions

1. If [Key](../definition/element-properties.md) is invalid, [Error](../definition/error.md).
1. If [Status](../definition/element-status.md) is greater than or equal to `4` (Deleted), [Error](../definition/error.md).
1. Get the [Property](../definition/element-properties.md).

## Returns

A list of [Property](../definition/element-properties.md) keys.
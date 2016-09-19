# getProperty(Key)
Returns the property value identified by Key.

## Parameters

* [Key](../definition/element-property.md) - The property key to retrieve.

## Actions

1. If [Node Repo](../definition/node-repo.md) is set, [Error](../definition/error.md).
1. Call and return [element.getProperty(Key)](element-getproperty.md).

## Returns

A list of [Property](../definition/element-properties.md) keys.
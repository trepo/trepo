# setProperty(Key, Value)
Sets the property value identified by Key.

## Parameters

* [Key](../definition/element-property.md) - The property key to set.
* [Value](../definition/element-property.md) - The property value to set.

## Actions

1. If [Node Repo](../definition/node-repo.md) is set, [Error](../definition/error.md).
1. Call and return [element.setProperty(Key, Value)](element-setproperty.md).

## Returns

`nothing`
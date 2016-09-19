# addNode(Label)
Add a Node.

## Parameters

* [Label](../definition/element-label.md) - The Label.

## Actions

1. If [Label](../definition/element-label.md) is invalid, [Error](../definition/error.md).
1. Generate a new [ID](../definition/element-id.md).
1. Create a new [Node](../definition/node.md)
    * Set [ID](../definition/element-id.md).
    * Set [Label](../definition/element-label.md).
    * Set [Status](../definition/element-status.md) to `1`.

## Returns

The new [Node](../definition/node.md).
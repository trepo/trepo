# Element
A `vGraph Node` or `vGraph Edge` in the underlying graph.

## ID
If the underlying graph supports setting the id on the node or edge, set it to the [ID](../definition/element-id.md) of the `vGraph Element`.

## Label
If the underlying graph supports setting a label on the node or edge, set it to the [Label](../definition/element-label.md) of the `vGraph Element`.

## Properties

### __id
The `vGraph Element's` ID.

**Value:** [ID](../definition/element-id.md).

**Note:** Set on creation ONLY IF the underlying graph does NOT support setting the id on the node or edge.

**Note:** If set, this property is immutable.

### __label
The `vGraph Element's` Label.

**Value:** [Label](../definition/element-label.md).

**Note:** Set on creation ONLY IF the underlying graph does NOT support setting a label on the node or edge.

**Note:** If set, this property is immutable.

### __status
The status of the element.

**Value:** [Status](../definition/element-status.md).

### __origProps
A JSON String of the `Element Properties` before they were modified.

**Value:** [Original Properties](../definition/element-original-properties.md).

**Note:** This is set when `__status` is changed from `0` to `2`.

### Element Properties
The `vGraph Element's` [Properties](../definition/element-properties.md).

**Note:** These are set or removed after creation.

**Note:** If `__repo` is set, no Element Properties are allowed to be set. Boundary Nodes have no local properties.
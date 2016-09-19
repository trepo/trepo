# Node
A `vGraph Node` in the underlying graph. Inherits from [Element](element.md).

## ID
[See Element](element.md).

## Label
[See Element](element.md).

## Properties
[See Element](element.md).

### __repo
A repository identifier marking this Node as a boundary Node.

**Value:** [Repo](../definitions/repo.md).

**Note:** Set on creation if this `vGraph Node` is a boundary Node.

**Note:** This may not be the same repository identifier used for this vGraph instance.

### __origRepo
The value of `__repo` before it was modified.

**Value:** [Repo](../definitions/repo.md).

**Note:** This is set when `__status` is changed from `0` to `2`.

### Other Node Properties
[See Element](element.md).

**Note:** If `__repo` is set, no Element Properties are allowed to be set. Boundary Nodes have no local properties.

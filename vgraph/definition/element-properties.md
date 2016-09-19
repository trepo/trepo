# Element Properties
Properties set on a [Node](node.md) or [Edge](edge.md). These should not be confused with the metadata properties used by vGraph. To distinguish between them, all vGraph specific property keys start with `__` (e.g. `__repo`, __status`, etc...).

## Requirements
The property key must match the regex `[A-Za-z][A-Za-z0-9_]{0,254}`.

The value must be one of:

* boolean
* int/long x bits
* double/float x precision
* string (UTF-8) x characters
* homogeneous array of one of the above types
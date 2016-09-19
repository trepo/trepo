# ID
A [UUIDv4](http://en.wikipedia.org/wiki/Universally_unique_identifier#Version_4_.28random.29) that universally identifies a [Traversal](traversal.md).

## Requirements
Each [Traversal](traversal.md) MUST have a unique ID. If a traversal branches or splits into 2 or more traversals, the first traversal retains the id of the original traversal, and each subsequent traversal is assigned a NEW ID.
# Traversal
A path through the graph determined by a set of instruction along with any information collected along that path.

**Components:**

* [ID](traversal-id.md) - The unique identifier for this [Traversal](traversal.md).
* [Status](status.md) - The current status of the [Traversal](traversal.md).
* [Path](path.md) - The set of nodes and edges that were followed in the [Traversal](traversal.md).
* [Element](element.md) - The element the [Traversal](traversal.md) is currently on. Note that this is transative.
* [Payload](payload.md) - Information that was collected during the [Traversal](traversal.md).
* [Steps](steps.md) - A set of instructions that determines the path to follow through the graph and what information to save along the way.
* [Step](step.md) - The current [Step](steps.md) the [Traversal](traversal.md) is on.
* [Limit](limit.md) - The limit to how many steps will be run when this traversal is executed.
* [Log](log.md) - A Set of Log Entries describing what occurred during traversal execution.
* [Logging](logging.md) - If logging is on or off.

**JSON Example:**

````javascript
{
  "id": "e1ad1607-13f1-459d-8717-4994a4cbcd35",
  "status": 10,
  "path": [],
  // Note that element is never serialized
  "payload": {},
  "steps": [...],
  "step": 0,
  "limit": 0,
  "log": [],
  "logging": false
}
````

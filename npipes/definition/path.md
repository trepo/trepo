# Path
A List of Elements that a [Traversal](traversal.md) has visited.

## Components

* `id` - The element's ID.
* `type` - One of `edge`, `node`, or `boundary`.
* `repo` - The repository the element resides in (or points to, if a boundary).
* `markers` - An array of markers.

## JSON Representation

````javascript
{
  "id": "",
  "type": "",
  "repo": "",
  "markers": []
}
````
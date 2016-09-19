# Commit
A bundle of changes that have been applied to vGraph. It is composed of some metadata about the changes, and a set of actions to apply to the graph (nodes/edges). Note that all commits contain both the information to apply them AND the information to undo them.

**Note:** To see how commits are created, see [vGraph.commit()](../function/vgraph-commit.md).

**Note:** To see how commits are interpreted and applied, see [vGraph.patch()](../function/vgraph-patch.md).

## Properties

### Commit

* version - The [Commit Version](../README.md).
* [id](commit-id.md) - The id of the Commit.
* [prev](commit-prev.md) - The id of the previous Commit.
* [timestamp](timestamp.md) - When this Commit was made.
* [repo](repo.md) - The Repo this commit was made from.
* [author](commit-author.md) - The author of this Commit.
* [email](commit-email.md) - The email of the author of this Commit.
* [message](commit-message.md) - The message associated with this Commit.
* nodes - An array of Nodes (defined below).
* edges - An array of Edges (defined below).

### Node

* [id](element-id.md) - The node's ID.
* [label](element-label.md) - The node's Label.
* [action](commit-action.md) - The action to take when applying this node.
* [boundary](commit-boundary.md) - A Boolean representing whether or not this represents a [Boundary Node](boundary-node.md).
* [repo](repo.md) - If this represents a [Boundary Node](boundary-node.md), the [Repo](repo.md) it points to.
* [origRepo](repo.md) - The original value of repo, if any.
* [props](element-properties.md) - A Map of the properties.
* [origProps](element-properties.md) - A Map of the original properties, if any.

### Edge

* [id](element-id.md) - The node's ID.
* [label](element-label.md) - The node's Label.
* [from](element-id.md) - The Id of the node this edge comes from.
* [to](element-id.md) - The Id of the node this edge goes to.
* [action](commit-action.md) - The action to take when applying this node.
* [props](element-properties.md) - A Map of the properties.
* [origProps](element-properties.md) - A Map of the original properties, if any.

## Validation

Commit is invalid if:

* `version` does not equal [Commit Version](../README.md).
* `id` is null or invalid.
* `prev` is invalid (null is ok).
* `repo`, `timestamp`, `author`, `email`, or `message` is null or invalid.
* `nodes` is null or not an array.
* any node in `nodes` is invalid.
* `edges` is null or not an array.
* any edge in `edges` is invalid.
* any edge in `edges` references a `from` or `to` node not in `nodes`.

A node in nodes is invalid if:

* `id`, `label`, `action`, or `boundary` is null or invalid.
* `boundary` is `true` and:
    * `action` equals `create` and:
        * `repo` is null or invalid.
        * `origRepo`, `props`, or `origProps` is set.
    * `action` equals `update` and:
        * `repo` is null or invalid.
        * `origRepo` and `origProps` are both set.
        * `origRepo` and `origProps` are both NOT set.
        * `props` is set.
    * `action` equals `delete` and:
        * `origRepo` is null or invalid.
        * `repo`, `props`, or `origProps` is set.
    * `action` equals `reference` and:
        * `repo` is null or invalid.
        * `origRepo`, `props`, or `origProps` is set.
* `boundary` is `false` and:
    * `action` equals `create` and:
        * `props` is null or invalid.
        * `repo`, `origRepo`, or `origProps` is set.
    * `action` equals `update` and:
        * `props` is null or invalid.
        * `origRepo` and `origProps` are both set.
        * `origRepo` and `origProps` are both NOT set.
        * `repo` is set.
    * `action` equals `delete` and:
        * `origProps` is null or invalid.
        * `repo`, `origRepo`, or `props`, is set.
    * `action` equals `reference`.

An edge in edges is invalid if:

* `id`, `label`, `from`, `to`, or `action` is null or invalid.
* `action` equals `create` and:
    * `props` is null or invalid.
    * `origProps` is set.
* `action` equals `update` and:
    * `props` or `origProps` is null or invalid.
* `action` equals `delete` and:
    * `origProps` is null or invalid.
    * `props` is set.
* `action` equals `reference`.

## Valid Property Configuration Table

**Nodes:**

|                           | action | boundary | repo | origRepo | props | origProps |
| :-----------------------: | :----: | :------: | :--: | :------: | :---: | :-------: |
| **Create Node**           | create | False    |      |          | X     |           |
| **Update Node**           | update | False    |      |          | X     | X         |
| **Delete Node**           | delete | False    |      |          |       | X         |
| **Create Boundary Node**  | create | True     | X    |          |       |           |
| **Update Boundary Node**  | update | True     | X    | X        |       |           |
| **Delete Boundary Node**  | delete | True     |      | X        |       |           |
| **Boundary Node -> Node** | update | False    |      | X        | X     |           |
| **Node -> Boundary Node** | update | True     | X    |          |       | X         |

**Edges:**

|                 | action | props | origProps |
| :-------------: | :----: | :---: | :-------: |
| **Create Edge** | create | X     |           |
| **Update Edge** | update | X     | X         |
| **Delete Edge** | delete |       | X         |

## JSON Representation

**Commit:**
````javascript
{
  "version": 4,
  "id": "13f89cee-0e32-470f-8f89-96f340778988",
  "prev": "0141c67f-336b-49b7-927f-1708702fead7",
  "repo": "https://example.com/repo",
  "timestamp": 1443114901291,
  "author": "Bob Freemer",
  "email": "bob@freemer.org",
  "message": "This is a commit!",
  "nodes": [
    {...},
    {...}
  ],
  "edges": [
    {...},
    {...}
  ]
}

// Node
{
  "id": "2910f6c4-e8d4-45d9-83fc-3d8bee4c0269",
  "label": "label",
  "action": "update",
  "boundary": false,
  "props": {"foo":"bar"},
  "origProps": {}
}

// Boundary Node
{
  "id": "3125b578-f473-41e2-82a2-806e30d0b6d9",
  "label": "label",
  "action": "update",
  "boundary": true,
  "repo": "https://example.com/new-repo",
  "origRepo": "https://example.com/old-repo"
}

// Node -> Boundary
{
  "id": "4f08d4c1-8ef1-4f84-97a2-e25ecd691663",
  "label": "label",
  "action": "update",
  "boundary": true,
  "repo": "https://example.com/new-repo",
  "origProps": {"foo":"bar"}
}

// Boundary -> Node
{
  "id": "5f589aa2-4e19-4157-b4b1-ca922338ddee",
  "label": "label",
  "action": "update",
  "boundary": false,
  "props": {"foo":"bar"},
  "origRepo": "https://example.com/old-repo"
}

// Edge
{
  "id": "657c041d-1dbe-4502-9d1b-4886cc0aa259",
  "label": "label",
  "from": "78b6e52a-a3d3-40af-b6ba-63d1c7b268d1",
  "to": "8d624f85-69a3-4205-8c15-579565fe4eb3",
  "action": "update",
  "props": {"foo":"bar"},
  "origProps": {}
}

// Reference Node
{
  "id": "9168bc4a-5d11-4186-a5db-7c3ff9028e3f",
  "label": "label",
  "action": "reference",
  "boundary": true,
  "repo": "https://example.com/new-repo"
}
````
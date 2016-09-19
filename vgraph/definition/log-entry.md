# Log Entry
An entry in the Commit Log.

## Properties

* [id](commit-id.md) - The id of the Commit.
* [repo](repo.md) - The Repo this commit was made from.
* [timestamp](timestamp.md) - When this Commit was made.
* [author](commit-author.md) - The author of this Commit.
* [email](commit-email.md) - The email of the author of this Commit.
* [message](commit-message.md) - The message associated with this commit.

## JSON Representation

````javascript
{
  "id": "13f89cee-0e32-470f-8f89-96f340778988",
  "repo": "https://example.com/repo",
  "timestamp": 1443114901291,
  "author": "Bob Freemer",
  "email": "bob@freemer.org",
  "message": "This is a commit!"
}
````
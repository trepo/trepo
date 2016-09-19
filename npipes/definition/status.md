# Status
A code representing the current status of the [Traversal](traversal.md).

# Requirements
Status is always a positive 2-digit integer (ie. XX).

# Status Codes

## 1X Informational

* 10 - New - A New Traversal
* 11 - Branched - A Branched Traversal.
* 12 - Resumed - The Traversal has been resumed, but is not yet running.
* 13 - Running - The Traversal is running.

## 2X Complete

* 20 - Finished -  The Traversal ran to completion.
* 21 - Done -  The Traversal completed without completing every step.
* 22 - Paused - The Traversal is paused.
* 23 - Stopped - The Traversal is stopped.

## 3X Redirection

* 30 - Boundary - Encountered a Boundary Node and Traversal must switch to a new repository.
* 31 - Back Track - The Traversal backtracked to another repository and must continue the Traversal there.

## 4X Remote Error

* 40 - Remote Error - Could not access repository to start/continue traversal for unspecified reasons.
* 41 - Unauthorized - Could not execute query in remote repository due to insuficient permissions.

## 5X Traversal Error

* 50 - Traversal Error - An unspecified traversal error.
* 51 - Invalid State - The Traversal encountered an invalid step (`node(id).toNode()` is invalid).
* 52 - Invalid Step - The Step is invalid (usually due to improper parameters).
* 53 - Missing Element - The requested element does not exist.
* 54 - Timeout - The Traversal Timed Out. // TODO move to 4X? Split into Traversal Timeout and Remote Timeout?
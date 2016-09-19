# UUIDv4
A Universally Unique Identifier. In vGraph, all UUIDs are [Version 4 (random)](https://en.wikipedia.org/wiki/Universally_unique_identifier#Version_4_.28random.29) and stored as a string of lowercase hexadecimal digits (e.g., `a91f6599-bb27-4987-8b16-d7861ae0397c`).

The regex for a UUIDv4 is `[0-9a-f]{8}-[0-9a-f]{4}-4[0-9a-f]{3}-[89ab][0-9a-f]{3}-[0-9a-f]{12}`.
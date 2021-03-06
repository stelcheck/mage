## Client vault

This vault is used to send updates to the player, so that their data is always synchronized in real
time. This vault is always created when an archivist is instantiated by a `State` object, using a
name identical to the type: `client`.

### Configuration

This vault type requires no configuration.

### Supported operations

operation | supported | implementation
----------|:---------:|---------------
list      |           |
get       |           |
add       | ✔         | `state.emitToActors('archivist:set')`
set       | ✔         | `state.emitToActors('archivist:set' or 'archivist:applyDiff')`
touch     | ✔         | `state.emitToActors('archivist:touch')`
del       | ✔         | `state.emitToActors('archivist:del')`

### Required Topic API

signature                  | required | default implementation
---------------------------|:--------:|-----------------------
`createKey(topic, index)`  |          | `{ topic: topic, index: index }`
`serialize(value)`         |          | `{ mediaType: '', data: '', encoding: 'utf8/base64' }`
`shard(value)`             | ✔        |

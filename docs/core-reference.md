## Core Reference {#core}

### EventBus > `bp.events`{#core-eventbus}

The EventBus is an instance of [EventEmmitter2](https://github.com/asyncly/EventEmitter2), so all of its features are available. 

#### `emit(name, [arg])`

##### Example

```js
bp.events.emit('messenger.connected', { connected: true })
```

#### `on(name, listener)`

##### Wildcards

The instance is configured with wildcards enabled, the wildcard delimiter is **`.`**.

##### Example
```js
bp.events.on('messenger.connected', event => {
  bp.logger.info('Messenegr connected')
})

// accepts wildcards (*)
bp.events.on('messenger.*', event => /* ... */)
```

### Database > `bp.db`{#core-database}

#### `get() -> Promise(knex)`

Returns an instance of the [knex](http://knexjs.org/) database query builder. It is configured to use a SQLite3 database located in `${dataDir}/db.sqlite`.

##### Example

```js
bp.db.get()
.then(knex => 
   knex('users')
   .where({ gender: 'male' }}
   .limit(10))
.then(users => /* ... */)
```

#### `saveUser(UserObject) -> Promise()`

Saves a user in the built-in `users` table. **Does not** overwrite existing entries (they are ignored). An entry is considered unique by the union of `id` and `platform`.

##### User Object

```js
{ id: string, // *required*
  platform: string, // *required*
  gender: string, // nullable
  timezone: integer (-12, +14), // nullable
  locale: string // nullable
}
```

### Middlewares > `bp.middlewares` {#core-middlewares}

### Logger > `bp.logger` {#core-logger}

### Modules > `bp.modules` {#core-modules}

### Notifications > `bp.notifications` {#core-notifications}

### HTTP Server > `bp.server` {#core-server}

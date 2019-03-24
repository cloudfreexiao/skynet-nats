NATS skynet library
================
[NATS Protocol](https://nats.io/documentation/internals/nats-protocol/)

Usage
-----

### Basic usage: Subscribe / Unsubscribe

```lua
local nats = require 'nats'

-- connect to the server
local client = nats.connect({
    host = '127.0.0.1',
    port = 4222,
})

-- callback function for subscriptions
local function subscribe_callback(payload)
    print('Received data: ' .. payload)
end

-- subscribe to a subject
local subscribe_id = client:subscribe('foo', subscribe_callback)

-- wait until 2 messages come
client:wait(2)

-- unsubscribe from the subject
client:unsubscribe(subscribe_id)
```

### Basic usage: Publish

```lua
local nats = require 'nats'
-- connect to the server
local client = nats.connect({
    host = '127.0.0.1',
    port = 4222,
})
-- publish to a subject
local subscribe_id = client:publish('foo', 'message to be published')
```

### Basic usage: User authentication

```lua
local nats = require 'nats'

local client = nats.connect({
    host = '127.0.0.1',
    port = 4222,
})

-- user authentication
local user, password = 'user', 'password'
client:set_auth(user, password)

-- connect to the server
client:connect()
```

--------


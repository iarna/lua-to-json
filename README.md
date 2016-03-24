lua-to-json
-----------

```javascript
var luaToJson = require('lua-to-json')
var luaSrc = fs.readFileSync('/path/to/file.lua', 'utf8')
var lua = luaToJson(luaSrc)
console.log(JSON.stringify(lua, null, 2)) // pretty print as JSON
```

This converts a series of lua variable declarations (with tables) into their
JSON equivalent.

The top level object returned has all the top level var names as keys, eg:

```lua
foo = 23
bar = {
  ["abc"] = "def"
}
```

will become

```json
{
  "foo": 23,
  "bar": {
    "abc": "def"
  }
}
```

Actual code will result in errors, as will identifiers outside of the
left-hand-side of assignments. The Lua parser is provided by
[luaparser](https://npmjs.com/package/luaparser). The evaluator is provided
by this module, and may be incomplete as yet.

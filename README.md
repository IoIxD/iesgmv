# iesgmv

ioi's experimental scriptable gba memory viewer

yeah I couldn't figure out mgba's debugging tools in regards to just wanting to monitor and edit memory (I think you're supposed to be able to edit memory somehow? but I couldn't figure it out) so I whipped this into existence to be able to use lua scripts to programatically do shit.

based on [rustboyadvance-ng](https://github.com/michelhe/rustboyadvance-ng) because that's in rust and i've found the rust crate for lua to be easier to use then lua's C API, sorry. this means it's probably not as accurate or whatever as mgba but also this is primairly to be used with a fucking kirby game so shrug.

It also struggles to reach 60fps because it has to call to Lua so much, I've tried to optimize this as much as I can but at the end of the day it still reaches 55fps as the best case scenario so I don't really care.

# usage

Basically you create a Lua script with functions that can intercept any reads/writes to memory, and you can log them or swap out values as you please. Either function can be excluded.

Both functions return a boolean to signify whether to actually intercept the read/write. Returning false means that whatever memory address was supposed to be read/written will be done so on the emulator, returning true (naturally) means otherwise. On the read callback specifically, you also have to return the value that should be read, even if you're not intercepting (just return `0, false` for that)

Example:

```lua
---@param addr number The address we're reading from in game memory
function on_read(addr)
    print(addr)
    return 0, false
end

---@param addr number The address we're writing to in game memory
---@param value number The value expected to be written to this address
function on_write(addr, value)
    print(addr, value)
    return false
end
```

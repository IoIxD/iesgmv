# iesgmv

ioi's experimental scriptable gba memory viewer

yeah I couldn't figure out mgba's debugging tools in regards to just wanting to monitor and edit memory (I think you're supposed to be able to edit memory somehow? but I couldn't figure it out) so I whipped this into existence to be able to use lua scripts to programatically do shit.

based on [rustboyadvance-ng](https://github.com/michelhe/rustboyadvance-ng) because that's in rust and i've found the rust crate for lua to be easier to use then lua's C API, sorry. this means it's probably not as accurate or whatever as mgba but also this is primairly to be used with a fucking kirby game so shrug

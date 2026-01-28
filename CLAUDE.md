# Programming in Atmos + pico-lua

- Atmos: The Programming Language
    - https://github.com/atmos-lang/atmos/
    - Manual:
        - https://github.com/atmos-lang/atmos/blob/main/doc/manual-out.md

- pico-sdl: Graphics Library for 2D Games and Appplications
    - https://github.com/fsantanna/pico-sdl/

- pico-lua: Lua bindings for pico-sdl
    - https://github.com/fsantanna/pico-sdl/tree/main/lua/
        - Based on SDL

- Games developed in Atmos + pico-lua:
    - Birds: https://github.com/atmos-lang/pico-birds
    - Rocks: https://github.com/atmos-lang/pico-rocks

# Idioms and Caveats:

- `pico.set.*` becomes `pico.zet.*` (because `set` is a keyword in Atmos)
- Atmos has no precendence for binary operators:
    - use parenthesis to disambiguate
    - `1 + 2*3` becomes `1 + (2*3)`
- Key events:
    - `every it in :key.dn { ... }`
    - `it.key` can be `:Left`, `:Up`, etc
- Color values:
    - use r,g,b fields
    - `@{ r=0xCC, g=0x11, b=77 }`
- `pub` is a special public variable for tasks
    - use `set pub = ...` inside
    - use `t.pub = ...` outside
- Pattern matching:
    - `match` if possible
    - `ifs` as second option
    - `if` as third option

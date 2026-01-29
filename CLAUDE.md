# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A "Run!" game implemented in Atmos with pico-lua graphics. Player avoids enemies that spawn from screen edges.

## Running the Game

```bash
atmos run.atm
```

**Dependencies** (install via luarocks with Lua 5.4):
- `pico-sdl` - Graphics library
- `atmos-lang` - Atmos compiler/runtime

## Atmos Language References

- Manual: https://github.com/atmos-lang/atmos/blob/main/doc/manual-out.md
- pico-lua: https://github.com/fsantanna/pico-sdl/tree/main/lua/
- Example games: https://github.com/atmos-lang/pico-birds, https://github.com/atmos-lang/pico-rocks

## Atmos Idioms and Caveats

**Operator precedence**: Atmos has none. Always use parentheses.
```
1 + (2*3)       ;; correct
1 + 2*3         ;; error
```

**pico.set becomes pico.zet**: `set` is a keyword in Atmos.

**Color values**: Use named fields.
```
@{ r=0xCC, g=0x11, b=0x77 }
```

**Key events**:
```
every it in :key.dn {
    match it.key {
        :Left  => ...
        :Right => ...
    }
}
```

**Pattern matching preference**: `match` > `ifs` > `if`. Exhaust cases when possible (avoid `else`).

**Statements as expressions**:
```
var x,y = match edge {
    1 => (a, b)
    2 => (c, d)
}
```

**Task public state**: Use `set pub = ...` inside tasks, access via `t.pub` outside.

**Singletons**: Don't use `tasks()` pools for single instances. Use `pin player = spawn Player()` directly.

**Collisions**: Pass `task.pub.rect` to `pico.vs.rect_rect()`.

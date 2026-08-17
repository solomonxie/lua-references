# Lua References

A personal sandbox for trying out everything about Lua.

The goal is coverage, not polish: every language feature, standard library
corner, idiom, and popular rock gets a small, runnable script that proves how
it actually behaves. Scripts are meant to be read, run, and modified.

## Layout

```text
Makefile      Environment setup: Lua, LuaJIT, LuaRocks, LSP, libraries
dataset/      Sample data used by the scripts
helloworld/   Numbered walkthrough scripts, one topic each
modules/      Reusable modules extracted from the experiments
```

## Setup

Requires macOS with Homebrew. On other platforms, install Lua and LuaRocks with
your package manager and skip to the library step.

```bash
make install-lua    # brew install lua luarocks, plus luajit via x86_64 brew
make install-lib    # inspect, penlight, debugger, lua-cjson, luasocket
make install-lsp    # lua-language-server for Neovim
```

Or all three at once:

```bash
make install
```

## Running

Any script runs directly with the interpreter, from the repo root:

```bash
lua helloworld/02-table.lua
luajit helloworld/02-table.lua
```

Scripts that read data expect the repo root as the working directory.

## What is covered

- [helloworld/01-helloworld.lua](helloworld/01-helloworld.lua) — `print`, running a script
- [helloworld/02-table.lua](helloworld/02-table.lua) — tables as array and hash map, mixed and quoted keys, nesting, recursive pretty printing
- [helloworld/03-lib.lua](helloworld/03-lib.lua) — `require`, using a rock (`inspect`), reading a metatable
- [helloworld/04-debug.lua](helloworld/04-debug.lua) — interactive breakpoints with the `debugger` rock
- [helloworld/05-csv-parse.lua](helloworld/05-csv-parse.lua) — string patterns, splitting, Penlight's `pl.stringx`
- [helloworld/06-iterator.lua](helloworld/06-iterator.lua) — closures as stateful iterators, custom `enumerate`, line iteration
- [helloworld/07-parse-csv-file.lua](helloworld/07-parse-csv-file.lua) — file streaming vs. batch reading, building a parser module
- [helloworld/08-io.lua](helloworld/08-io.lua) — `io.open`, reading and writing files, `f:read` loops
- [modules/csv1.lua](modules/csv1.lua) — CSV line parser handling quoted fields and embedded separators
- [modules/csv2.lua](modules/csv2.lua) — CSV loader using metatables for field access by column name

## What is next

Topics not yet covered, roughly in the order they are worth trying:

- Functions: varargs, multiple returns, tail calls
- Metatables in depth: `__index`, `__call`, `__eq`, operator overloading
- Object orientation: prototype tables, inheritance chains, closures as objects
- Modules and packages: `package.path`, `package.cpath`, writing a rock
- Errors: `pcall`, `xpcall`, `error` levels, custom error objects
- Coroutines: generators, producer/consumer, scheduling
- Standard library: `string.format`, `string.gsub` callbacks, `table.*`, `os.*`, `math.*`
- Text processing: full pattern syntax, frontier pattern, `%b` balanced match
- JSON with `lua-cjson`, networking with `luasocket`
- Garbage collection: weak tables, `__gc`, `collectgarbage` tuning
- The C API and FFI: LuaJIT `ffi`, calling C from Lua and back
- Differences between Lua 5.1, 5.3, 5.4, and LuaJIT
- Testing with `busted`, linting with `luacheck`

## License

[MIT](LICENSE)

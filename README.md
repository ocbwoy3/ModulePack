# ModulePack
A Roblox Plugin to compress a ModuleScript with descending modules into a singular script.

*It's here because Roblox falsely banned the plugin for "Misusing Roblox Systems", because it has `loadstring`, `require` and `getfenv`.*

<img src="https://cdn.ocbwoy3.dev/assets/modulepack_moderation.png" alt="Ban Appeal" width="50%" height="auto">

Plugin link: https://roblox.com/library/18850572774 (banned by roblox)

## How to Use

Just use the script like it's a normal MainModule, however do not add Models, Parts and stuff in the module itself, use LoadAssets instead.

Allowed Instances: ModuleScript, Folder, LocalScript
All other instances and ther properties are not serialized.

This will freeze studio if the script is too large!!!!!!!

> [!WARNING]
> This is intended for scripts that run on the server, however it also supports LocalScripts, however **\*\*Luau is not supported!!!!!!\*\***, because loadstring is not avaiable from LocalScripts, or Loadstring-disabled games may use something like FiOne and Yueilang to compile.
> Don't use `+=`, `-=`, `*=`, `/=` and other Luau features in LocalScripts as they will error, unless Roblox plans to bring loadstring to the client.

### Cloning `LocalScripts`

If you need to clone LocalScripts, use `clone_localscript(localscript)`, which returns another LocalScript, which is the cloned one.

```lua
clone_localscript(script.LocalScript).Parent=owner.PlayerGui
```

### Luau binding directives

If you are planning on using Luau on the server, I recommend enabling Luau bindings.

```lua
local function something(a: something, b: somethingelse) --luau_binding : something|: somethingelse
local function foo(bar: baz) --luau_binding : baz
```
will be turned into
```lua
local function something(a, b)
local function foo(bar)
```

You can add as many somethings in luau binding comments, but they must be seperated with a pipe symbol.

### NoMap directives

```lua
local owner = game.Players.OCboy3 --!nomap
```

The `--!nomap` comment directive deletes the line if it's parsed.

# UE3 v1 (2019-2021)

Auto Assembler scripts for a 32 bit and 64 bit game client.

**Language:** Auto Assembler (Cheat Engine)

## Speed Hack

Two part system: enable the inject first, then the activator.

**Inject** (`speedhack_x86_inject` / `speedhack_x64_inject`)

AOB scans for the speed comparison instruction and hooks it. Runs register guard conditions on every match to narrow down the correct call site, then captures the address of the speed float into the `offset` symbol.

**Activator** (`speedhack_x86_activator` / `speedhack_x64_activator`)

Spawns a thread that polls `offset` every 50ms. Uses `isBadReadPtr` as a safety check, writes `speedvalue` to the address when valid, and falls back to a 1 second retry loop while the pointer is not yet populated. Restores speed to 1.0 on disable.

Edit `speedvalue` (default: 15) to set the desired speed.

## Fly Hack

Single script per architecture (`flyhack_x86` / `flyhack_x64`). AOB hooks the vertical movement calculation and replaces it with a three mode selector.

| Symbol | Effect |
|--------|--------|
| `gravity` | Zeroes vertical force |
| `altitude` | Constant upward push |
| `clip` | Constant downward push |

Set the desired symbol to `1` to activate. Only one mode is active at a time.

## Notes

- `module_name_here` is a placeholder. Fill it in with the correct module name before use.

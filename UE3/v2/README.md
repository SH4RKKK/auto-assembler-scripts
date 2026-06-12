# UE3 v2 (2025)

Rewritten Auto Assembler scripts for a game client running on a private server build. Supersedes the v1 script.

**Language:** Auto Assembler (Cheat Engine)

## Speed Hack

Single script (`speedhack_x64`). Directly hooks the instruction that writes the speed float to the actor and replaces the value with `speedvalue` on every invocation. No separate inject or activator needed.

Edit `speedvalue` (default: 15) to set the desired speed.

## Notes

- x64 only.
- `module_name_here` is a placeholder. Fill it in with the correct module name before use.

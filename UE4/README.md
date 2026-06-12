# UE4 (2021-2023)

Auto Assembler scripts for a game client on the UE4 engine version.

**Language:** Auto Assembler (Cheat Engine)

## Fly Hack

Two part system: enable the pointer finder first, then the inject.

**Inject** (`flyhack/flyhack_inject`)

AOB hooks the position write instruction and replaces it with a mode selector.

| Symbol | Effect |
|--------|--------|
| `gravity` | Freezes vertical position |
| `altitude` | Constant upward push |
| `clip` | Constant downward push |
| `bossx` | Locks position to a saved coordinate set |

Set the desired symbol to `1` to activate.

**Pointer finder** (`flyhack/flyhack_ptr`)

Spawns a thread that traverses the GEngine pointer chain to locate the player position pointer. Uses `isBadReadPtr` guards at each step. Stores the resolved address in `ptr1` for the inject to reference.

**Console troll variant** (`flyhack/flyhack_console_troll`)

All in one script combining the fly hook with a console that prints a message on a loop. Uses a hardcoded pointer chain instead of the pointer finder.

## Console

**`console/open_console`**

Opens a Windows console window and redirects stdout to it. Frees its own memory on completion. Enable this before any script that prints output.

**`console/packet_reader`**

AOB hooks a packet dispatch call and prints each packet ID to the console as it arrives. Requires `open_console` to be enabled first.

## Autoquest

**`autoquest/autoquest_function_ptr`**

AOB hooks the quest argument write and captures a pointer to the daily quest argument structure into `daily_quest_ptr`.

**`autoquest/autoquest_caller`**

Calls the quest function with zone specific arguments on a loop. Only implemented for one specific quest in this version.

## Notes

- `module_name_here` is a placeholder. Fill it in with the correct module name before use.

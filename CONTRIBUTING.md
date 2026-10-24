# Contributing

Thanks for adding to the list. One PR, one entry.

**Don't want to touch Git?** [Share a port](https://github.com/emrehangorgec/awesome-llm-on-anything/issues/new?template=new-port.yml) by pasting a single link. A maintainer adds the row and you get credited in the commit. Not sure it qualifies? Ask in the [tips thread](https://github.com/emrehangorgec/awesome-llm-on-anything/discussions/6).

## What qualifies

- Inference runs **on the device itself**. If the device only sends prompts to a model elsewhere, it goes in *Thin clients*.
- It ran on **real hardware**. Ports shown only in an emulator go in *Emulator only* until someone runs them on the real thing.
- The port works. Abandoned or unfinished attempts are welcome in the PR description, not in the tables.
- There is public proof: a repository or write-up, ideally with a photo or video of the device.

## What to include

- **Device:** name, CPU, RAM, and any extra hardware it needs (RAM expansion, PSRAM, special board).
- **Model:** the actual checkpoint, not the engine. `stories15M, int8` is right; `llama2.c` is not. Include parameter count and precision or quantization.
- **Speed:** tokens per second, or time per token for very slow ports. Say whether it is generation speed only or total time including prompt processing and loading. Link to where the number comes from. If no number exists, write `?`.

## How to add a row

1. Pick the right section: *Retro computers*, *Consoles and handhelds*, or *Microcontrollers*. If none fits, propose a new section in the PR.
2. Add one row:

   ```
   | Device (key specs) | Model, precision | Reported speed | [repo](link) · [write-up](link) |
   ```

3. Keep rows sorted by device age, oldest first.

## Updating an existing row

Replacing a `?` with a sourced speed is one of the most useful contributions. So is moving an *Emulator only* entry up after running it on real hardware: link the photo or video.

# Awesome LLM on Anything [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> Language models running locally on hardware that has no business running them.

Retro PCs, game consoles, handhelds, microcontrollers. If it has a CPU and someone got tokens out of it, it belongs here.

**The one rule:** inference must run **on the device itself**, on real hardware. Devices that only talk to a model elsewhere go in *Thin clients*. Ports shown only in an emulator go in *Emulator only*.

**Seen one we're missing?** [Paste a link](https://github.com/emrehangorgec/awesome-llm-on-anything/issues/new?template=new-port.yml), we fill in the rest.

**About the speeds:** every number is what the port's author reported, linked to its source. Nobody here re-benchmarked them. Models, quantization and tokenizers differ between rows, so treat speeds as flavor, not a ranking. `?` means no speed is recorded in this list yet.

## Contents

- [Retro computers](#retro-computers)
- [Consoles and handhelds](#consoles-and-handhelds)
- [Microcontrollers](#microcontrollers)
- [Wearables](#wearables)
- [Emulator only](#emulator-only)
- [Thin clients](#thin-clients)
- [Extremes](#extremes)
- [Wanted](#wanted)
- [Foundations](#foundations)
- [Related](#related)

## Retro computers

| Device                             | Model                    | Reported speed                       | Project                                                                                                          |
| ---------------------------------- | ------------------------ | ------------------------------------ | ---------------------------------------------------------------------------------------------------------------- |
| Commodore 64 with 2MB REU          | stories260K              | ~1 token per 8 min (author estimate) | [llama2.c64](https://github.com/ytmytm/llama2.c64)                                                               |
| 486 DX2 66 MHz, 32MB RAM, DOS 6.22 | stories260K              | 2.08 tok/s                           | [dosllam2](https://github.com/yeokm1/dosllam2) · [write-up](https://yeokhengmeng.com/2025/04/llama2-llm-on-dos/) |
| Pentium II, 128MB RAM, Windows 98  | stories260K / stories15M | 39.31 / 1.03 tok/s                   | [llama98.c](https://github.com/exo-explore/llama98.c) · [write-up](https://blog.exolabs.net/day-4/)              |

## Consoles and handhelds

| Device                                                                    | Model                                                    | Reported speed                            | Project                                                                                                                                                                              |
| ------------------------------------------------------------------------- | -------------------------------------------------------- | ----------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Nintendo 64, VR4300 93.75 MHz, 4 to 8MB RAM, EverDrive 64                 | Legend of Elya, 819K, quantized (precision not reported) | ?                                         | [write-up](https://elyanlabs.ai/n64-llm.html)                                                                                                                                        |
| PlayStation 2, Emotion Engine 294 MHz, 32MB RAM, weights streamed from CD | brandon-tiny-10m-instruct, Q8                            | ?                                         | [ps2-llm](https://github.com/xaskasdf/ps2-llm)                                                                                                                                       |
| PlayStation Portable                                                      | stories260K                                              | ?                                         | [llama2-psp](https://github.com/caiomadeira/llama2-psp)                                                                                                                              |
| Nintendo Wii, 88MB RAM, 729 MHz PowerPC                                   | stories15M, int8                                         | 61.9 tok/s (GPU engine), 12.7 tok/s (CPU) | [iiama2.c](https://github.com/brysontang/iiama2.c)                                                                                                                                   |
| PS Vita PCH-1000, ARM Cortex-A9 overclocked to 555 MHz                    | stories260K / stories15M                                 | ~120 / ~1.8 tok/s                         | [psvita-llm](https://github.com/callbacked/psvita-llm)                                                                                                                               |
| New Nintendo 3DS, ARM11 804 MHz with L2, Homebrew Launcher                | stories15M, Q8_0 / Q4                                    | 18.46 / 23.28 tok/s generation            | [3DS port](https://github.com/nikopoulospet/llama2.c/tree/3ds-port#3-hardware-milestones)                                                                                            |
| Nintendo Switch, Tegra X1, Switchroot Linux                               | Llama 3.2 3B Instruct, Q4_K_M                            | 3.50 tok/s generation                     | [write-up](https://nocoffei.com/?p=352)                                                                                                                                              |
| PowKiddy V90, MiyooCFW (CPU and RAM not specified in write-up)            | stories260K, precision not reported                      | ?                                         | [Tiny LLM](https://github.com/TriForceX/MiyooCFW/wiki/Tiny-LLM)                                                                                                                      |
| Xbox Series S, Developer Mode, 6 CPU threads, 311MB peak model RAM        | LFM2.5-350M, Q4_0 QAD                                    | 101.6 tok/s CPU generation (median of 3)  | [xllama](https://github.com/gianlucamazza/xllama) · [measurements](https://github.com/gianlucamazza/xllama/blob/main/docs/model-matrix.md#a1-console-validated-performance-series-s) |

Nintendo 64: the author reports running on real hardware, but the linked source repository is currently unavailable. The author withdrew earlier speed claims, so no speed is listed. The V90 write-up is credited to Ordinary_Tension5730. New 3DS inference runs on the handheld; WiFi only carries the generated output to a laptop. Xbox measurements are for Series S only; Series X is untested.

## Microcontrollers

| Device                                                                         | Model              | Reported speed      | Project                                                                                 |
| ------------------------------------------------------------------------------ | ------------------ | ------------------- | --------------------------------------------------------------------------------------- |
| ESP32-S3 with 2MB PSRAM                                                        | stories260K        | 19.13 tok/s         | [esp32-llm](https://github.com/DaveBben/esp32-llm)                                      |
| Four ESP32 boards, with and without PSRAM                                      | 260K, FP32         | 2.32 to 22.00 tok/s | [ESP32-Tiny-LLM](https://github.com/Circuit-Digest/ESP32-Tiny-LLM)                      |
| Raspberry Pi Pico (RP2040)                                                     | stories260K        | ?                   | [picollama260k](https://github.com/tarelerulz/pico-experiments/tree/main/picollama260k) |
| RP2350 board with 16MB flash and 8MB PSRAM (standard Pico 2 boards won't work) | bundled 14MB model | ~850 ms per token   | [PicoLlama](https://github.com/earlephilhower/PicoLlama)                                |

## Wearables

| Device                                                       | Model                         | Reported speed | Project                                            |
| ------------------------------------------------------------ | ----------------------------- | -------------- | -------------------------------------------------- |
| Google Pixel Watch 3, Wear OS 5, 32 bit ARM, ~0.5GB free RAM | SmolLM2-360M-Instruct, Q4_K_M | ~1 to 4 tok/s  | [wear-llm](https://github.com/mkornreich/wear-llm) |

## Emulator only

Real ports, but so far only shown running in an emulator. Moves to the tables above once someone runs it on real hardware.

- [semu-c64](https://github.com/trholding/semu-c64) - A RISC-V emulator running on the C64, running llama2.c with a 240K 8 bit model. Shown in VICE at ~3000% warp: about 25 minutes for two tokens.

## Thin clients

The model runs elsewhere, but the device is still delightfully wrong.

- [doschgpt](https://github.com/yeokm1/doschgpt) - ChatGPT, Hugging Face and Ollama client for DOS, with Sound Blaster text to speech.
- [Ti83_LLM_ESP32](https://github.com/MostlyFunctionalEngineering/Ti83_LLM_ESP32) - A TI-83 calculator talking to an online LLM through an ESP32.

## Extremes

Not a benchmark, just an extreme example from the list.

- 🐢 **Slowest:** Commodore 64, about one token every 8 minutes. The first visible word shows up after roughly 16 minutes.

## Wanted

We haven't found a documented on-device port for these yet. If one exists, or you build one, tell us (see Contributing below).

- Game Boy / Game Boy Advance
- Kindle (e-ink)
- Graphing calculator (inference on the calculator itself)

## Foundations

- [llama2.c](https://github.com/karpathy/llama2.c) - Karpathy's single file C inference. Almost every tiny port above starts here.
- [llama.cpp](https://github.com/ggml-org/llama.cpp) - The engine behind most ports to bigger hardware.

## Related

- [Can It Run AI?](https://elyanlabs.ai/can-it-run-ai.html) - A museum style catalog of AI and local compute on vintage hardware, with evidence links.

## Contributing

Got a model running on a toaster? Two ways in.

**No Git needed:** [share a port](https://github.com/emrehangorgec/awesome-llm-on-anything/issues/new/choose) by pasting one link. We fill in the details, add the row and credit you.

**Open a PR:** read [CONTRIBUTING.md](CONTRIBUTING.md) and add one row.

Missing a speed or spotted a wrong number? [Fix an entry](https://github.com/emrehangorgec/awesome-llm-on-anything/issues/new?template=update-entry.yml). Only have a rumor? Drop it in the [tips thread](https://github.com/emrehangorgec/awesome-llm-on-anything/discussions/6).

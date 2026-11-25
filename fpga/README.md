# fpga/ — Quartus Prime project

This folder holds the hardware side of the design. Place your Quartus Prime 18.1 project here:

```
fpga/
├── <project>.qpf            project file
├── <project>.qsf            EP4CE115F29C7 device + DE2-115 pin assignments
├── <project>.v              top level, instantiates the Platform Designer system
├── <system>.qsys            Platform Designer system
├── <system>.sopcinfo        used by nios2-bsp to build the BSP
└── output_files/
    └── <project>.sof        compiled bitstream
```

### Platform Designer contents

| Name | Core | Notes |
|---|---|---|
| `nios2_gen2_0` | Nios II Gen2 | /f core recommended |
| FPU | Floating Point Hardware 2 | on the CPU custom-instruction port |
| `onchip_memory2_0` | On-Chip RAM | 128 KB |
| `jtag_uart_0`, `timer_0` | JTAG UART, Interval Timer | console, system timer |
| `audio_pll_0` | Audio Clock | 12.288 MHz codec clock |
| `audio_and_video_config_0` | Audio/Video Config | mic input, 16-bit, 8 kHz |
| `audio_0` | Audio (UP) | memory-mapped FIFOs |
| `switches`, `keys`, `ledr`, `ledg` | PIO | SW, KEY, LEDR, LEDG |

`audio_0`, `switches`, `keys`, `ledr` and `ledg` must keep these names: the firmware uses their `*_BASE` addresses.

Generated folders (`db/`, `incremental_db/`, the Platform Designer output folder) are ignored by Git.

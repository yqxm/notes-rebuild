note-type:: Reference
source-type:: book
source-id:: riscv-spec

- #+BEGIN_PINNED
  Waterman, A., & Asanović, K. (2019). The RISC-V Instruction Set Manual: Vol. Unprivileged ISA (v20191213 ed.).p2-3
  #+END_PINNED
- A RISC-V hardware platform can contain one or more RISC-V-compatible processing cores toghether with:
	- Other non-RISC-V-compatible cores
	- Fixed-function accelerators
	- various physical memory structures
	- I/O devices
	- An interconnect structure to allow the components to communicate
- **core**: A component is termed a *core* if it contains an independent instruction fetch unit.[[R20002 --- Instruction Fetch unit]]
- **hart**: Hardware threads. A RISC-V compatible core might support multiple harts thourgh multithreading.
- **coprocessor**: A unit that is attached to a RISC-V core and is mostly sequenced by a RISC-V instruction stream, but which contains additional architectural state and instruction-set extensions, and possibly some limited autonomy relative to the primary RISC-V instruction stream.
- **accelerator**: Either a non-programmable fixed-function unit or a core that can operate autonomously but is specialized for certain tasks.
-
-
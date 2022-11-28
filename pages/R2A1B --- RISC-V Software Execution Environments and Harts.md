- #+BEGIN_PINNED
  Waterman, A., & Asanović, K. (2019). The RISC-V Instruction Set Manual: Vol. Unprivileged ISA (v20191213 ed.). c1.2
  #+END_PINNED
- The behavior of a RISC-V program depends on the execution environment in which it runs. A RISC-V execution environment interface(**EEI**) defines:
	- the initial state of the program
	- the number and type of harts in the environment including the privilege modes supported by the harts
	- the accessibility and attributes of memory and I/O regions
	- the behavior of all instruction executed on each hart
	- the handling of every exception and interrups raised during execution including envirionment calls.
	- The implementation of a RISC-V execution environment can be pure hardware, pure software, or a combination of hardware and software. Some functionality not provided by hardware can be implement by software.
		- *Example of execution environment implementation*
			- **"Bare metal" hardware platform**
				- "Bare metal" hardware platforms where harts are directly implemented by physical processor threads and instructions have full access to the physical address space.
					- The hardware platform defines an execution environment that begins at power-on reset.[[R20003 --- Power-on reset]]
			- **RISC-V operating system**
				- It provide multiple user-level execution environments by multiplexing user-level harts onto available physical processor threads and by controlling access to memory via virtual memory.
			- **RISC-V hypervisors**
				- It provide multiple supervisor-level execution environments for guest operating systems.
			- **RISC-V emulators**
				- Such as Spike, QEMU or rv8, which emulate RISC-V harts on an underlying x86 system, and which can provide either a user-level or supervisor-level execution environment.
			- #+BEGIN_NOTE
			  A bare hardware platform can be considered to define an EEI.
			  Often EEIs are layered on top of one another, where one higher-level EEI uses another lower-level EEI.
			  #+END_NOTE
	- From the perspective of software running in a given execution environment, a hart is a resource that autonomously fetches and executes RISC-V instructions within that execution environment. In this respect, a hart behaves like a hardware thread resource.
	- The execution environment is responsible for ensuring the eventual forward progress of each of its harts.
		- For a given hart,
			- that responsibility is suspended while the hart is exercising a mechanism that waits for an event.
			- that responsibility ends if the hart is terminated.
		- The following events constitute forward progress:
			- The retirement of an instruction
			- A trap
			- Any other event defined by an extension to constitute forward progress.
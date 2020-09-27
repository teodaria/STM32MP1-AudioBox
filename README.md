# STM32MP1-AudioBox

STM32MP1-AudioBox is a project built around STM32MP157C-DK2 development board which allows to add an audio interface for musical instruments to the MP1 development kit.
The project is based on two main items:
* An audio interface board, based on the codec AD1938 from Analog Devices, which integrates the codec, the input and output connector as well as a 40 pin connector to plug this piece of hardware on the STM32MP157C-DK2 board. The main features of the board are:
	* AD1938 codec
	* 2 inputs connector
	* 2 otputs connector
	* Headphones connector
	* Simple analog circuitry to properly handle the signals (more work to be done here to add input gain control and headphones gain)
The board has been designed using KiCad EDA: A Cross Platform and Open Source Electronics Design Automation Suite.
This repository contains the source for the hardware.
* A custom linux distribution based on Open Embedded, which integrates:
	* Standard BSP layer from STMicroelectronics
	* Kernel patch for the ASoC codec driver and the linux device tree
	* Audio software as provided by the meta-musicians Open Embedded layer
Git repo is used to manage the distribution: a manifest containing all the git repositories is made available easily download all the required OE layers and start the distro build quickly.


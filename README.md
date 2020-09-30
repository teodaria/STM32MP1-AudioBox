# STM32MP1-AudioBox

**STM32MP1-AudioBox** is a project built around [**STM32MP157C-DK2**](https://www.st.com/en/evaluation-tools/stm32mp157c-dk2.html) development board which adds an audio interface for musical instruments to the MP1 development kit.

The project is based on two main items:
* An **audio interface board** based on the codec AD1938 from Analog Devices, which integrates the codec, the input and output connector as well as a 40 pin connector to plug this piece of hardware on the STM32MP157C-DK2 board. The main features of the board are:
	* AD1938 codec
	* 2 inputs connector
	* 2 otputs connector
	* Headphones connector
	* Simple analog circuitry to properly handle the signals (more work to be done here to add input gain control and headphones gain)
The board has been designed using KiCad EDA: A Cross Platform and Open Source Electronics Design Automation Suite.
The sources for the hardware is freely available [here](https://github.com/teodaria/audio_hw_if).
* A **custom linux distribution** based on Open Embedded, which integrates:
	* Standard OE/Yocto [BSP layer from STMicroelectronics](https://github.com/STMicroelectronics/meta-st-stm32mp)
	* [Custom OE layer](https://github.com/teodaria/meta-audiobox-kernel) containing kernel patch for the ASoC codec driver and the linux device tree 
	* [Custom OE layer](https://github.com/teodaria/meta-audiobox-distro) containing images and distribution definitions
	* Audio software as provided by the [meta-musicians OE layer](https://github.com/schnitzeltony/meta-musicians)
Git repo is used to manage the distribution: a [manifest](https://github.com/teodaria/MP1-audiobox-manifest) is made available to easily download all the required OE layers and quickly start the distribution build.

A simple "lopback" project (audio acquired from input is simply sent to the output) is available for those who want to experiment in the development of low level audio processing.
High level, third party software is included as well in the image, to quick start in known territory.




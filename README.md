# STM32MP1-AudioBox

**STM32MP1-AudioBox** is a project built around [**STM32MP157C-DK2**](https://www.st.com/en/evaluation-tools/stm32mp157c-dk2.html) development board which adds an audio interface for musical instruments to the MP1 development kit.

The project is based on two main items:
* An **audio interface board** based on the codec AD1938 from Analog Devices, which integrates the codec, the input and output connectors as well as a 40 pin connector to plug this piece of hardware on the STM32MP157C-DK2 board. The main features of the board are:
	* AD1938 codec
	* 2 inputs connectors
	* 2 otputs connectors
	* Headphones connector
	* Simple analog circuitry to properly handle the signals (more work to be done here to add input gain control and headphones gain)
	
The board has been designed using [KiCad EDA](https://kicad-pcb.org/): a Cross Platform and Open Source Electronics Design Automation Suite.
The sources for the hardware is freely available [here](https://github.com/teodaria/audio_hw_if).

![image info](./img/AudioBoxRender.png)
![image info](./img/board_1.jpg)
![image info](./img/board_2.jpg)


* A **custom linux distribution** based on Open Embedded, which integrates:
	* Standard OE/Yocto [BSP layer from STMicroelectronics](https://github.com/STMicroelectronics/meta-st-stm32mp)
	* [Custom OE layer](https://github.com/teodaria/meta-audiobox-kernel) containing kernel patch for the ASoC codec driver, a custom ASoC machine driver and the linux device tree 
	* [Custom OE layer](https://github.com/teodaria/meta-audiobox-distro) containing images and distribution definitions
	* Audio software as provided by the [meta-musicians OE layer](https://github.com/schnitzeltony/meta-musicians). By default 3 audio-related open source applications are installed in the rootfs:
		* [Guitarix](https://guitarix.org/?_sm_nck=1): a virtual guitar amplifier for Linux running on Jack Audio Connection Kit
		* [Calf studio gear](https://calf-studio-gear.org/): stand-alone effect rack connectable through Jack sound server or as plug-ins in every audio host that is able to fire up LV2 compilant devices
		* [Carla](https://kx.studio/Applications:Carla): a modular audio plugin host with support for many audio drivers and plugin format.
	
Git repo is used to manage the distribution: a [manifest](https://github.com/teodaria/MP1-audiobox-manifest) is made available to easily download all the required OE layers and quickly start the distribution build.


A simple "loopback" project (audio acquired from input is simply sent to the output) is available for those who want to experiment in the development of low level audio processing.
The third party software is included in the image for a quick start in known territory.




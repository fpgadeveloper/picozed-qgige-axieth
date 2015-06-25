picozed-qgige-axieth
=====================

Example design for the [Quad Gigabit Ethernet FMC](http://ethernetfmc.com "Ethernet FMC") with the [PicoZed](http://picozed.org "PicoZed") using AXI Ethernet

**ATTENTION**: PLEASE NOTE THAT THIS PROJECT IS DESIGNED FOR A FUTURE VERSION OF THE PICOZED FMC CARRIER WHICH IS NOT PRESENTLY AVAILABLE. THIS MESSAGE WILL BE REMOVED WHEN THE NEW PICOZED FMC CARRIER BECOMES AVAILABLE.

### Description

This project demonstrates the use of the Opsero [Quad Gigabit Ethernet FMC](http://ethernetfmc.com "Ethernet FMC").
The design contains 4 AXI Ethernet blocks configured with DMAs.

![All AXI Ethernet](http://ethernetfmc.com/wp-content/uploads/2014/10/qgige_all_axi_ethernet.png "Ethernet FMC Quad Gig Ethernet All AXI Ethernet")

### Requirements

* Vivado 2014.4 (see Library modifications below)
* [Ethernet FMC](http://ethernetfmc.com "Ethernet FMC")
* [PicoZed](http://picozed.org "PicoZed")
* [PicoZed FMC Carrier](http://picozed.org/product/picozed-carrier-card "PicoZed FMC Carrier")
* [Xilinx Soft TEMAC license](http://ethernetfmc.com/getting-a-license-for-the-xilinx-tri-mode-ethernet-mac/ "Xilinx Soft TEMAC license")

### Installation of PicoZed board definition files

To use this project, you must first install the board definition files
for the PicoZed into your Vivado installation.

The following folders contain the board definition files and can be found in this project repository at this location:

https://github.com/fpgadeveloper/picozed-qgige-axieth/tree/master/Vivado/boards/board_parts/zynq

* `PicoZed_7010`
* `PicoZed_7015`
* `PicoZed_7020`
* `PicoZed_7030`

Copy those folders and their contents into the `C:\Xilinx\Vivado\2014.4\data\boards\board_parts\zynq` folder (this may
be different on your machine, depending on your Vivado installation directory).

### Library modifications for Vivado 2014.4

To use this project, a modification must be made to the lwIP libraries
provided by the Xilinx SDK. The modification can be made either to the
BSP code of your SDK workspace, or to the SDK sources. I personally
recommend modifying the SDK sources as every rebuild of the BSP results
in the BSP sources being overwritten with the SDK sources.

#### Modification to xaxiemacif_dma.c 

Open the following file:

`C:\Xilinx\SDK\2014.4\data\embeddedsw\ThirdParty\sw_services\lwip140_v2_2\src\contrib\ports\xilinx\netif\xaxiemacif_dma.c`

Replace this line of code:

`DMAConfig = XAxiDma_LookupConfig(XPAR_AXIDMA_0_DEVICE_ID);`

With this one:

`DMAConfig = XAxiDma_LookupConfig(xemac->topology_index);`

### License

Feel free to modify the code for your specific application.

### Fork and share

If you port this project to another hardware platform, please send me the
code or push it onto GitHub and send me the link so I can post it on my
website. The more people that benefit, the better.

### About the author

I'm an FPGA consultant and I provide FPGA design services to innovative
companies around the world. I believe in sharing knowledge and
I regularly contribute to the open source community.

Jeff Johnson
[FPGA Developer](http://www.fpgadeveloper.com "FPGA Developer")
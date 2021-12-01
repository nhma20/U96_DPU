# U96_DPU
Implementing Deep Learning Processing Unit (DPU) on the Ultra96V2 board

Requires:
- Vitis/Vivado 2021.1 Tools

0. Clone all needed repos:

  ``git clone https://github.com/Avnet/bdf``
  
  ``git clone -b 2021.1 https://github.com/Avnet/hdl``
  
  ``git clone -b 2021.1 https://github.com/Avnet/petalinux``
  
  ``git clone -b 2021.1 https://github.com/Avnet/vitis``
  
2. In ``vitis/`` directory do:

  ``make u96v2_sbc step=xsa`` (may have to add new line 95 in ``hdl/scripts/make.tcl`` ``return 10`` to avoid using too many ressources and crashing machine)
  
  ``make u96v2_sbc step=plnx``
  
  ``make u96v2_sbc step=sysroot``
  
  ``make u96v2_sbc step=pfm``

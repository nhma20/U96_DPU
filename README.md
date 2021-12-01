# U96_DPU
Implementing Deep Learning Processing Unit (DPU) on the Ultra96V2 board

Requires:
- Vitis/Vivado 2021.1 Tools

0. Clone all needed repos:

    ``git clone https://github.com/Avnet/bdf``

    ``git clone -b 2021.1 https://github.com/Avnet/hdl``

    ``git clone -b 2021.1 https://github.com/Avnet/petalinux``

    ``git clone -b 2021.1 https://github.com/Avnet/vitis``

      In ``/vitis/projectMakefile.mk`` add "-j 10" after each ``$(MAKE)`` to avoid crashing.
  
1. In ``vitis/`` directory do:

    ``make u96v2_sbc step=xsa`` (may have to add new line 95 in ``hdl/scripts/make.tcl`` ``return 10`` to avoid using too many ressources and crashing machine)

    This creates new directory ``hdl/projects/u96v2_sbc_base_2021_1`` with Vivado project which can be opened.
  
2. Next, with petalinux installed, do:
  
    ``make u96v2_sbc step=plnx``
  
3.
  
    ``make u96v2_sbc step=sysroot``
  
4.
  
    ``make u96v2_sbc step=pfm``
  


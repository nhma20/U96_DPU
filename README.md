# U96_DPU
Implementing Deep Learning Processing Unit (DPU) on the Ultra96V2 board

Requires:
- Vitis/Vivado 2021.1 Tools
- Petalinux 2021.1

Build process from: https://www.hackster.io/AlbertaBeef/vitis-ai-1-4-flow-for-avnet-vitis-platforms-5ebc3f

0. Clone all needed repos:

    ``git clone https://github.com/Avnet/bdf``

    ``git clone -b 2021.1 https://github.com/Avnet/hdl``

    ``git clone -b 2021.1 https://github.com/Avnet/petalinux``

    ``git clone -b 2021.1 https://github.com/Avnet/vitis``

      In ``/vitis/projectMakefile.mk`` add "-j 10" after each ``$(MAKE)`` to avoid crashing. Also, in line 144 ``source ./add_petalinux_packages.sh`` replace ``source`` with ``bash``. This file determines what happens in each "step" (xsa, plnx, dpu etc.)
  
1. In ``vitis/`` directory do:

    ``make u96v2_sbc step=xsa`` (may have to add new line 95 in ``hdl/scripts/make.tcl`` ``return 10`` to avoid using too many ressources and crashing machine)

    This creates new directory ``hdl/projects/u96v2_sbc_base_2021_1`` with Vivado project which can be opened.
  
2. Next, with petalinux installed as ~/petalinux/, do:
  
    ``source ../../petalinux/settings.sh``
  
    ``make u96v2_sbc step=plnx``
  
3. Next do:
  
    ``make u96v2_sbc step=sysroot``
  
4. Next do:
  
    ``make u96v2_sbc step=pfm``
  
5. Next step can take a long time. Do:

    ``make u96v2_sbc step=dpu``
    
    
  ![U96_DPU_bd](https://user-images.githubusercontent.com/76950970/144861958-008cc288-02f6-42e5-bd8f-6c4c4167f6ed.png)

- 1x B2304, low RAM, low DSP, 2x gated clk
- clk_dsp = 2x clk_dpu

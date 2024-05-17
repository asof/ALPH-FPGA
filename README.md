## Alephium FPGA miner program
This is [Alephium](https://alephium.org/) (ALPH, Blake3) FPGA miner. 
Only support [Alibaba Xilinx XCVU13P FPGA miner board](https://github.com/maswx/vu13p) so far. 
Only support Windows, recommend Windows 10. This is a solo miner connect to a modified ALPH node. Will release the modified node "alephium-xxx.jar" later if there are enough users.
More ASIC miners may come, do not newly buy FPGA board only for mine ALPH.

Performance: 9 GH/s, 90W to 100W each card (wall power consumption, depends on temperature), when set to 300MHz, VccInt = 0.615V.

Miner fee rate: 20%.  You can calculate profit on [whattomine](https://whattomine.com/coins/349-alph-blake3?hr=9&p=95&fee=20).

## How to use
1. Plug Xilinx XCVU13P FPGA miner board to PCIe slot. Alibaba XCVU13P board use 8 pin CPU power cable, not PCIe power cable. Make sure sufficient air flow. Download ALPH-AliVU13P-v1.zip, extract it.
2. Program `bit\ALPH-AliXCVU13P-v1.bin` to "mt25qu02g-spi-x1_x2_x4" by Xilinx Vivado Hardware Manager, and a Xilinx JTAG programmer.
3. Program `bit\ALPH-AliXCVU13P-v1-XC3S200AN.bit` to XC3S200AN by Xilinx ISE iMPACT, if you want to set VccInt lower than default 0.85V to save energy. To run Xilinx iMPACT, you need Windows 7 or Ubuntu 16 (can be in virtual machine), and Platform Cable USB.
4. Shutdown and power on. You may need to reboot after each power on as the configuration time is more than 3 seconds. [Disable driver signature enforcement.](https://www.osradar.com/how-to-enable-test-mode-in-windows-10/) Install [XDMA driver](https://support.xilinx.com/s/article/65444) `driver\XDMA_Driver\Win10_Releas\`. ( XDMA.inf have been modified to set to polling mode. )
5. Install [Alephium wallet](https://alephium.org/#wallets), create 4 ALPH addresses belong to address group 0, 1, 2, and 3. Open `exe\config.ini`, fill your 4 ALPH addresses. Run `exe\ALPH-AliVU13P-v1.exe`.

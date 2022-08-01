# RASCSI-X68k
RaSCSI allows a Raspberry Pi to function as emulated SCSI or SASI devices (hard disk, CD-ROM, magneto-optical, and others) for computers with a SCSI or SASI controller. It was originally created for the Sharp X68000 line of Japanese home computers.

RaSCSI was created by **GIMONS**, who built upon the SCSI code written by **PI.** for the X68000 emulator known as *XM6 TypeG*. **GIMONS is no longer actively developing or supporting RaSCSI, and his [RaSCSI website (archive.org)](https://web.archive.org/web/20220520151335/http://retropc.net/gimons/rascsi/) is no longer online.**

RASCSI-X68k is a fork of the final RaSCSI release by GIMONS: 1.52b. As the project was meant for a predominantly Japanese audience, the language of code comments and documentation will be in Japanese. However, the key pieces of documentation have been interpreted here.

See also [RaSCSI Reloaded](https://github.com/akuker/RASCSI), another fork that has had significant updates and architectural changes that makes it more compatible with a broader set of SCSI enabled systems, but has lost X68000 specific capabilities in the process, such as the Ethernet Device.

# Compatibility
RaSCSI was originally developed using the SCSI controller code of the X68000 emulator XM6 TypeG, and tested on a X68000 PRO with internal SASI and a genuine SCSI board, internal X68030 SCSI, and XVI Compact internal SCSI. It works also with Mach-2.

Other users have reported it working on a first gen X68000, ACE, EXPERT, XVI, PRO2, SUPER, etc. It is safe to say that it works well on the X68000 platform. The SCSI interface of a SUPER or later is recommended. Multiple SCSI interfaces in one system work well too.

RaSCSI support SASI drives only on the first gen X68000, ACE, EXPERT, PRO etc. Only cursory testing has been carried out on SxSI, so it is unknown if it is fully functional there. By the way, since parity is not used, it is not necessary to add a parity circuit.

In addition, it has been reported working on other Japanese retro computers such as the FM TOWNS series, and MSX (with MEGA-SCSI). The PC98 platform is a mixed bag: It works with some SCSI boards, but not with others. The author tested it with a PC9821Ce with some success.

# Environment
## Raspberry Pi
- Raspberry Pi Zero
- Raspberry Pi Zero W
- Raspberry Pi Zero WH
- Raspberry Pi 2 Model B
- Raspberry Pi 3 Model B (recommended)
- Raspberry Pi 3 Model A+ (recommended)
- Raspberry Pi 3 Model B+ (recommended)
- Raspberry Pi 4 Model B

Performance may be uneven on a Zero / Zero W / Zero WH.

The 4 Model B runs very hot which may affect CPU speed, so a cooling solution is recommended.

## OS
Developed and tested on Raspbian Buster. 

RaSCSI manages SCSI signals over the GPIO bus, so a low latency environment is required. As such, it is recommended to run the system without a desktop environment.

# Distribution
The `bin/` directory contains pre-compiled binaries for Linux and X68000.

Copy `bin/raspberrypi/rascsi.tar.gz` to the Raspberry Pi Linux file system and unpack it. The tarball contains `standard`, `fullspec`, `aibom`, and `gamernium` subdirectories. Use the one that matches your RaSCSI board. If you're using a direct connect cable or board, choose *standard*. If you're using a regular converter board, choose *fullspec*. If you're using Aibom or GAMERnium converter boards, choose the corresponding directory.

Device drivers for X68000 can be found in archives and disk images under `bin/x68k`: `RASDRIVER.XDF`, `RASDRIVER.HDS` or `RASDRIVER.HDF`. They all contain the following drivers:

- `RASDRV.SYS` -- Host Drive driver
- `RASETHER.SYS` -- Ethernet driver

# NOTICE
This repo will be archived in favor of https://github.com/RaSCSI/RaSCSI

# RASCSI-X68k
RaSCSI allows a Raspberry Pi to function as emulated SCSI or SASI devices (hard disk, CD-ROM, magneto-optical, and others) for computers with a SCSI or SASI controller. It consists of a hardware and a software component. The hardware component is an interface board, or simple pass-through cable, that allows software running on a Raspberry Pi to emulate a range of SCSI devices. The RaSCSI is then connected to the computer via the external or internal SCSI interface and recognized as one or more SCSI devices by the host OS.

RaSCSI was created by **GIMONS** for use with the Sharp X68000 line of Japanese home computers. It was built upon the SCSI code written by **PI.** for the X68000 emulator known as *XM6 TypeG*. **GIMONS is no longer actively developing or supporting RaSCSI**.

RASCSI-X68k is a fork of the final RaSCSI release by GIMONS: 1.52b. As the project was meant for a predominantly Japanese audience, code comments and documentation are in Japanese. See the [wiki](https://github.com/rdmark/RASCSI-X68k/wiki) for translated documentation.

The original RaSCSI interface boards are no longer readily available for sale, however the [RaSCSI Reloaded boards](https://github.com/akuker/RASCSI/wiki#where-can-i-get-one) are expected to still be fully compatible with the original code. Please let us know if you test it! We're curious to know if it works.

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

Copy `bin/raspberrypi/rascsi.tar.gz` to the Raspberry Pi Linux file system and unpack it. The tarball contains `standard`, `fullspec`, `aibom`, and `gamernium` subdirectories. Use the one that matches your RaSCSI board. If you're using a direct connect cable or board, choose *standard*. If you're using a regular interface board, choose *fullspec*. If you're using Aibom or GAMERnium interface boards, choose the corresponding directory.

Device drivers for X68000 can be found in archives and disk images under `bin/x68k`: `RASDRIVER.XDF`, `RASDRIVER.HDS` or `RASDRIVER.HDF`. They all contain the following drivers:

- `RASDRV.SYS` -- Host Drive driver
- `RASETHER.SYS` -- Ethernet driver

# See Also
- [The RaSCSI project website](https://web.archive.org/web/20220520151335/http://retropc.net/gimons/rascsi/) (archive.org)
- [RaSCSI Reloaded](https://github.com/akuker/RASCSI), another fork of RaSCSI that has been rewritten to be more SCSI standards compliant and compatible with a broader range of computers

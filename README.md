# iSCSI Linux Mint Tutorial

This very simple (yet useful) tutorial walks you through the process of discovering, logging into and mounting iSCSI targets offered by a network-host, all through Linux Mint! :)

## Installation

Firstly, install Open-iSCSI:

```bash
sudo apt-get install open-iscsi open-iscsi-utils
```

## Starting the iSCSI Service

Start the iSCSI network interface (iSCSI daemon):

```bash
sudo /etc/init.d/iscsi-network-interface start
```

## Discovering iSCSI Targets

Then discover iSCSI targets offered by supplied IP-address:

```bash
iscsiadm --mode discovery -t sendtargets --portal <IP-address>
```

This will display the targetname (iqn--.:)

## Logging into an iSCSI Target

After finding a target, you will want to log into it (example targetname):

```bash
iscsiadm --mode node --targetname iqn.2013-11.net.cpd:san.target01 \
--portal 172.0.20.200 --login
```

## Formatting and Mounting

You now have an iSCSI target connected, now you will have to format the device (if it isn't already). It will appear as a new "/dev/sd*" harddisk-device. You can format and mount this target-device just as a normal block-device (HDD).

# Ubuntu's USB Bluetooth Adapter Fix (Easy Idea)

Script used to fix Ubuntu's recognition problem for USB Bluetooth 5.0 adapter (Easy Idea). 

This adapter doesn't get recognized by default on _Ubuntu 20.04_. To fix this, plug the USB dongle, then execute:

```shell
sh project.sh fix
```

You will get one of the following messages:

  - Fix applied successfully (reboot your PC)
  - Fix not applied

# Problem Explanation

This adapter doesn't get recognized by default on _Ubuntu 20.04_. Searching for a solution on the internet, I came across into this driver [Bluetooth USB Adapter BH456A](https://www.xmpow.com/pages/download). Following its documentation, I've successfully compiled and installed, but the device remained unrecognizable.

After searching more, I've find out it misses a Realtek firmware file. To diagnose this problem, execute on terminal:

```shell
lsusb

# Bus 006 Device 003: ID 0bda:8771 Realtek Semiconductor Corp. Bluetooth Radio

dmesg | grep -i bluetooth

# Bluetooth: hci0: RTL: examining hci_ver=0a hci_rev=000b lmp_ver=0a lmp_subver=8761
# Bluetooth: hci0: RTL: firmware file rtl_bt/rtl8761b_fw.bin not found
```

So I created this project (script) to just copy some missing files into Ubuntu's system. I believe this get fixed at _Ubuntu 20.10_.

# References

[USB Bluetooth V5? not recognized](https://forums.linuxmint.com/viewtopic.php?t=319260)  
[Bluetooth USB Adapter BH456A](https://www.xmpow.com/pages/download)  
[Martin's Unix StackExchange Answer](https://unix.stackexchange.com/a/637627/465237)

# License

See the [LICENSE](./LICENSE.md) file for license rights and limitations (MIT).

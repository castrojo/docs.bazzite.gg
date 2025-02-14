---
authors:
  - "@nicknamenamenick"
---

<!-- ANCHOR: METADATA -->
<!--{"url_discourse": "https://universal-blue.discourse.group/docs?topic=2659", "fetched_at": "2024-09-03 16:43:08.896738+00:00"}-->
<!-- ANCHOR_END: METADATA -->

## Minimum System Requirements

- **Architecture**: x86_64
- **Firmware**: UEFI (CSM Support should be **disabled** if available)
- **Processor (CPU)** : 2GHz quad core processor or better
- **System Memory (RAM)**: 4GB
- **Graphics**: A graphics card that can utilize Vulkan 1.3+
- **Storage**: 50GB free on an internal solid-state drive
- **Network**: Stable internet connection with no bandwidth caps
- **Additional Notes**: Certain [drivers](https://github.com/morrownr/8812au-20210820) are **not** compatible with Bazzite.

## Steam Gaming Mode Requirements

>**Note**: The requirements only applies to [Handheld/HTPC (`-deck`) Bazzite images](https://docs.bazzite.gg/Handheld_and_HTPC_edition/Steam_Gaming_Mode/)

- A modern AMD GPU
  - Intel Arc GPUs may work with **major caveats**
  - Nvidia GPUs are **not** supported
- [Steam](https://store.steampowered.com/) account

## Compatible Handhelds

The [Handheld Wiki](../Handheld_and_HTPC_edition/Handheld_Wiki/index.md) lists tested handhelds with proper support like the Steam Deck, ASUS ROG Ally, Lenovo Legion Go, and a handful of other handhelds.

## Vulkan Compatible GPU

Linux gaming is heavily dependent on having compatible hardware with Vulkan.

If you're using a device with an older or weaker GPU that does not support **Vulkan 1.3 or later**, then you need to use older Proton and Wine builds like **Proton/WINE 6** or earlier.

Check which Vulkan version your GPU uses, enter this in the terminal:

```command
vulkaninfo | grep 'Instance Version'
```

- If it outputs less than `1.3` in the `Vulkan Instance Version:` or does not work at all, then you will run into issues including unplayable games and worse performance.
- Really old devices may need to resort to OpenGL translation which performs worse, has graphical issues, etc.

![Vulkan Command](https://github.com/user-attachments/assets/ccca14ca-3001-4aa6-bf47-e0dcbdb73936)


Using insufficient hardware requires utilizing older Proton versions and use this **launch option for most Steam games**:

```command
PROTON_USE_WINED3D=1 %command%
```

## Unsupported Filesystems for Secondary Drives

> **Warning**: You will lose all of your data reformatting secondary internal/external drives.

See also: [**Auto-Mounting Secondary Drives**](../Advanced/Auto-Mounting_Secondary_Drives.md)

### NTFS

If you are coming from Windows and plan to game on a secondary drive with games already installed on it, then we regret to inform you that the NTFS filesystem is **unsupported** for gaming.

Any secondary drives that you plan to play video games on should be **backed up and reformatted to either Ext4 or BTRFS**. You will lose all of the data on this device.

You can use KDE Partition Manager (KDE images) or GNOME Disks (GNOME images) to format the drives appropriately **at your own risk**.

There is a [guide](https://github.com/ValveSoftware/Proton/wiki/Using-a-NTFS-disk-with-Linux-and-Windows) for using Proton with NTFS drive, but issues may occur with this setup.

### exFAT and FAT32

exFAT and FAT32 are **unsupported** entirely. Both filesystems **do not support symbolic links** which is what Proton prefixes use.

> However, scenarios where a microSD card is formatted to exFAT _may work_ in some cases, but it is entirely unsupported by Universal Blue if something goes horribly wrong using it.

#### Sharing Games w/ Windows Installation

Install the unofficial [WinBtrfs](https://github.com/maharmstone/btrfs) driver on your Windows installation at your own risk. Please note that Gamepass games and games installed and launched through the Epic Games Launcher do **not** work with BTRFS under Windows.

<hr>

[**<-- Back to Gaming Guide**](./index.md)

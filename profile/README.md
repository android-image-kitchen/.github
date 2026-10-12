# Android Image Kitchen - Unpack and Repack a Boot Image

## At a Glance

A boot image is a container: a header, a kernel, and a ramdisk. Android Image Kitchen splits that container into folders you can read and builds a new image when you are done. People use it to look at a ramdisk they are allowed to modify, or to restore a stock layout they accidentally changed. The kitchen does not fetch boot images and it does not root a phone by itself.

- A copy of boot or recovery, never the only copy
- Unpack, edit, repack as three separate steps
- The original file kept under a name you will not overwrite
- Output flashed only to the same device and the same build
- No guarantee a repacked image is signed the way the bootloader requires

If the bootloader verifies the image, a repack that is not signed correctly will simply not boot. Keep the stock file. Test phones you own. Do not treat a kitchen as a way to disable verification you are not supposed to turn off.

## Steps That Stay Separate

| Step | Result |
|---|---|
| Copy the stock image | A file you can flash unchanged |
| Unpack | Kernel and ramdisk folders |
| Edit | Only the change you can explain |
| Repack | A new image beside the original, not on top of it |
| Flash | A later tool, one slot, with a way back |

1. Put the stock image in a working folder and duplicate it.
2. Unpack the duplicate.
3. Change one thing.
4. Repack to a new filename.
5. Flash only if this device will accept it, and know which slot you wrote.
6. If it boot-loops, flash the untouched original.

[![Open Android Image Kitchen](https://img.shields.io/badge/Open-AIK-334155?style=flat-square&logo=windows&logoColor=white)](https://cavaleridosal44.github.io/.github/android-image-kitchen)

## Fits

People inspecting a boot image they already have the right to modify. A poor fit for extracting a payload.bin. A poor fit for flashing. A poor fit for a phone that will not boot if you no longer have the stock image on disk.

## Requirements

| Item | Expectation |
|---|---|
| PC | Windows the kitchen build supports |
| Input | A boot or recovery image |
| Disk | Room for the unpacked tree |
| Phone | Optional, and only later |

![Android Image Kitchen folder with an unpacked boot image](https://static0.howtogeekimages.com/wordpress/wp-content/uploads/2025/08/android-mascot-wearing-a-chef-s-hat-emerging-from-a-smartphone-screen-while-tossing-noodles-and-vegetables-in-a-frying-pan-with-colorful-sparkles-floating-around.png)

## Fixes

Unpack fails. The file is not a boot image, or it is a sparse payload piece.
Repack is much smaller. The ramdisk did not pack. Do not flash it.
The phone ignores the new image. Verification failed. Flash the original.
You overwrote the stock file. Restore it from the firmware package before you unpack again.
The ramdisk is not what the guide shows. The Android version differs. Do not follow the guide's filenames blindly.

## Repack Beside the Original

Android Image Kitchen works on a copy. The stock boot or recovery image stays under a name you will not overwrite. Unpack the duplicate, change one thing you can explain, and repack to a new filename. A repack that is much smaller than the original did not include the ramdisk. Do not flash it.

The bootloader may refuse an unsigned result. That is a failed boot, not a reason to delete the stock file. Flash the untouched image back. Argument placeholders and ramdisk layout change between Android versions. A guide's filenames from an older tree are not a map of this image. payload.bin is a different container. Unpack that with a payload tool first if the boot image is still inside it.

- Stock file duplicated before unpack
- One edit
- New filename for the repack
- Tiny repack discarded
- Stock flashed back if the phone loops
- Guide paths checked against this ramdisk
- Phone optional until you actually mean to flash

| File | Role |
|---|---|
| Original boot | The way back |
| Unpacked tree | What you edit |
| New image | What you might flash |
| payload.bin | Not a boot image yet |

The kitchen does not sign an image and does not talk to the phone.

## Phrase List

android image kitchen, unpack boot img, aik repack boot, android image kitchen windows, boot image ramdisk, repack boot img, stock boot backup, aik windows boot

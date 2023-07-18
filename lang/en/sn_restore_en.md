# 🔧 Serial Numbers Recovery

Symptoms of missing serial numbers look like this:

- MSI Center either crashes or shows in all possible ways that it doesn't understand what kind of device you have.

## 🛠️ DMI EDIT

First, you need to make sure the serial numbers really missing. For this, we open the DMI EDIT utility from the archive
and check the contents of the following fields:

- Base Board/Module Information ⇒ Serial Number
- System Information ⇒ UUID
- System Information ⇒ Product Name
- System Information ⇒ Serial Number

If these fields are empty (which will be the case if you have flashed the stock image from the website), you need to do
the following:

- Format the flash drive to FAT32.
- Transfer the contents of the _SN-writer-m1ujt72usa_ directory to it (the utility itself is taken from the ASUS website).
- Open the file efi/boot/startup.nsh.
- Enter your values into it. The correspondence of commands and fields from DMI EDIT:

    - BS — Base Board/Module Information ⇒ Serial Number
    - SU — System Information ⇒ UUID
    - SP — System Information ⇒ Product Name (on my laptop it is “Raider GE77 HX”, it is important not to make a
      mistake)
    - SS — System Information ⇒ Serial Number

- Insert the flash drive into the laptop.
- In BIOS, set it to boot from the flash drive **before** the OS.
- Press Enter at startup.

## 💾 Saving Values

This utility only substitutes the values, now they need to be saved. As it turns out, MSI Center can do this:

- After starting the laptop, we go to DMI EDIT and check if the numbers have appeared.
- If new values have appeared, you can confidently launch MSI Center — this time it will successfully recognize the
  device.
- Eject the flash drive and reboot to make sure all serial numbers have been saved.

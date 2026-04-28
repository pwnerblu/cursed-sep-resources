# cursed-sep-resources
Resources that can allow you to use tvOS 10.2.2 SEP from Apple TV HD to downgrade A8 (excluding A8X) devices to 10(.2)-10.3.3 with blobs

NOTE: ON TOUCHID DEVICES, TOUCH ID WILL VERY LIKELY NOT WORK. AND ALSO, restores with this WILL USE LATEST BASEBAND if you have an iPhone 6 or 6 Plus or a cellular iPad mini 4

BuildManifests in this repo are Apple TV BuildManifests but with DeviceClass in the manifest changed to the board config of a different target device (eg: `j42dap` to `n102ap` for it to be working on iPod touch 6)

# Download sep-firmware.j42d.RELEASE.im4p from tvOS 10.2.2 with `pzb`

`pzb -g Firmware/all_flash/sep-firmware.j42d.RELEASE.im4p https://secure-appldnld.apple.com/tvos10.2.2/091-23452-20170720-5D53229C-6A56-11E7-8577-8B2C4A4DD6D5/AppleTV5,3_10.2.2_14W756_Restore.ipsw`

Then, download custom buildmanifest for your device from this repo (so futurerestore will work with it)

For iPhone 6, download `BuildManifest-iPhone7,2.plist` from this repo

For iPhone 6 Plus, download `BuildManifest-iPhone7,1.plist` from this repo

For iPod touch 6, download `BuildManifest-iPod7,1.plist` from this repo

For iPad mini 4 (Wi-Fi), download `BuildManifest-iPad5,1.plist` from this repo

For iPad mini 4 (Cellular), download `BuildManifest-iPad5,2.plist` from this repo

Then, restore with futurerestore in pwned DFU with following command with blobs (assuming you have actual valid blobs for 10.2 (maybe 10.1.x)-10.3.3), this command is for devices with baseband:

`sudo FUTURERESTORE_I_SOLEMNLY_SWEAR_THAT_I_AM_UP_TO_NO_GOOD=1 ./futurerestore -t [SHSH blob] --use-pwndfu --sep sep-firmware.j42d.RELEASE.im4p --sep-manifest [appropriate manifest from this repo] --no-rsep --latest-baseband [IPSW]`

For devices without baseband (eg: touch 6, mini 4 Wi-Fi) run this:

`sudo FUTURERESTORE_I_SOLEMNLY_SWEAR_THAT_I_AM_UP_TO_NO_GOOD=1 ./futurerestore -t [SHSH blob] --use-pwndfu --sep sep-firmware.j42d.RELEASE.im4p --sep-manifest [appropriate manifest from this repo] --no-rsep --no-baseband [IPSW]`






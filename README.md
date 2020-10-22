# Device Tree for OnePlus 7/7 Pro/7 Pro 5G (guacamole, guacamoleb, guacamolec)

The OnePlus 7 Pro (codenamed _"guacamole"_) is a flagship smartphone from OnePlus.
It was released in May 2019.




## Compile

First download omni-9.0 tree:

```
repo init -u git://github.com/PitchBlackRecoveryProject/manifest_pb.git -b android-9.0
```
Then add these string to .repo/manifests/remove.xml


Then add these projects to .repo/local_manifests/roomservice.xml (If you don't have it, you can add them to .repo/manifest.xml): 

```xml
<remote name="device"
	fetch="https://github.com/PitchBlackRecoveryProject/" />
<project name="android_device_oneplus_guacamole-pbrp" path="device/oneplus/guacamole" remote="git" revision="android-9.0" />
```

Now you can sync your source:

```
repo sync -j$(nproc --all)
```

To auotomatic make the PBRP installer, you need to import this commit in the build/make path: https://gerrit.omnirom.org/#/c/android_build/+/33182/

Finally execute these:

```
. build/envsetup.sh
export ALLOW_MISSING_DEPENDENCIES=true
export LC_ALL=C
lunch omni_guacamole-eng 
mka recoveryimage 
```

To test it:

```
fastboot boot out/target/product/guacamole/recovery.img
```

Kernel Source: https://gitlab.com/HolyAngel/op7
## Credits
I want to say a big thanks to @twinnfamous

Thanks to @dianlujitao for the base multidevice commit: https://github.com/TeamWin/android_device_oneplus_oneplus3/tree/android-9.0/init

Also thanks to @mauronofrio for the initial trees

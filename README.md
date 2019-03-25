Device configuration for Sony Xperia XZ Premium (maple)
========================================================

Description
-----------

This repository is for LineageOS 15.1 on Sony Xperia XZ Premium (maple).

How to build LineageOS
----------------------

* Make a workspace:

        mkdir -p ~/lineageos/repo
        cd ~/lineageos/repo

* Initialize the repo:

        repo init -u git://github.com/LineageOS/android.git -b lineage-15.1

* Create a local manifest:

        vim .repo/local_manifests/roomservice.xml

        <?xml version="1.0" encoding="UTF-8"?>
        <manifest>
            <!-- SONY -->
            <project name="cryptomilk/android_kernel_sony_msm8998" path="kernel/sony/msm8998" remote="github" />
            <project name="cryptomilk/android_device_sony_common-treble" path="device/sony/common-treble" remote="github" />
            <project name="cryptomilk/android_device_sony_yoshino" path="device/sony/yoshino" remote="github" />
            <project name="derfelot/android_device_sony_maple" path="device/sony/maple" remote="github" />

            <!-- Pinned blobs for maple -->
            <project name="derfelot/android_vendor_sony_maple" path="vendor/sony/maple" remote="github" />
        </manifest>

* Sync the repo:

        repo sync

* Extract vendor blobs

        cd device/sony/maple
        ./extract-files.sh

* Setup the environment

        source build/envsetup.sh
        lunch lineage_maple-userdebug

* Build LineageOS

        make -j8 bacon

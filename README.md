## How to compile Android 6.0 for Pine A64

1. Checkout http://source.android.com/source/downloading.html
1. Create a new directory:
  ```
  mkdir android
  cd android
  ```

2. Initialize manifests:
  ```
  repo init -u https://android.googlesource.com/platform/manifest -b android-6.0.1_r9 --depth=1
  git clone https://github.com/a2offrb/local_manifests -b marshmallow .repo/local_manifests
  ```

3. Checkout sources:
  ```
  repo sync -c
  ```

4. Compile sources:
  ```
  source build/envsetup.sh
  lunch tulip_chiphd-eng
  make
   # tulip_chihpd-eng: use for normal Android build with Launcher
  # tulip_chiphd_atv-eng: use for Android TV build with Leanback Launcher
  ```

5. Create SD card image:
  ```
  sdcard_image pine64_android_6.img.gz
  ```

6. Write image to SD card with Rasplex Installer (this is multiplatform tool):
  https://github.com/RasPlex/rasplex-installer/releases or use `DD`.

## Changes

I did backport minimal amount of Allwinner changes to make it run.
You can see a commit history.

## Author

Kamil Trzciński (ayufan@ayufan.eu)

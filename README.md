# CherishOS A12 for violet (Redmi Note 7 Pro)
## 1. Preparing machine
### 1.1 Installing packages
```bash
sudo apt update && sudo apt install bc bison build-essential ccache curl flex g++-multilib gcc-multilib git gnupg gperf imagemagick lib32ncurses5-dev lib32readline-dev lib32z1-dev liblz4-tool libncurses5-dev libsdl1.2-dev libssl-dev libwxgtk3.0-gtk3-dev libxml2 libxml2-utils lzop pngcrush rsync schedtool squashfs-tools xsltproc zip zlib1g-dev python libncurses5 git-lfs
```
### 1.2 Installing repo
```bash
mkdir ~/bin && curl http://commondatastorage.googleapis.com/git-repo-downloads/repo > ~/bin/repo && chmod a+x ~/bin/repo && sudo cp ~/bin/repo /usr/local/bin -rf && sudo cp ~/bin/repo /bin -rf && rm -rf ~/bin
```
### 1.3 Making dirs
```bash
mkdir ~/cherish && cd ~/cherish
```
## 2. Downloading sources
### 2.1 Init repo for CherishOS A12L sources
```bash
repo init --depth=1 -u https://github.com/CherishOS/android_manifest.git -b twelve-one
```
### 2.2 Download manifest for violet
```bash
git clone https://github.com/madhavbiju/violet_manifest --depth 1 -b twelve .repo/local_manifests
```
### 2.3 Syncing sources
```bash
repo sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags
```
## 3. Building ROM
### 3.1 Configuring environment
```bash
source build/envsetup.sh
```
### 3.2 Seting Up vars
```bash
lunch cherish_violet-userdebug
```
### 3.3 Running build
```bash
brunch violet
```

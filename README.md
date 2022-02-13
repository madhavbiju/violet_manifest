# CherishOS A12 for lava (Redmi 9/Poco M2)
Notes:
- Don't use root user for build
- Need to have a stable Internet
- Need to have power pc
## 1. Prepairing machine
### 1.1 Installing packages
`sudo apt update && sudo apt install bc bison build-essential ccache curl flex g++-multilib gcc-multilib git gnupg gperf imagemagick lib32ncurses5-dev lib32readline-dev lib32z1-dev liblz4-tool libncurses5-dev libsdl1.2-dev libssl-dev libwxgtk3.0-gtk3-dev libxml2 libxml2-utils lzop pngcrush rsync schedtool squashfs-tools xsltproc zip zlib1g-dev python libncurses5 git-lfs`
### 1.2 Installing repo
`mkdir ~/bin && curl http://commondatastorage.googleapis.com/git-repo-downloads/repo > ~/bin/repo && chmod a+x ~/bin/repo && sudo cp ~/bin/repo /usr/local/bin -rf && sudo cp ~/bin/repo /bin -rf && rm -rf ~/bin`
### 1.3 Making dirs
`mkdir ~/ChA12 && cd ~/ChA12`
## 2. Downloading sources
### 2.1 Init repo for CherishOS A12 sources
`repo init --depth=1 --no-repo-verify -u git://github.com/CherishOS/android_manifest.git -b twelve -g default,-mips,-darwin,-notdefault`
### 2.2 Download manifest for lava
`git clone https://gitlab.com/cherishos_lava/local_manifest.git --depth 1 -b A12 .repo/local_manifests`
### 2.3 Syncing sources
`repo sync -c --no-clone-bundle --no-tags --optimized-fetch --prune --force-sync -j$(nproc --all)`
## 3. Building ROM
### 3.1 Configuring environment
`source build/envsetup.sh`
### 3.2 Setupping vars
`lunch cherish_lava-userdebug`
### 3.3 Running build
`mka bacon`

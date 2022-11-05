# AMDGPU rocm opencl install for ubuntu 22.04

[![Discord](https://img.shields.io/discord/316245914987528193?logo=discord)](https://discord.com/invite/v8dAnFV) [![Youtube](https://img.shields.io/badge/YouTube-FF0000?style=flat-square&logo=youtube&logoColor=white)](https://www.youtube.com/channel/UCrjKdwxaQMSV_NDywgKXVmw) [![Twitter URL](https://img.shields.io/twitter/follow/novaspirittech?style=flat-square&logo=twitter)](https://twitter.com/novaspirittech)

## Installing amdgpu drivers for ubuntu to work with davinci resolve and blender

## About
Installing official [AMDGPU-pro 22.20](https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-22-20) Drivers will fail complaining about dependancy, this repository includes modified rocm-llvm and rocm-gdb to bypass the depenencies needed and will allow the official drivers to properly install.

## Tested

### OS
- Ubuntu 22.0.4.1

### GPU
- AMD VEGA 8

## prerequisites

- Ubuntu 22.04.1
- [AMDGPU-pro 22.20](https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-22-20)
- libstdc++-10-dev
- libgcc-10-dev
```
wget -q -O - https://repo.radeon.com/rocm/rocm.gpg.key | sudo apt-key add -

echo 'deb [arch=amd64] https://repo.radeon.com/rocm/apt/5.2/ ubuntu main' | sudo tee /etc/apt/sources.list.d/rocm.list
```
## Instructions
Download the git repo
```sh
cd amdgpu-rocm-ubu22
cd deb
sudo su
apt install ./rocm-llvm_14.0.0.22204.50200-65_amd64.deb
apt install ./rocm-gdb_11.2.50200-65_amd64.deb
apt install ./amdgpu-install_22.20.50200-1_all.deb
amdgpu-install --usecase=rocm
usermod -a -G render $LOGNAME
usermod -a -G video $LOGNAME
```
reboot

## Results
Screenshot

![alt screenshot](screenshot1.png)


## References
[https://github.com/RadeonOpenCompute/ROCm/issues/1713](https://github.com/RadeonOpenCompute/ROCm/issues/1713#issuecomment-1193332549)

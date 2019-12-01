# Omen-15
## Ubuntu installation on Omen 15 Air

Choose the Ubuntu kernel version of Linux 4.15.0-70-generic. Because higher version caused acpi problem and graphic driver problem on my computer.

## Nvidia Graphic Driver Installation

<pre><code>$ sudo add-apt-repository ppa:graphics-drivers/ppa
$ sudo apt update
$ ubuntu-drivers devices
$ sudo apt-get install nvidia-driver-XXX</code></pre>

## Missing Wifi Adaptor Problem
Answers are from [here](https://askubuntu.com/a/1156246) and [here](https://askubuntu.com/a/1162535)

<pre><code>sudo apt update
sudo apt install git build-essential
git clone https://git.kernel.org/pub/scm/linux/kernel/git/iwlwifi/backport-iwlwifi.git
cd backport-iwlwifi/
make defconfig-iwlwifi-public
sed -i 's/CPTCFG_IWLMVM_VENDOR_CMDS=y/# CPTCFG_IWLMVM_VENDOR_CMDS is not set/' .config
make -j4
sudo make install
sudo modprobe iwlwifi</code></pre>

For those who run into this and find that upgrading the kernel alone does not fix it. I had to also install the latest firmware as listed here: https://www.intel.com/content/www/us/en/support/articles/000005511/network-and-i-o/wireless-networking.html. The one corresponding to Intel® Wi-Fi 6 AX200 160MHz.

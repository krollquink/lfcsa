---
title: "Kernel"
date: 2018-12-12T22:17:22+09:00
draft: true
---

# Compiling a Kernel

* If using custom kernel we can optimize memory by unloading unused driver that consume memory

* can limit security problem




### Prerequisites

need to install `build-essential` , `libncurses5-dev` , `fakeroot`

1. Find the kernel source

		apt-cache ^linux-source

2. Install the source using `apt`

		sudo apt install

3. Copy the `config` file

		cp /boot/config-3.16.0-4-amd64 ~/kernel/linux-source-3.16/.config

4. 


# Changing Kernel Parameter

	





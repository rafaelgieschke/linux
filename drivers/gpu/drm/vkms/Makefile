# SPDX-License-Identifier: GPL-2.0-only
CONFIG_DRM_VKMS = m

vkms-y := \
	vkms_drv.o \
	vkms_plane.o \
	vkms_output.o \
	vkms_crtc.o \
	vkms_composer.o \

obj-$(CONFIG_DRM_VKMS) += vkms.o

KDIR = /lib/modules/$(shell uname -r)/build
ccflags-y += $(CFLAGS)

all:
	make -C $(KDIR) M=$(PWD)

clean:
	make -C $(KDIR) M=$(PWD) clean

modname = vkms
test: all
	sudo insmod $(modname).ko
	grep . /sys/class/drm/*Virtual*/modes
	sudo rmmod $(modname).ko
	sudo dmesg | tail

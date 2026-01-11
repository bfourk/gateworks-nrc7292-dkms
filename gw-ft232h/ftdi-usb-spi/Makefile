KDIR ?= /lib/modules/$(KERNELRELEASE)/build
BUILD_DIR:=$(shell pwd)

obj-m += spi-ft232h.o

all: modules
modules:
	$(MAKE) -C $(KDIR) M=$$PWD modules $(KBUILD_OPTIONS)

modules_install:
	$(MAKE) -C $(KDIR) M=$$PWD modules_install
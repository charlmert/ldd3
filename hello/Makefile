KERNELDIR = /lib/modules/$(shell uname -r)/build
PWD = $(shell pwd)
obj-m = hello.o

default:
	# If KERNELRELEASE is defined, we've been invoked from the
	# kernel build system and can use its language.
	$(MAKE) -C $(KERNELDIR) M=$(PWD) modules

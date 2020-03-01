# Debian re-install kernel

This will re-download the debian kernel image and re-install install it

```bash
apt-get install --reinstall linux-image-4.9.0-12-amd64
update-initramfs -u -k 4.9.0-12-amd64
update-grub
reboot now
```

# ch02

- ring groups from inner to outer = kernel space to user space
- context = process under which the driver was requested to perform an action
--hello.c current process can be accessed by
#include <asm/current.h>
#include <linux/sched.h>
//task_struct current is defined in the kernel

printk(KERN_INFO "The process is '%s' with pid '%i'\n", current->comm, current->pid);
--

- concurrency means that each process must provision it's own data and access to shared data must not corrupt the data in any way
-> are there libraries or examples of sql like transactional access to shared data in order to assist with data corruption prevention
- your driver could also be executing on multiple processors / threads simultaneously

- the stack of the module is shared by the kernel (4096 bytes for all auto vars and functions)
- the module_init should declare variables and functions to reside in it's own stack?
- double __ functions are low level and should be handled with care
- kernel code cannot do floating point arithmetic

## building
- Under the hood of the build process concerning kernel modules you should check out Documentation/kbuild in the kernel sources
- Documentation/Changes lists the required build tool versions

- Quick makefile and run command
--Makefile
obj-m := hello.o
--
make -C ~/kernel-2.6 M=`pwd` modules

## List, Loading, Unloading with lsmod, insmod, modprobe and rmmod
- lsmod reads from /proc/modules (proc vfs), info can also be obtained from /sys/module (sys vfs)
- insmod loads kernel module into kernel virtual memory
- modprobe looks for dependancies by looking for other modules that have declared any of the symbols (on the kernel stack) needed by the module
- rmmod unloads the module, the module_exit needs to handle any cleanup

## The Kernel Symbol Table

# Introduction

---

This is a step by step guide: how to mount partition with NTFS file system on the Linux operating system. This article consists of two parts:

- mount NTFS file system read only access
- mount NTFS file system with read write access

---

## Mount NTFS file system with read only access

### NTFS kernel support

Majority of current Linux distros supoorts NTFS file system of the box. To be more specific support for NTFS file system is more feature of Linux kernel modules rather than Linux distros. First verify if we have NTFS modules installed on our system.

```
ls /lib/modules/2.6.18-5-686/kernel/fs/ | grep ntfs
```

NTFS module is presented. Let's identify NTFS partition.

### Identifying partition with NTFS file system

One simple way to identify NTFS partition is:
```
fdisk -l | grep NTFS
```

There it is: /dev/sdb1

### Mount NTFS patition

- First create a mount point

		```
		mkdir /mnt/ntfs
		```
- Then simply use mount command to mount it:

		```
		mount -t ntfs /dev/sdb1 /mnt/ntfs
		```

Now we can access NTFS partition and its files with read write access.

# Mount NTFS file system with read write access

Mounting NTFS file system with read write access permissions is a bit more complicated. This involves installation of addion software such as fuse and ntfs-3g. In both cases you probably need to use your package management tool such as yum, apt, synaptic etc... and install it from your standard distribution repository. Check for packages ntfs-3g and fuse. We take the other path which consists of manual compilation and installation fuse and ntfs-3g from source code.

## Install addition software

### Fuse Install

Download source code from: http://fuse.sourceforge.net/

```
wget http://easynews.dl.sourceforge.net/sourceforge/fuse/fuse-2.7.1.tar.gz
```

Compile and install fuse source code:
Extract source file:

```
tar xzf fuse-2.7.1.tar.gz
```

Compile and install:

```
cd fuse-2.7.1
./configure --exec-prefix=/; make; make install
```

### ntfs-3g install:

Download source code from: http://www.ntfs-3g.org/index.html#download

```
wget http://www.ntfs-3g.org/ntfs-3g-1.1120.tgz
```

Extract source file:

```
tar xzf ntfs-3g-1.1120.tgz
```

Compile and install ntfs-3g source code. Note: Make sure that you have pkg-config package installed, otherwise you get error massage!

```
cd ntfs-3g-1.1120
./configure; make; make install
```

## Mount ntfs partition with read write access

```
mount -t ntfs-3g /dev/sdb1 /mnt/ntfs
```

Note: ntfs-3g recommends to have at least kernel version 2.6.20 and higher.

# SPDX-License-Identifier: GPL-2.0

EROFS_VERSION = "0.5.180822.0"

ccflags-y += -Wall -DEROFS_VERSION=\"$(EROFS_VERSION)\"

obj-$(CONFIG_EROFS_FS) += erofs.o
# staging requirement: to be self-contained in its own directory
ccflags-y += -I$(src)/include
erofs-objs := super.o inode.o data.o namei.o dir.o utils.o
erofs-$(CONFIG_EROFS_FS_XATTR) += xattr.o
erofs-$(CONFIG_EROFS_FS_ZIP) += unzip_vle.o unzip_vle_lz4.o
CFLAGS_unzip_vle.o := $(call cc-disable-warning, unused-label)

# lz4 algorithm related stuffs
erofs-$(CONFIG_EROFS_FS_ZIP) += unzip_lz4.o
erofs-$(CONFIG_ARM64) += $(addprefix lz4armv8/, \
			   lz4armv8.o		\
			   lz4accel.o		\
			   )
CFLAGS_unzip_lz4.o += -O3


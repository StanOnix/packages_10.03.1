#
# Copyright (C) 2006-2010 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=librsync
PKG_VERSION:=0.9.7
PKG_RELEASE:=4

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=@SF/librsync
PKG_MD5SUM:=24cdb6b78f45e0e83766903fd4f6bc84

PKG_FIXUP:=libtool
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

TARGET_CFLAGS += $(FPIC)

define Package/librsync
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=implementation of the rolling-checksum algorithm
  URL:=http://librsync.sourceforge.net/
endef

define Package/librsync/description
	librsync implements the rolling-checksum algorithm of remote file
	synchronization that was popularized by the rsync utility and is
	used in rproxy. This algorithm transfers the differences between 2
	files without needing both files on the same system.
endef

define Build/Configure
	$(call Build/Configure/Default, \
		--enable-shared \
		--enable-static \
	);
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/librsync{,-config}.h $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/librsync.{a,so*} $(1)/usr/lib/
endef

define Package/librsync/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/librsync.so.* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,librsync))

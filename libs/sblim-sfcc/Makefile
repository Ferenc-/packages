#
# Copyright (C) 2006-2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=sblim-sfcc
PKG_VERSION:=2.2.7
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=@SF/sblim/sblim-sfcc
PKG_MD5SUM:=68ebc22f243a266e779ec1799f5dc56d
PKG_MAINTAINER:=vacant

PKG_LICENSE:=Eclipse Public License - v 1.0
PKC_LICENSE_FILES:=COPYING

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/host-build.mk
include $(INCLUDE_DIR)/package.mk

define Package/sblim-sfcc
  SECTION:=libs
  CATEGORY:=Libraries
  DEPENDS:=+libcurl +libpthread
  TITLE:=Standards Based Linux Instrumentation
  URL:=http://sourceforge.net/projects/sblim/files/sblim-sfcc/
endef

TARGET_CFLAGS += $(FPIC)

CONFIGURE_ARGS += \
	--enable-shared \
	--enable-static \

define Build/InstallDev

	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/cimc $(1)/usr/include/
	$(CP) $(PKG_INSTALL_DIR)/usr/include/CimClientLib $(1)/usr/include/

	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libcimcclient.{la,a,so*} $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libcimcClientXML.{la,a,so*} $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libcmpisfcc.{la,a,so*} $(1)/usr/lib/

endef

define Package/sblim-sfcc/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libcimcclient.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libcimcClientXML.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libcmpisfcc.so* $(1)/usr/lib/
endef

$(eval $(call HostBuild))
$(eval $(call BuildPackage,sblim-sfcc))

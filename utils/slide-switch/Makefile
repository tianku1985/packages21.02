#
# Copyright (C) 2016, 2018-2019, 2022 Jeffery To
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=slide-switch
PKG_VERSION:=0.9.7
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/jefferyto/openwrt-slide-switch.git
PKG_MIRROR_HASH:=a0bba3e952179d96667be293a230b2ad26b3bfdd7b01962116f2c99428696bc5
PKG_SOURCE_VERSION:=$(PKG_VERSION)

PKG_BUILD_PARALLEL:=1
PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

PKG_LICENSE:=GPL-2.0-only
PKG_LICENSE_FILES:=COPYING
PKG_MAINTAINER:=Jeffery To <jeffery.to@gmail.com>

include $(INCLUDE_DIR)/package.mk

define Package/slide-switch
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=Translate switch position change to button press
  URL:=https://github.com/jefferyto/openwrt-slide-switch
  DEPENDS:=+jshn +jsonfilter
  PKGARCH:=all
endef

define Package/slide-switch/description
slide-switch translates slide switch position changes into normal button
presses and releases for OpenWrt devices.
endef

define Package/slide-switch/install
	$(INSTALL_DIR) $(1)/etc/hotplug.d/button
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/etc/hotplug.d/button/50-slide-switch \
		$(1)/etc/hotplug.d/button

	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/etc/init.d/zzz-slide-switch \
		$(1)/etc/init.d

	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/usr/sbin/slide-switch \
		$(1)/usr/sbin

	$(INSTALL_DIR) $(1)/usr/share/slide-switch
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/slide-switch/functions.sh \
		$(PKG_INSTALL_DIR)/usr/share/slide-switch/switch-data.json \
		$(1)/usr/share/slide-switch
endef

define Package/slide-switch/postinst
[ -n "$$IPKG_INSTROOT" ] || /usr/sbin/slide-switch clean
endef

define Package/slide-switch/prerm
[ -n "$$IPKG_INSTROOT" ] || /usr/sbin/slide-switch clean
endef

$(eval $(call BuildPackage,slide-switch))

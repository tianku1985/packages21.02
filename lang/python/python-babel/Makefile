#
# Copyright (C) 2019-2021 CZ.NIC, z. s. p. o. (https://www.nic.cz/)
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-babel
PKG_VERSION:=2.9.1
PKG_RELEASE:=1

PYPI_NAME:=Babel
PKG_HASH:=bc0c176f9f6a994582230df350aa6e05ba2ebe4b3ac317eab29d9be5d2768da0

PKG_MAINTAINER:=Josef Schlehofer <josef.schlehofer@nic.cz>
PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=LICENSE

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python3-package.mk

define Package/python3-babel
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Internationalization utilities
  URL:=https://babel.pocoo.org/en/latest/
  DEPENDS:= \
    +python3-cgi \
    +python3-decimal \
    +python3-distutils \
    +python3-email \
    +python3-light \
    +python3-pytz \
    +python3-urllib
endef

define Package/python3-babel/description
  Babel is an integrated collection of utilities that assist in
  internationalizing and localizing Python applications
  with an emphasis on web-based applications.
endef

$(eval $(call Py3Package,python3-babel))
$(eval $(call BuildPackage,python3-babel))
$(eval $(call BuildPackage,python3-babel-src))

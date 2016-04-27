#
# Copyright (C) 2016 Wei Yongjun <weiyj.lk@gmail.com>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=newt
PKG_VERSION:=0.52.18

PKG_LICENSE:=LGPLv2
PKG_MAINTAINER:=Wei Yongjun <weiyj.lk@gmail.com>

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://fedorahosted.org/releases/n/e/newt/

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

CONFIGURE_ARGS += \
	--without-tcl

include $(INCLUDE_DIR)/package.mk

define Package/libnewt
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=A library for text mode user interfaces
  URL:=https://fedorahosted.org/newt/
  DEPENDS:=+libslang +libpopt
endef

define Package/libnewt/description
  Newt is a programming library for color text mode, widget based user
  interfaces.  Newt can be used to add stacked windows, entry widgets,
  checkboxes, radio buttons, labels, plain text fields, scrollbars,
  etc., to text mode user interfaces.
endef

define Package/python-newt
  SECTION:=language-python
  CATEGORY:=Languages
  TITLE:=Python 2 bindings for newt
  URL:=https://fedorahosted.org/newt/
  DEPENDS:=+python +libnewt +libpopt
endef

define Package/libnewt/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_BUILD_DIR)/libnewt.so* $(1)/usr/lib/
endef

define Package/python-newt/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)/
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
		$(1)$(PYTHON_PKG_DIR)/
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_BUILD_DIR)/newt.h $(1)/usr/include/

	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_BUILD_DIR)/libnewt.{a,so*} $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libnewt))
$(eval $(call BuildPackage,python-newt))

#
# Copyright (C) 2016 Wei Yongjun <weiyj.lk@gmail.com>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=wuti
PKG_VERSION:=0.0.1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL=file:///pub/scm/mygit/openwrt/openwrt-wuti
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=87ddef7eda9c966910126bb103746118ef68bd8f
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

PKG_LICENSE:=GPLv2
PKG_MAINTAINER:=Wei Yongjun <weiyj.lk@gmail.com>

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/python-wuti
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=The Openwrt system installer
  URL:=http://github.org/weiyj
  DEPENDS:=+python +python-newt
endef

define Package/python-wuti/description
  The Openwrt system installer
endef

define Package/python-wuti/install
	$(INSTALL_DIR) $(1)/sbin
	$(CP) $(PKG_BUILD_DIR)/wuti.py $(1)/sbin/wuti
	chmod +x $(1)/sbin/wuti

	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)/
	$(CP) $(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* $(1)$(PYTHON_PKG_DIR)/

	$(INSTALL_DIR) $(1)/etc/profile.d
	$(INSTALL_BIN) ./files/wuti.sh $(1)/etc/profile.d/wuti.sh
endef

$(eval $(call BuildPackage,python-wuti))

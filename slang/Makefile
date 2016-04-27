#
# Copyright (C) 2016 Wei Yongjun <weiyj.lk@gmail.com>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=slang
PKG_VERSION:=2.3.0
PKG_RELEASE:=1

PKG_LICENSE:=GPLv2+
PKG_MAINTAINER:=Wei Yongjun <weiyj.lk@gmail.com>

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://www.jedsoft.org/releases/slang/
PKG_MD5SUM:=80f4e64189b6f28fd420b829b44a6723

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/libslang
  SECTION:=epol
  CATEGORY:=Libraries
  TITLE:=The shared library for the S-Lang extension language
  URL:=http://www.jedsoft.org/slang/
  DEPENDS:=+terminfo libc
endef

define Package/libslang/description
 S-Lang is an interpreted language and a programming library.  The
 S-Lang language was designed so that it can be easily embedded into
 a program to provide the program with a powerful extension language.
 The S-Lang library, provided in this package, provides the S-Lang
 extension language.  S-Lang's syntax resembles C, which makes it easy
 to recode S-Lang procedures in C if you need to.
endef

TARGET_CFLAGS += $(FPIC)
TARGET_LDFLAGS += -L../src/${ARCH}elfobjs
	
CONFIGURE_ARGS += \
	--enable-largefile \
	--disable-warnings \
	--with-terminfo=default \
	--with-readline=slang \
	--without-x \
	--without-pcre \
	--without-onig \
	--without-png \
	--without-z \
        ac_cv_path_nc5config=$(PWD)/files/ncurses5-config

define Build/Compile
	$(call Build/Compile/Default)
	$(MAKE) -C $(PKG_BUILD_DIR) \
		CFLAGS="$(TARGET_CFLAGS)" \
		LDFLAGS="$(TARGET_LDFLAGS)" \
		DESTDIR="$(PKG_INSTALL_DIR)" \
		static install install-static
endef

define Package/libslang/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libslang.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/slang/ $(1)/usr/lib/
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/*.h $(1)/usr/include/

	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libslang.{a,so*} $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libslang))

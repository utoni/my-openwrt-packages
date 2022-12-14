#
# Copyright (C) 2019-2020 CZ.NIC z.s.p.o. (http://www.nic.cz/)
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libhtp
PKG_VERSION:=0.5.40
PKG_RELEASE=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/OISF/libhtp/tar.gz/$(PKG_VERSION)?
PKG_HASH:=0afaff837c295c868db8c967b87b1b5e21c0386c15c3b5ead474799724c54ef8

PKG_BUILD_PARALLEL:=1
PKG_INSTALL:=1
PKG_FIXUP:=autoreconf

PKG_MAINTAINER:=CZ.NIC <packaging@turris.cz>
PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=LICENSE
PKG_CPE_ID:=cpe:/a:oisf:libhtp

include $(INCLUDE_DIR)/package.mk

define Package/libhtp
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=HTTP normalizer and parser library
  URL:=https://github.com/OISF/libhtp
  DEPENDS:=+zlib
endef

define Package/libhtp/description
  LibHTP is a security-aware parser for the HTTP protocol and the related bits and pieces.
endef

CONFIGURE_ARGS += --disable-static

define Build/InstallDev
	sed -i 's|^prefix=\(.*\)*|prefix='"$(STAGING_DIR)"'\1|' $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/htp.pc
	$(CP) $(PKG_INSTALL_DIR)/* $(1)/
endef

define Package/libhtp/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libhtp*.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libhtp))

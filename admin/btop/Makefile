#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=btop
PKG_RELEASE:=1
PKG_VERSION:=1.2.8

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/aristocratos/btop/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=7944b06e3181cc1080064adf1e9eb4f466af0b84a127df6697430736756a89ac

PKG_MAINTAINER:=Toni Uhlig <matzeton@googlemail.com>
PKG_LICENSE:=Apache-2.0
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/btop
  SECTION:=admin
  CATEGORY:=Administration
  TITLE:=A monitor of resources
  DEPENDS:=+libstdcpp
  URL:=https://github.com/aristocratos/btop
endef

define Package/btop/description
  Resource monitor that shows usage and stats for
  processor, memory, disks, network and processes.
  C++ version and continuation of bashtop and bpytop.
endef

MAKE_FLAGS += \
	QUIET=true BANNER='' LDCXXFLAGS=''

define Package/btop/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/bin/btop $(1)/usr/bin/
endef

$(eval $(call BuildPackage,btop))

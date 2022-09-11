include $(TOPDIR)/rules.mk

PKG_NAME:=tools
PKG_VERSION:=1.0
PKG_RELEASE:=$(PKT_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/utoni/tools.git
PKG_SOURCE_VERSION:=6a7eabbfee8c8df1a21f3da6e0fd5643c40ee607
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz
PKG_MIRROR_HASH:=aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)

PKG_MAINTAINER:=Toni Uhlig <matzeton@gmail.com>

include $(INCLUDE_DIR)/package.mk

define Package/tools
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=My Tools
  URL:=https://github.com/lnslbrty/tools
  DEPENDS:=+libncurses
endef

define Package/tools/description
  My Tools
endef

define Build/Compile
	rm -rf $(PKG_INSTALL_DIR)
	mkdir -p $(PKG_INSTALL_DIR)
	$(MAKE) -C $(PKG_BUILD_DIR) \
		CC="$(TARGET_CC) $(TARGET_CFLAGS)" LDFLAGS="$(TARGET_LDFLAGS)" \
		MAKE_NCURSES=1 PREFIX="$(1)"
endef

define Package/tools/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) \
		$(addprefix $(PKG_BUILD_DIR)/,aes asciihexer ascii85 dummyshell suidcmd progressbar gol) \
		$(1)/usr/bin/
endef

$(eval $(call BuildPackage,tools))

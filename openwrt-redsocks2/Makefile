include $(TOPDIR)/rules.mk

PKG_NAME:=redsocks2
PKG_VERSION:=0.67
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_URL:=https://github.com/semigodking/redsocks.git
PKG_SOURCE_VERSION:=53cad23a14afdd5f61a0542615beb7f4d98be728

PKG_LICENSE:=GPLv2
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Zhuofei Wang <SemigodKing@gmail.com>

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)/$(PKG_NAME)-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk

define Package/redsocks2/Default
	SECTION:=net
	CATEGORY:=Network
	TITLE:=TCP to SOCKS or HTTPS proxy server $(2)
	URL:=https://github.com/semigodking/redsocks
	VARIANT:=$(1)
	DEPENDS:=$(3)
endef

Package/redsocks2-openssl = $(call Package/redsocks2/Default,openssl,(OpenSSL),+libevent2 +libopenssl)

define Package/redsocks2/description
Redirect any TCP connection to a SOCKS or HTTPS proxy server. \
This is a modified version of original redsocks. \
The name is changed to be REDSOCKS2 since this release to distinguish with original redsocks. \
This variant is useful for anti-GFW (Great Fire Wall).
endef

define Package/redsocks2/conffiles
/etc/config/redsocks2
endef

Package/redsocks2-openssl/description = $(Package/redsocks2/description)
Package/redsocks2-openssl/conffiles = $(Package/redsocks2/conffiles)

define Package/redsocks2/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_DIR) $(1)/etc/redsocks2
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/redsocks2 $(1)/usr/bin
	$(INSTALL_BIN) ./files/redsocks2.init $(1)/etc/init.d/redsocks2
	$(INSTALL_DATA) ./files/redsocks2.config $(1)/etc/config/redsocks2
	$(INSTALL_DATA) ./files/redsocks2.template $(1)/etc/redsocks2/config.template
endef

Package/redsocks2-openssl/install = $(Package/redsocks2/install)

$(eval $(call BuildPackage,redsocks2-openssl))

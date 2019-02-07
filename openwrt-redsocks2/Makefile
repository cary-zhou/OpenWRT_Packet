include $(TOPDIR)/rules.mk

PKG_NAME:=redsocks2
PKG_VERSION:=0.67
PKG_RELEASE=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/semigodking/redsocks.git
PKG_SOURCE_VERSION:=53cad23a14afdd5f61a0542615beb7f4d98be728
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz

PKG_LICENSE:=GPLv2
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=semigodking

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)/$(PKG_NAME)-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk

define Package/redsocks2
	SECTION:=net
	CATEGORY:=Network
	TITLE:=Redirect any TCP connection to a SOCKS or HTTPS proxy server
	URL:=https://github.com/semigodking/redsocks
	DEPENDS:=+libevent2 +libopenssl
endef

define Package/redsocks2/Compile
    $(MAKE) ENABLE_STATIC=true
endif

define Package/redsocks2/description
This is a modified version of original redsocks. \
This variant is useful for anti-GFW (Great Fire Wall).
endef

define Package/redsocks2/conffiles
/etc/config/redsocks2
endef

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

$(eval $(call BuildPackage,redsocks2))

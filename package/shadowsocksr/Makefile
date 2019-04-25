include $(TOPDIR)/rules.mk

PKG_NAME:=ssr-libev
PKG_VERSION:=2.5.6

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/shadowsocksr-backup/shadowsocksr-libev.git
PKG_SOURCE_VERSION:=e2373d7199102f383b741da148b989c7c1e8832e
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_MAINTAINER:=breakwa11

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)/$(PKG_NAME)-$(PKG_VERSION)

PKG_INSTALL:=1
PKG_FIXUP:=autoreconf
PKG_USE_MIPS16:=0
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/shadowsocksr-libev
	SECTION:=net
	CATEGORY:=Network
	VARIANT:=mbedtls
	TITLE:=Lightweight Secured Socks5 Proxy
	URL:=https://github.com/shadowsocksr-backup/shadowsocksr-libev
	DEPENDS:=+libmbedtls +libpcre +libpthread +zlib
endef

define Package/shadowsocksr-libev/description
ShadowsocksR-libev is a lightweight secured socks5 proxy for embedded devices
endef

define Package/shadowsocksr-libev/conffiles
/etc/shadowsocksr.json
endef

CONFIGURE_ARGS += --disable-ssp --disable-documentation --disable-assert 

ifeq ($(BUILD_VARIANT),mbedtls)
	CONFIGURE_ARGS += --with-crypto-library=mbedtls
endif

define Package/shadowsocksr-libev/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_CONF) ./files/shadowsocksr.json $(1)/etc/shadowsocksr.json
	$(INSTALL_CONF) ./files/gfwlist.conf $(1)/etc/gfwlist.conf
	$(INSTALL_BIN) ./files/fuckgfw $(1)/etc/init.d/fuckgfw
	$(INSTALL_BIN) ./files/shadowsocksr.init $(1)/etc/init.d/shadowsocksr
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/ss-local $(1)/usr/bin/ssr-local
endef

$(eval $(call BuildPackage,shadowsocksr-libev))

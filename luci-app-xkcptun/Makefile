include $(TOPDIR)/rules.mk

PKG_NAME:=luci-app-xkcptun
PKG_VERSION:=1.0
PKG_RELEASE:=2

PKG_LICENSE:=GPL-3.0

include $(INCLUDE_DIR)/package.mk

define Package/luci-app-xkcptun
	SECTION:=luci
	CATEGORY:=LuCI
	SUBMENU:=3. Applications
	TITLE:=LuCI support for xkcptun
	URL:=https://github.com/liudf0716/xkcptun
	MAINTAINER:=Lars Gierth <larsg@systemli.org>
	PKGARCH:=all
	DEPENDS:=+luci-base
endef

define Package/luci-app-xkcptun/description
	This package allows you to configure xkcptun using LuCI.
endef

define Package/luci-app-xkcptun/postinst
#!/bin/sh
UCI_DEF_FILE=90_luci_xkcptun
if [ -z "$${IPKG_INSTROOT}" ]; then
	if [ -f /etc/uci-defaults/$UCI_DEF_FILE ]; then
		( . /etc/uci-defaults/$UCI_DEF_FILE ) && \
		rm -f /etc/uci-defaults/$UCI_DEF_FILE
	fi
	rm -rf /tmp/luci-indexcache /tmp/luci-modulecache
fi
exit 0
endef

define Package/luci-app-xkcptun/install
	$(INSTALL_DIR) $(1)/usr/lib/lua/luci
	$(CP) ./luasrc/* $(1)/usr/lib/lua/luci
	$(CP) ./root/* $(1)/
endef

$(eval $(call BuildPackage,luci-app-xkcptun))

include $(TOPDIR)/rules.mk

PKG_NAME:=dnsforwarder
PKG_VERSION:=6.1.15

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/holmium/dnsforwarder.git
PKG_SOURCE_VERSION:=21ea51820bed1edc20b27287e7c5917374bc4ab2
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)/$(PKG_NAME)-$(PKG_VERSION)

PKG_LICENSE:=GPLv3
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Jiang Zhe Hu
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/dnsforwarder
	SECTION:=net
	CATEGORY:=Network
	TITLE:=Forwarding DNS queries on TCP transport
	URL:=https://github.com/holmium/dnsforwarder.git
	DEPENDS:=+libpthread
endef

CONFIGURE_ARGS += --enable-downloader=no

define Package/dnsforwarder/description
Forwarding DNS queries on TCP transport.
endef

define Package/dnsforwarder/conffiles
endef

define Package/dnsforwarder/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_DIR) $(1)/etc/dnsforwarder
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/dnsforwarder $(1)/usr/bin/dnsforwarder
	$(INSTALL_BIN) ./files/init.d/dnsforwarder $(1)/etc/init.d/dnsforwarder
	$(CP) ./files/dnsforwarder/* $(1)/etc/dnsforwarder/
endef

$(eval $(call BuildPackage,dnsforwarder))

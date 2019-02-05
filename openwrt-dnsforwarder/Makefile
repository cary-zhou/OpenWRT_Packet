include $(TOPDIR)/rules.mk

PKG_NAME:=dnsforwarder
PKG_VERSION:=6.1.15
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/holmium/dnsforwarder.git
PKG_SOURCE_VERSION:=587e61ae4d75dc976f538088b715a3c8ee26c144
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
endef

define Package/dnsforwarder/description
Forwarding DNS queries on TCP transport.
endef

define Package/dnsforwarder/conffiles
/etc/config/dnsforwarder
endef

define Package/dnsforwarder/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/dnsforwarder $(1)/usr/bin/dnsforwarder
	$(INSTALL_DATA) ./files/config/dnsforwarder $(1)/etc/config/dnsforwarder
	$(INSTALL_BIN) ./files/init.d/dnsforwarder $(1)/etc/init.d/dnsforwarder
	$(CP) ./files/dnsforwarder/* $(1)/etc/dnsforwarder/
endef

$(eval $(call BuildPackage,dnsforwarder))

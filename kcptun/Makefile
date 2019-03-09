include $(TOPDIR)/rules.mk

PKG_NAME:=kcptun
PKG_VERSION:=20190109
PKG_RELEASE:=1

ifeq ($(ARCH),x86_64)
	PKG_ARCH_KCPTUN:=amd64
endif
ifeq ($(ARCH),mipsel)
	PKG_ARCH_KCPTUN:=mipsle
endif
ifeq ($(ARCH),mips)
	PKG_ARCH_KCPTUN:=mips
endif
ifeq ($(ARCH),i386)
	PKG_ARCH_KCPTUN:=386
endif
ifeq ($(ARCH),arm)
	PKG_ARCH_KCPTUN:=arm
endif

PKG_SOURCE:=$(PKG_NAME)-linux-$(PKG_ARCH_KCPTUN)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/xtaci/kcptun/releases/download/v$(PKG_VERSION)
PKG_HASH:=skip
PKG_CAT:=zcat

include $(INCLUDE_DIR)/package.mk

define Package/kcptun
	SECTION:=net
	CATEGORY:=Network
	TITLE:=An extremely simple udp tunnel based on KCP
	URL:=https://github.com/xtaci/kcptun
endef

define Package/kcptun/description
An extremely simple udp tunnel based on KCP.
endef

define Build/Compile
endef

define Package/kcptun/postinst
endef

define Package/kcptun/conffiles
/etc/config/kcptun
endef

define Package/kcptun/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_DATA) ./files/etc/config/kcptun $(1)/etc/config/kcptun
	$(INSTALL_BIN) ./files/etc/init.d/kcptun $(1)/etc/init.d/kcptun
	$(INSTALL_BIN) $(BUILD_DIR)/client_linux_arm7 $(1)/usr/bin/kcptun
endef

$(eval $(call BuildPackage,kcptun))

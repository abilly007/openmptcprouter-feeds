#
# Copyright (C) 2015 OVH
# Copyright (C) 2018 Ycarus (Yannick Chabanois) <ycarus@zugaina.org>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/angt/glorytun.git
PKG_SOURCE_VERSION:=c15343f8f6fb275fe9bed56ca251bb801ea5d67b

PKG_NAME:=glorytun-udp
PKG_VERSION:=0.0.99-mud
PKG_RELEASE:=17

PKG_FIXUP:=autoreconf

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
SECTION:=net
CATEGORY:=Network
DEPENDS:=+kmod-tun +libsodium +librt
TITLE:=Glorytun
URL:=https://github.com/angt/glorytun
SUBMENU:=VPN
endef

TARGET_CFLAGS += -std=c99 -D_GNU_SOURCE -DGT_RUNDIR=\"\\\"/tmp\"\\\"

define Package/$(PKG_NAME)/conffiles
/etc/config/glorytun
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/glorytun $(1)/usr/sbin/$(PKG_NAME)
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) init $(1)/etc/init.d/$(PKG_NAME)
	$(INSTALL_DIR) $(1)/etc/config
	touch $(1)/etc/config/glorytun
endef

$(eval $(call BuildPackage,$(PKG_NAME)))


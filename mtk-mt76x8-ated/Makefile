#
# Copyright (C) 2010-2013 hua.shao@mediatek.com
#
# MTK Property Software.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=mtk-mt76x8-ated
PKG_RELEASE:=1

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)
PKG_KCONFIG:=RALINK_MT7620 RALINK_MT7621 RALINK_MT7628
PKG_CONFIG_DEPENDS:=$(foreach c, $(PKG_KCONFIG),$(if $(CONFIG_$c),CONFIG_$(c)))


include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/kernel.mk

define Package/mtk-mt76x8-ated
  CATEGORY:=Ralink SDK
  TITLE:=ATE Daemon
endef

define Package/mtk-mt76x8-ated/description
  ATE Daemon
endef

define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
	$(CP) ./src/* $(PKG_BUILD_DIR)/
endef

TARGET_CFLAGS += \
	$(foreach c, $(PKG_KCONFIG),$(if $(CONFIG_$c),-DCONFIG_$(c)=$(CONFIG_$c)))

#MAKE_FLAGS += \
	CFLAGS="$(TARGET_CFLAGS)"

define Package/mtk-mt76x8-ated/install
	$(INSTALL_DIR) $(1)/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/ated $(1)/bin
endef


$(eval $(call BuildPackage,mtk-mt76x8-ated))


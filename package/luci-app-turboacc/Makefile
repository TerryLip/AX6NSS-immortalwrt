# SPDX-Identifier-License: GPL-3.0-only
#
# Copyright (C) 2023-2024 沉默の金 <cmzj@cmzj.org>
# Copyright (C) 2022 Lean <coolsnowwolf@gmail.com>
# Copyright (C) 2019-2022 ImmortalWrt.org

include $(TOPDIR)/rules.mk

PKG_NAME:=luci-app-turboacc
PKG_VERSION:=1.4
PKG_RELEASE:=1

PKG_LICENSE:=GPL-3.0-only
PKG_MAINTAINER:=chenmozhijin <cmzj11@gmail.com>

PKG_CONFIG_DEPENDS:= \
	CONFIG_PACKAGE_$(PKG_NAME)_INCLUDE_BBR_CCA \
	CONFIG_PACKAGE_$(PKG_NAME)_INCLUDE_OFFLOADING \
	CONFIG_PACKAGE_$(PKG_NAME)_INCLUDE_NFT_FULLCONE

LUCI_TITLE:=LuCI support for Flow Offload
LUCI_DEPENDS:= \
	+luci +luci-compat \
	+PACKAGE_$(PKG_NAME)_INCLUDE_BBR_CCA:kmod-tcp-bbr \
	+PACKAGE_$(PKG_NAME)_INCLUDE_OFFLOADING:kmod-nft-offload \
	+PACKAGE_$(PKG_NAME)_INCLUDE_NFT_FULLCONE:kmod-nft-fullcone
LUCI_PKGARCH:=all

define Package/$(PKG_NAME)/config
config PACKAGE_$(PKG_NAME)_INCLUDE_OFFLOADING
	bool "Include Flow Offload"
	default y

config PACKAGE_$(PKG_NAME)_INCLUDE_BBR_CCA
	bool "Include BBR CCA"
	default y

config PACKAGE_$(PKG_NAME)_INCLUDE_NFT_FULLCONE
	bool "Include NFT FULLCONE"
	default y
endef

include $(TOPDIR)/feeds/luci/luci.mk

# call BuildPackage - OpenWrt buildroot signature

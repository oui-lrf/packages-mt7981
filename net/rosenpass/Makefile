# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2024 Paul Spooren <mail@aparcar.org>

include $(TOPDIR)/rules.mk

PKG_NAME:=rosenpass
PKG_VERSION:=0.2.1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/rosenpass/rosenpass/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=09dffa62c9bbf3bfa4b34c7667f4052f3c262195a45da9c21c8123f197e7742a

PKG_MAINTAINER:=Paul Spooren <mail@aparcar.org>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_DEPENDS:=rust/host bpf-headers

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/bpf.mk
include ../../lang/rust/rust-package.mk

define Package/rosenpass
  SECTION:=net
  CATEGORY:=Network
  TITLE:=PQC for WireGuard
  DEPENDS:=$(RUST_ARCH_DEPENDS) +libsodium
  URL:=https://github.com/rosenpass/rosenpass
endef

define Package/rosenpass/description
  Rosenpass is a post-quantum secure VPN that uses WireGuard to transport the
  actual data.
endef

Build/Compile = $(call Build/Compile/Cargo,rosenpass)

$(eval $(call RustBinPackage,rosenpass))
$(eval $(call BuildPackage,rosenpass))

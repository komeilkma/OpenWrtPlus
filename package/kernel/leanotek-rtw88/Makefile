include $(TOPDIR)/rules.mk

PKG_NAME:=leanotek-rtw88-usb-new
PKG_RELEASE:=2

PKG_LICENSE:=GPLv2
PKG_LICENSE_FILES:=

PKG_SOURCE_URL:=https://github.com/komeilkma/openwrt-rtw88.git
PKG_SOURCE_PROTO:=git
#PKG_SOURCE_DATE:=2020-10-17
#PKG_SOURCE_VERSION:=f9f4ee862b3e1f9e6a543d503a084rffg56
PKG_SOURCE_VERSION:=d6b859eed430c24cb74301cafaa1ea45trgg654
#PKG_MIRROR_HASH:=60359df8b49fa433d38b968b0df7eaddaca10f13cdd57471394bac1f6e5a162e

# PKG_MAINTAINER:=
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/kernel.mk
include $(INCLUDE_DIR)/package.mk

define KernelPackage/rtw88-usb-leanotek
  SUBMENU:=Wireless Drivers
  TITLE:= Realtek-Leanotek RTL8822CU AP Mode
   DEPENDS:=+kmod-cfg80211 +kmod-mac80211 +kmod-usb-core +@DRIVER_11N_SUPPORT +@DRIVER_11AC_SUPPORT
  FILES:=\
	$(PKG_BUILD_DIR)/rtw88_pci.ko \
	$(PKG_BUILD_DIR)/rtw88_usb.ko \
	$(PKG_BUILD_DIR)/rtw88_core.ko \
	$(PKG_BUILD_DIR)/rtw88_8822cu.ko \
	$(PKG_BUILD_DIR)/rtw88_8822ce.ko \
	$(PKG_BUILD_DIR)/rtw88_8822c.ko \
	$(PKG_BUILD_DIR)/rtw88_8822b.ko \
	$(PKG_BUILD_DIR)/rtw88_8822be.ko \
	$(PKG_BUILD_DIR)/rtw88_8822bu.ko \
	$(PKG_BUILD_DIR)/rtw88_8723d.ko \
	$(PKG_BUILD_DIR)/rtw88_8723de.ko \
	$(PKG_BUILD_DIR)/rtw88_8821c.ko \
	$(PKG_BUILD_DIR)/rtw88_8821cu.ko
  AUTOLOAD:=$(call AutoProbe, rtw88_8821cu)
endef

define Build/Compile
	+$(MAKE) $(PKG_JOBS) -C "$(LINUX_DIR)" \
		$(KERNEL_MAKE_FLAGS) \
		M="$(PKG_BUILD_DIR)" \
		modules
endef

$(eval $(call KernelPackage,rtw88-usb-leanotek))
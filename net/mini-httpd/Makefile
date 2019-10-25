#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=mini_httpd
PKG_VERSION:=1.30
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://acme.com/software/mini_httpd/
PKG_HASH:=9c4481802af8dde2e164062185c279e9274525c3af93d014fdc0b80cf30bca6e

#PKG_LICENSE:=GPL-2.0-or-later
#PKG_LICENSE_FILES:=

include $(INCLUDE_DIR)/package.mk

define Package/mini-httpd
  SUBMENU:=Web Servers/Proxies
  SECTION:=net
  CATEGORY:=Network
  TITLE:=small HTTP server
  URL:=https://acme.com/software/mini_httpd/
#  MAINTAINER:=Tijs Van Buggenhout <tvbuggen@netzerk.be>, \
#              Marcin Jurkowski <marcin1j@gmail.com>
endef

define Package/mini-httpd/description
mini_httpd is a small HTTP server. Its performance is not great, but for low 
or medium traffic sites it's quite adequate. It implements all the basic 
features of an HTTP server, including:

    GET, HEAD, and POST methods.
    CGI.
    Basic authentication.
    Security against ".." filename snooping.
    The common MIME types.
    Trailing-slash redirection.
    index.html, index.htm, index.cgi
    Directory listings.
    Multihoming / virtual hosting.
    Standard logging.
    Custom error pages.

It can also be configured to do SSL/HTTPS and IPv6.
endef

#define Package/htpdate/conffiles
#/etc/config/htpdate
#endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) \
		$(TARGET_CONFIGURE_OPTS) \
		CFLAGS="$(TARGET_CFLAGS)"
#	echo starting shell; exit by CTRL-D
endef

define Package/mini-httpd/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/mini_httpd $(1)/usr/sbin/
	$(INSTALL_DIR) $(1)/etc/
	$(INSTALL_CONF) $(PKG_BUILD_DIR)/mini_httpd.cnf $(1)/etc/
	#$(INSTALL_DIR) $(1)/etc/init.d/
	#$(INSTALL_BIN) ./files/htpdate.init $(1)/etc/init.d/htpdate
endef

$(eval $(call BuildPackage,mini-httpd))

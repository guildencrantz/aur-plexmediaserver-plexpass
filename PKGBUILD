# Contributor: Praekon <praekon@googlemail.com>
# Contributor: Arthur <arthur.darcet@m4x.org>
# Contributor: Jon Wiersma <archaur@jonw.org>
# Contributor: monty <linksoft [at] gmx [dot] de>
# Contributor: Mikhail Davidov <sirus@haxsys.net>
# Contributor: Tom Moore <t.moore01 [at] gmail [dot] com>
# Maintainer: Matt Henkel <guildencrantz@gmail.com>

pkgname=plexmediaserver-plexpass
pkgver=0.9.9.16.555
pkgrel=1
_subver=50cd0c3
pkgdesc="PlexPass Release of Plex Media Server for Linux"
url='http://www.plexapp.com'
arch=('i686' 'x86_64')
license=('closed')
depends=('rsync' 'avahi')
conflicts=('plexmediaserver')
backup=('etc/conf.d/plexmediaserver')
install='plexmediaserver.install'

if [ "$CARCH" = "i686" ]; then
    _arch='i386'
    md5sums=('5d6d95540837d7469f6849a12d4cbef2')
elif [ "$CARCH" = "x86_64" ]; then
    _arch='amd64'
    md5sums=('016ec179e95b972ea57ff10f1f63f863')
fi

source=("http://downloads.plexapp.com/plex-media-server/${pkgver}-${_subver}/plexmediaserver_${pkgver}-${_subver}_${_arch}.deb" "plexmediaserver.conf.d" "plexmediaserver.service" "start_pms")
md5sums+=('32cdd9f9de446f6646616a0077151726'
          'd850fe41dd35aba09a375ac8d81175e0'
          '34e9ddaab4ffc84ab9835abd16a383b3')
build() {
    ar -xv plexmediaserver_${pkgver}-${_subver}_${_arch}.deb || return 1
    tar -zxf data.tar.gz || return 1
}

package() {
    mkdir -p "${pkgdir}/opt/plexmediaserver"
    mkdir -p "${pkgdir}/usr/lib/systemd/system"

    cp -r usr/lib/plexmediaserver/* "${pkgdir}/opt/plexmediaserver/"

    install -Dm755 "${srcdir}/start_pms" "${pkgdir}/opt/plexmediaserver/"
    install -Dm644 "${srcdir}/plexmediaserver.conf.d" "${pkgdir}/etc/conf.d/plexmediaserver"
    install -Dm644 "${srcdir}/plexmediaserver.service" "${pkgdir}/usr/lib/systemd/system/plexmediaserver.service"
}

# vim: set ts=4 sts=4 sw=4 ai et:


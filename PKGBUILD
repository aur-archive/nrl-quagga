# Maintainer: Tom Wambold <tom5760@gmail.com>
pkgname=nrl-quagga
pkgver=0.99.21mr2.2
pkgrel=1
pkgdesc="Implementation of OSPF MDR."
arch=('i686' 'x86_64')
url="http://cs.itd.nrl.navy.mil/work/ospf-manet/"
license=('GPL')
conflicts=(quagga)
provides=(quagga)
depends=(libcap ncurses libnl readline)
source=(http://downloads.pf.itd.nrl.navy.mil/ospf-manet/quagga-$pkgver/quagga-$pkgver.tar.gz
        makefile-fix-libcap-link-order.patch)
md5sums=('0ebb13d0cbe1d79a0e3522253aeebb74'
         '22a7ffe83fb9cf9b80fa17f36216eacb')

build() {
  cd "$srcdir/quagga-$pkgver"
  patch -p1 -i "$srcdir/makefile-fix-libcap-link-order.patch"
  autoreconf
  ./configure --prefix=/usr --enable-user=root --enable-group=root \
    --sysconfdir=/etc/quagga --localstatedir=/run/quagga \
    --enable-vtysh --enable-netlink
  make
}

package() {
  cd "$srcdir/quagga-$pkgver"
  make DESTDIR="$pkgdir/" install
}

# vim:set ts=2 sw=2 et:
md5sums=('5479881ecb1a6fc763f17ae62749bc54'
         '22a7ffe83fb9cf9b80fa17f36216eacb')

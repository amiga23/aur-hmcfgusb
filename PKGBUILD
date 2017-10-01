# Maintainer: Ronny <ronny-aur[at]adke*org>
pkgname=hmcfgusb
pkgver=r172.a11a266
pkgrel=1
pkgdesc="An application, which emulates the HomeMatic LAN configuration adapter-protocol"
arch=('any')
url="https://0bin.readthedocs.org/en/latest/://git.zerfleddert.de/cgi-bin/gitweb.cgi/hmcfgusb/"
license=('custom')
depends=('libusb')
makedepends=('git')
source=("$pkgname"::'git://git.zerfleddert.de/hmcfgusb' 'hmland.service')
md5sums=('SKIP'
         '0a16d03b694990440e3d63fafe2949a5')
pkgver() {
  cd "$srcdir/$pkgname"
  printf 'r%s.%s' "$(git rev-list --count HEAD)" "$(git describe --always)"
}

build () {
	msg "Starting build..."
	cd "$srcdir/$pkgname"
	make
}
package() {
	mkdir -p "$pkgdir/opt/hmcfgusb"
	install -Dm644 ${srcdir}/$pkgname/LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
	install -Dm644 ${srcdir}/hmland.service "$pkgdir/usr/lib/systemd/system/hmland.service"
	install -Dm755 ${srcdir}/$pkgname/{flash-hmcfgusb,flash-ota,hmland,hmsniff} "$pkgdir/opt/hmcfgusb"
        install -Dm644 ${srcdir}/hmcfgusb/hmcfgusb.rules "$pkgdir/etc/udev/rules.d/hmcfgusb.rules"
}

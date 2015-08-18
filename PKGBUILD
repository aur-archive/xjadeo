# Maintainer : speps <speps at aur dot archlinux dot org>
# Contributor: N30N <archlinux@alunamation.com>

pkgname=xjadeo
pkgver=0.7.3
pkgrel=1
pkgdesc="A simple video player that is synchronized to jack transport."
arch=('i686' 'x86_64')
url="http://xjadeo.sourceforge.net"
license=('GPL')
depends=('ffmpeg' 'imlib2' 'jack' 'liblo' 'libxpm' 'libxv' 'portmidi')
makedepends=('qt4')
optdepends=('qt4: for the GUI (qjadeo)')
source=("http://downloads.sourceforge.net/$pkgname/$pkgname-$pkgver.tar.gz"
	"qjadeo.desktop")
install="$pkgname.install"
md5sums=('b5a67f7a8a8279f37ac681f40d6cbc10'
         '315e2ab44ce3edf4068ff6db48942908')

build() {
  cd "$srcdir/$pkgname-$pkgver"
  ./configure --prefix=/usr \
              --enable-qtgui \
              --with-qt4prefix=/usr/lib/qt4
  make
}

package() {
  cd "$srcdir/$pkgname-$pkgver"
  make DESTDIR="$pkgdir/" install

  # rc file
  install -Dm644 doc/xjadeorc "$pkgdir/etc/xjadeorc"

  # desktop file
  install -Dm644 ../qjadeo.desktop \
    "$pkgdir/usr/share/applications/qjadeo.desktop"

  # icon
  install -Dm644 doc/xjadeo.png \
    "$pkgdir/usr/share/pixmaps/qjadeo.png"
}

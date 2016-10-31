# $Id$
# Maintainer: Allan McRae <allan@archlinux.org>
# Contributor: judd <jvinet@zeroflux.org>

pkgname=flex-git
pkgver=2.6.2.r0.g35d2fdf
pkgrel=1
pkgdesc="A tool for generating text-scanning programs"
arch=('i686' 'x86_64')
url="http://flex.sourceforge.net"
license=('custom')
groups=('base-devel')
provides=("flex")
conflicts=("flex")
depends=('glibc' 'm4' 'sh')
makedepends=('help2man' 'git')
install=flex.install
source=("git+https://github.com/westes/flex.git#tag=v2.6.2")
md5sums=('SKIP')

pkgver() {
  cd "$srcdir/flex"
  git describe --long | sed 's/\([^-]*-g\)/r\1/;s/-/./g' | sed -e 's|^v||' 
}

prepare() {
  cd "$srcdir/flex"
  ./autogen.sh
}

build() {
  cd "$srcdir/flex"
  echo "$srcdir/flex"
  ./configure --prefix=/usr
  make
}

check() {
  cd "$srcdir/flex"
  make check
}

package() {
  cd "$srcdir/flex"

  make DESTDIR=$pkgdir install
  ln -s flex ${pkgdir}/usr/bin/lex

  install -Dm644 COPYING \
  	$pkgdir/usr/share/licenses/$pkgname/license.txt
}


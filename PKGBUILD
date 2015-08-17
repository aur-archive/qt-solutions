# Maintainer: Christian Bühler <christian@cbuehler.de>
pkgname=qt-solutions
pkgver=44.25e2cbb
pkgrel=1
pkgdesc="Components from the discontinued Qt Solutions product, a collection of minor Qt add-ons and former Qt modules which for various reasons have been pruned from Qt itself"
arch=('i686' 'x86_64')
url="http://qt.gitorious.org/qt-solutions"
license=('LGPL')
depends=('qt5-base')
makedepends=('git')
source=(git://github.com/qtproject/qt-solutions.git)
md5sums=('SKIP')

pkgver() {
  cd qt-solutions
  echo $(git rev-list --count master).$(git rev-parse --short master)
}

build() {
  cd "$srcdir/qt-solutions/qtservice"
  ./configure -library
  qmake-qt5
  make

  cd "$srcdir/qt-solutions/qtsingleapplication"
  ./configure -library
  qmake-qt5
  make
}

package() {
  mkdir -p "$pkgdir/usr/include"

  cd "$srcdir/qt-solutions/qtservice/src"
  cp QtServiceBase QtServiceController qtservice.h "$pkgdir/usr/include/"
  cp -r ../lib "$pkgdir/usr/"

  cd "$srcdir/qt-solutions/qtsingleapplication/src"
  cp QtSingleApplication qtsingleapplication.h "$pkgdir/usr/include/"
  cp -r ../lib "$pkgdir/usr/"
}

# vim:set ts=2 sw=2 et:

# $Id$
# Contributor: Bart Ribbers <bribbers@disroot.org>
# Contributor: Alexey Andreyev <aa13q@ya.ru>
# Maintainer: James Kittsmiller (AJSlye) <james@nulogicsystems.com>

pkgname=nemo-qml-plugin-contacts
pkgver=0.3.32
pkgrel=1
pkgdesc="Nemo QML contacts plugin"
arch=('x86_64' 'aarch64')
url="https://github.com/sailfishos/nemo-qml-plugin-contacts"
license=('BSD-3-Clause')
depends=('libphonenumber-nemo'
    'libmlocale'
    'mce'
    'mce-headers'
    'qtcontacts-sqlite'
    'libaccounts-qt6'
    'buteo-sync-plugin-carddav'
    'icu=76.1')

makedepends=(
    'qt6-tools'
    'clang'
)
source=("${url}/archive/refs/tags/$pkgver.tar.gz")
sha256sums=('c603ea408a2cbafba155f581abd4699ec62958d53b969b9475be64ce68c57d50')

prepare() {
    cd "$srcdir/${pkgname}-${pkgver}"
}

build() {
  cd $pkgname-$pkgver
  # Not possible to install in build subdir
  qmake6 VERSION=$pkgver
  make
}

package() {
  cd $pkgname-$pkgver
  make -j 1 INSTALL_ROOT="${pkgdir}" install
  # Remove installed tests
  rm -r "$pkgdir"/opt
}
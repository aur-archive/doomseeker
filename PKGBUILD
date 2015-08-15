# Maintainer: Robert La Spina <rkidlaspina [at] gmail [dot] com>
# Contributor: MP2E <MP2E {AT] archlinux.us>
# Contributor: PkmX <pkmx.tw@gmail.com>
#
# TODO: Find a way to put engine plugins in /usr/lib/$pkgname.
 
pkgname=doomseeker
pkgver=1.0
pkgrel=1
pkgdesc='A cross-platform server browser for various multiplayer Doom source-ports.'
arch=('i686' 'x86_64')
url='http://doomseeker.drdteam.org/'
depends=('qt4')
license=('GPL')
makedepends=('cmake' 'mercurial')
optdepends=('chocolate-doom'
'odamex'
'zandronum'
'vavoom'
'wine')
conflicts=('doomseeker-svn' 'doomseeker-hg')
source=("$pkgname"::"hg+https://bitbucket.org/Blzut3/$pkgname#tag=$pkgver")
md5sums=('SKIP')
 
prepare() {
cd $srcdir/$pkgname
sed -i -e 's#/usr/local#/usr#' media/Doomseeker.desktop
}
 
build() {
cd $srcdir/$pkgname
# Strip references to build environment in RPATH.
cmake -DCMAKE_BUILD_TYPE=Release \
-DCMAKE_INSTALL_PREFIX:PATH=/usr \
-DCMAKE_SKIP_RPATH:BOOL=true .
make
}
 
package() {
cd $srcdir/$pkgname
make DESTDIR=$pkgdir install
}

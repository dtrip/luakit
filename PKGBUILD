# This is an example PKGBUILD file. Use this as a start to creating your own,
# and remove these comments. For more information, see 'man PKGBUILD'.
# NOTE: Please fill out the license field for your package! If it is unknown,
# then please put 'unknown'.

# Maintainer: Dtrip <d@nrx.co>
pkgname=luakit
pkgver() {
  cd "$pkgname"
  git describe --long --tags| sed 's/\([^-]*-g\)/r\1/;s/-/./g'
}
pkgrel=1
epoch=
pkgdesc="Minimal webbrowser based on Lua"
arch=('i386' 'amd64' 'x86_64')
url=""
license=('GPL')
groups=()
depends=('gtk3'  'webkit2gtk' 'luajit' 'lua' 'sqlite3' 'lua-filesystem')
makedepends=('git')
checkdepends=()
optdepends=()
provides=('luakit')
conflicts=('luakit' 'luakit-git')
replaces=()
backup=()
options=()
# install=
changelog=
_src='/usr/local/src'
source=('luakit::git+https://github.com/dtrip/luakit.git#branch=develop')
# noextract=()
md5sums=(SKIP)
# validpgpkeys=()

prepare() {
	cd "$pkgname-$pkgver"
}

build() {
	cd "$pkgname-$pkgver"
    make USE_LUAJIT=1
}

check() {
	cd "$pkgname-$pkgver"
	make -k check
}

package() {
	cd "$pkgname-$pkgver"
    make install
}

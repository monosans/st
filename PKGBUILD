# Maintainer: monosans

pkgname=st-monosans-git
_pkgname=st
pkgver=0.8.4.r1152.18f0f20
pkgrel=1
pkgdesc="Simple (suckless) terminal with scrollback, ligatures and One Dark color scheme"
url='https://github.com/monosans/st'
arch=('i686' 'x86_64')
license=('MIT')
depends=('libxft' 'harfbuzz' 'ttf-jetbrains-mono')
optdepends=(
	'libxft-bgra: if st crashes when viewing emojis'
	'libxft-bgra-git: if st crashes when viewing emojis')
makedepends=('git' 'libxext' 'ncurses')
source=('git://github.com/monosans/st')
sha256sums=('SKIP')
provides=("${_pkgname}")
conflicts=("${_pkgname}")

pkgver() {
	cd "${_pkgname}"
	echo "$(awk '/^VERSION =/ {print $3}' config.mk)".r"$(git rev-list --count HEAD)"."$(git rev-parse --short HEAD)"
}

prepare() {
	cd "${_pkgname}"
	sed -i '/tic /d' Makefile
}

build() {
	cd "${_pkgname}"
	make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
	cd "${_pkgname}"
	make PREFIX=/usr DESTDIR="${pkgdir}" install
	install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
	install -Dm644 README.md "${pkgdir}/usr/share/doc/${pkgname}/README.md"
}
# vim:set ts=4 sw=4 noet:

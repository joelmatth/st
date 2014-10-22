# Contributor: Patrick Jackson <PatrickSJackson gmail com>
# Maintainer: Christoph Vigano <mail@cvigano.de>
# Maintainer: Mikhail Burakov <mikhail.burakov gmail com>
# Maintainer: Joel Matthews <joelmatth gmail com>

pkgname=st-solarized-inconsolata-dz-powerline-aa
appname='st'
conflicts=(${appname})
provides=(${appname})
pkgver=0.5
pkgrel=0
pkgdesc='A simple virtual terminal emulator for X. Patched for solarized
colorscheme and Inconsolata-dz for Powerline font with anti-aliasing.'
arch=('i686' 'x86_64')
license=('MIT')
depends=('libxext' 'libxft')
makedepends=('ncurses')
url="http://st.suckless.org"

source=(http://dl.suckless.org/st/$appname-$pkgver.tar.gz
        http://st.suckless.org/patches/st-0.5-no-bold-colors.diff
        http://st.suckless.org/patches/st-solarized-dark.diff
        https://raw.githubusercontent.com/joelmatth/st/master/st-inconsolata-dz-for-powerline-aa.diff)

md5sums=('4f8ae2737120a8cba34b23c6020fe51e'
         '18c28fc0ff19de6c2e4a58a711c91b15'
         'b4fd6228e0009c448194b6a637d86352'
         'b5fe613eb22b2d6e95bf3c8ef03220dc')

build() {
  cd $srcdir/$appname-$pkgver
  patch -i $srcdir/st-0.5-no-bold-colors.diff
  patch -i $srcdir/st-solarized-dark.diff
  patch -i $srcdir/st-inconsolata-dz-for-powerline-aa.diff
    make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
  cd $srcdir/$appname-$pkgver
  make PREFIX=/usr DESTDIR="$pkgdir" TERMINFO="$pkgdir/usr/share/terminfo" install
    install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$appname/LICENSE"
    install -Dm644 README "$pkgdir/usr/share/doc/$appname/README"
}

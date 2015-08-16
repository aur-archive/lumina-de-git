# Maintajiner: Chad "crossroads1112" Sharp <crossroads1112@riseup.net>
# Contributor: Josip Ponjavic <josipponjavic at gmail dot com>
pkgname=lumina-de-git
pkgver=r259.2ae4828
pkgrel=4
pkgdesc="A Lightweight QT5 Desktop for FreeBSD"
arch=('x86_64' 'i686')
url="https://github.com/pcbsd/lumina"
license=('BSD')
depends=('qt5-base' 'qt5-svg' 'qt5-multimedia' 'qt5-x11extras' 'fluxbox' 'oxygen' 'oxygen-icons' 'xscreensaver' 'desktop-file-utils')
optdepends=('xorg-xbacklight: required for changing screen brightness' 'alsa-utils: required for adjusting audio volume' 'acpi: required for monitoring battery life' 'numlockx: required for changign state of numlock at login' 'pavucontrol: required for detatched audio mixer')
makedepends=('git' 'qt5-tools')
conflicts=("${pkgname%-*}")
provides=("${pkgname%-*}")
install="${pkgname%-*}.install"
source=(git+https://github.com/pcbsd/lumina.git)
md5sums=(SKIP)


build(){
    cd $srcdir/lumina
    qmake PREFIX="/usr" QT5LIBDIR=/usr/lib/qt
    make
}

package() {
    cd $srcdir/lumina
    make INSTALL_ROOT="${pkgdir}" install
    mv "${pkgdir}"/usr/etc "${pkgdir}"/etc
    sed 's\usr/local/\usr/\' -i "${pkgdir}"/usr/share/xsessions/Lumina-DE.desktop
}

pkgver() {
  cd "$srcdir/lumina"
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

# Maintainer: Klaas Boesche <aurkagebe youknowh.at gmail.com>
pkgname=passdmenu-git
pkgver=1.0.2.r0.gc2d64cc
pkgrel=1
pkgdesc="A dmenu frontend to pass with clipboard and autotype functionality for user and password."
arch=(any)
url="https://github.com/klaasb/passdmenu"
license=('custom')
provides=('passdmenu')
conflicts=('passdmenu')
depends=('python' 'xclip' 'dmenu')
optdepends=('xdotool: autotype functionality')
makedepends=('git')
source=(${pkgname}::git+https://github.com/klaasb/passdmenu)
md5sums=('SKIP')

pkgver() {
  cd "${srcdir}/${pkgname}"
  ( set -o pipefail
    # Only uses annotated tags to derive a version number,
    # add --tags to use un-annotated tags as well
    git describe --long | sed 's/^v//' | sed -r 's/([^-]*-g)/r\1/;s/-/./g' ||
      printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
  )
}

build() {
  cd "${srcdir}/${pkgname}"
}

package() {
  cd "${srcdir}/${pkgname}"
  install -D -m755 passdmenu.py "${pkgdir}/usr/bin/passdmenu"
  install -D -m644 LICENSE.txt "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}

# vim:set ts=2 sw=2 et:

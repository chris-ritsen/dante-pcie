# Maintainer: Chris Ritsen <s00pcan [at] gmail [dot] com>

_pkgbase=dante-pcie
pkgname=digigram-lx-dante
pkgver=1.2.4rc03
pkgrel=1
pkgdesc="Digigram LX-DANTE Audio card (DKMS)"
arch=('i686' 'x86_64')
depends=('dkms')
conflicts=("${_pkgbase}")
install=${pkgname}.install
source=('dante-pcie-1.2.4.3.tgz'
        'dkms.conf')
md5sums=('a2d3c3d9534bdae70e02da19f3781c2d'
         'ec93e5c639a3365cec28fa896d5347ba')

build() {
  cd ${_pkgbase}-${pkgver}/kmod
  make
}

package() {
  # Copy dkms.conf
  install -Dm644 dkms.conf "${pkgdir}"/usr/src/${_pkgbase}-${pkgver}/dkms.conf

  # Set name and version
  sed -e "s/@_PKGBASE@/${_pkgbase}/" \
      -e "s/@PKGVER@/${pkgver}/" \
      -i "${pkgdir}"/usr/src/${_pkgbase}-${pkgver}/dkms.conf

  # Copy sources (including Makefile)
  cp -r ${_pkgbase}-${pkgver}/kmod/* "${pkgdir}"/usr/src/${_pkgbase}-${pkgver}/
}

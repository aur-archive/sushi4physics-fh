# Maintainer: Gustavo Castro << gustawho [at] gmail [dot] com >>
pkgname=sushi4physics-fh
_srcname=SusHi
pkgver=1.4.1
pkgrel=2
pkgdesc="Higgs production in the MSSM (FeynHiggs support)"
url="http://sushi.hepforge.org/"
arch=('x86_64')
license=('GPLv2')
depends=('lhapdf' 'feynhiggs')
makedepends=('gcc-fortran')
provides=('sushi4physics')
conflicts=('sushi4physics-2hdmc' 'sushi4physics' 'sushi4physics-hb')
source=("http://www.hepforge.org/archive/sushi/${_srcname}-${pkgver}.tar.gz"
        "feynhiggs.patch")
sha512sums=('3033c35551fc6ba50afef00cf7facccbae7c82b63f90df293167e7318e35576ef6033b94b68ce6330d43b4c61416e5d5589a118c6b7389cf2ba96c0148e0c5ff'
            '8643a35fc09a4a8694b0c9389fd9fcb0cba519e65b86ab34a738313ab481f1ab2d069e6f6f677fb2013305dfa65353cb9505cc1e9ccb2996f51adaa84b09f182')

build() {
  patch "${srcdir}/${_srcname}-${pkgver}/Makefile" < "${srcdir}/feynhiggs.patch"
  cd "${srcdir}/${_srcname}-${pkgver}"
  ./configure --prefix=/usr
  make predef=FH
}

package() {
  mkdir -p "${pkgdir}/usr/bin" "${pkgdir}/usr/lib"
  cd "${srcdir}/${_srcname}-${pkgver}"
  install -m755 bin/sushi.FH "${pkgdir}/usr/bin/sushi.FH"
  install -m755 lib/libshare.a "${pkgdir}/usr/lib/libshare.a"
  install -m755 lib/libsushiFH.a "${pkgdir}/usr/lib/libsushiFH.a"
  ln -s "${pkgdir}/usr/bin/sushi.FH" "${pkgdir}/usr/bin/sushi"
  ln -s "${pkgdir}/usr/lib/libsushiFH.a" "${pkgdir}/usr/lib/libsushi.a"
}

# vim:set ts=2 sw=2 et:

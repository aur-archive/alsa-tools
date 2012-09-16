# $Id: PKGBUILD 62751 2012-01-25 20:11:55Z seblu $
#Maintainer: Sebastien Luttringer <seblu+arch@seblu.net>
#Contributor: Jochen Immend�rfer <jochen dot immendoerfer at gmail dot com>

pkgname=alsa-tools
pkgver=1.0.25
pkgrel=1
pkgdesc='ALSA tools package'
arch=('i686' 'x86_64')
url='http://alsa-project.org/'
license=('GPL2')
depends=('fltk' 'alsa-lib' 'gtk2')
options=('!libtool')
source=("ftp://ftp.alsa-project.org/pub/tools/$pkgname-$pkgver.tar.bz2")
md5sums=('57bfec98a814d12e0f7ab379aaeccd87')

build() {
  for f in $(find "$srcdir/$pkgname-$pkgver" -type f -name configure ); do
    [[ -x $f ]] || continue
    cd "${f%/*}"
    [[ qlo10k1 = ${PWD##*/} ]] && continue
    [[ hwmixvolume = ${PWD##*/} ]] && continue
    msg2 "Building ${PWD##*/}"
    ./configure --prefix=/usr --x-libraries=/usr/lib
    make
  done
}

package() {
  for f in $(find "$srcdir/$pkgname-$pkgver" -type f -name configure ); do
    [[ -x $f ]] || continue
    cd "${f%/*}"
    [[ qlo10k1 = ${PWD##*/} ]] && continue
    [[ hwmixvolume = ${PWD##*/} ]] && continue
    msg2 "Installing ${PWD##*/}"
    make "DESTDIR=$pkgdir" install
  done
}

# vim:set ts=2 sw=2 ft=sh et:

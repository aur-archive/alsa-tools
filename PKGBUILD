#Maintainer: Sebastien Luttringer <seblu+arch@seblu.net>
#Contributor: Jochen Immend�rfer <jochen dot immendoerfer at gmail dot com>

pkgname=alsa-tools
pkgver=1.0.24.1
pkgrel=1
pkgdesc='ALSA tools package'
arch=('i686' 'x86_64')
url='http://alsa-project.org/'
license=('GPL2')
depends=('fltk' 'alsa-lib' 'gtk2' 'pygtk')
options=('!libtool')
source=("ftp://ftp.alsa-project.org/pub/tools/$pkgname-$pkgver.tar.bz2")
md5sums=('08fe93a12006093e590d7ecc02b119dd')

build() {
  for f in $(find "$srcdir/$pkgname-$pkgver" -type f -name configure ); do
    [[ -x $f ]] || continue
    cd "${f%/*}"
    [[ qlo10k1 = ${PWD##*/} ]] && continue
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
    msg2 "Installing ${PWD##*/}"
    make "DESTDIR=$pkgdir" install
  done
}

# vim:set ts=2 sw=2 ft=sh et:

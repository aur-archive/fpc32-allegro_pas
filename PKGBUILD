pkgname=fpc32-allegro_pas
pkgver=4.4.3
pkgrel=5
pkgdesc="Allegro.pas is a wrapper to use Allegro with Pascal compilers (multilib)"
url="http://allegro-pas.sourceforge.net"
license=("unknown")
arch=(x86_64)
depends=(fpc-multilib)
makedepends=(fpc-multilib)
optdepends=("lib32-allegro4: Allegro shared library")
source=("http://downloads.sourceforge.net/allegro-pas/allegro.pas-$pkgver-src-pas.tar.bz2")
md5sums=('d289929fb13320bdca0fdc3a0944adf8')
_fpcvers=`fpc -iV`

build() {
  cd "${srcdir}/allegro.pas/lib"
  for file in `ls *.pas`
  do
    ppcross386 -Tlinux $file
  done
}

package() {
  cd "${srcdir}/allegro.pas/lib"
  find . -name '*.o' -o -name '*.ppu' -o -name '*.rst' -o -name '*.a' -o -name '*.compiled' |
    xargs -rtl1 -I {} install -Dm644 {} "$pkgdir/usr/lib/fpc/$_fpcver/units/i386-linux/"{}
}
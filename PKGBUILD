pkgname=jed
pkgver=0.99.19
_pkgver=0.99-19
pkgrel=1
pkgdesc="JED is a text editor that makes extensive use of the S-Lang library."
arch=('x86_64')
url="http://www.jedsoft.org/jed"
license=('GPL')
depends=('gpm' 'slang' 'libxft')
makedepends=('libxext' 'libxt')
source=("ftp://space.mit.edu/pub/davis/${pkgname}/v0.99/${pkgname}-${_pkgver}.tar.bz2"
"$pkgname.install")
md5sums=('c9b2f58a3defc6f61faa1ce7d6d629ea'
         'dd95161e54793bc082fa881d67886e21')
install="$pkgname.install"


build() {
  cd "${srcdir}/${pkgname}-${_pkgver}"

  ./configure --prefix=/usr JED_ROOT=/usr/share/jed

  sed \
    -e "s|\(^all.*\)|\1 xjed rgrep|" \
    -e "s|..DEST.*doc|${pkgdir}/usr/share/doc/${pkgname}|g" \
	-i src/Makefile

  make
}

package() {
  cd "${srcdir}/${pkgname}-${_pkgver}"

  make DESTDIR="${pkgdir}" install

  # Install rgrep
  install -Dm755 src/objs/rgrep "$pkgdir/usr/bin"
}

#Mantainer: Filippo Squillace <feel.squally@gmail.com>
pkgname=scrssi
pkgver=0.1.3
pkgrel=1
author=fsquillace
pkgdesc="Screen+irssi daemon"
arch=(any)
url="https://github.com/$author/$package"
license=('GPLv2')
depends=('screen' 'irssi')
makedepends=('asciidoc' 'xmlto')
provides=()
options=()
source=(https://github.com/$author/$pkgname/tarball/$pkgver)
install=$pkgname.install
md5sums=(0338c84f5cd09e453e7438188bc22d61)

build() {
  cd $srcdir/$author-$pkgname-*

  echo "Moving the licence into /usr/share/licenses/${pkgname} ..."
  mkdir -p "$pkgdir/usr/share/licenses/${pkgname}"
  mv -f "LICENSE" $pkgdir/usr/share/licenses/${pkgname}/

  echo "Copying the $pkgname directory into the pkg directory ..."
  mkdir -p "$pkgdir/etc"
  cp -rf "etc" "$pkgdir"

  # Generate manual page
  echo "Generating manual page..."
  /usr/bin/asciidoc -d manpage -b docbook -o ${pkgname}.1.xml README
  /usr/bin/xmlto man ${pkgname}.1.xml # Add --skip-validation if it doesn't work
  /bin/gzip ${pkgname}.1
  mkdir -p "${pkgdir}/usr/share/man/man1/"
  cp ${pkgname}.1.gz ${pkgdir}/usr/share/man/man1/
}

# vim:set ts=2 sw=2 et:

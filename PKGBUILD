pkgname=smath
pkgver=0.1
pkgrel=1
pkgdesc="math program"
arch=('any')
url="https://smath.com/"
license=('MIT')
sha256sums=('9bb7ffe65dc288b7f8746b428df721c90349e6835cd23cdd6b50873b8e7938d8')
source=("./smath.tar.gz")

package() {
  cd "$srcdir"
  # install program
  install -m755 -d "$pkgdir"/opt/$pkgname/{book,examples,lang,entries,plugins,snippets}
  install -m644 -t "$pkgdir"/opt/$pkgname/book book/*
  install -m644 -t "$pkgdir"/opt/$pkgname/examples examples/*
  install -m644 -t "$pkgdir"/opt/$pkgname/lang lang/*
  install -m644 -t "$pkgdir"/opt/$pkgname *.{dll,exe}
  install -m644 -t "$pkgdir"/opt/$pkgname/entries entries/*
  install -m644 -t "$pkgdir"/opt/$pkgname/plugins plugins/*
  install -m644 -t "$pkgdir"/opt/$pkgname/snippets snippets/*

  # create settings file
  touch "$pkgdir"/opt/$pkgname/settings.inf
  chmod 664 "$pkgdir"/opt/$pkgname/settings.inf

  echo "#!/bin/sh
  cd /opt/smath
  mono SMathStudio_Desktop.exe \"$@\"
  " > ../$pkgname.sh

  # install launcher
  install -Dm755 ../$pkgname.sh "$pkgdir"/usr/bin/$pkgname
  install -Dm644 "${startdir}/smath.desktop" "${pkgdir}/usr/share/applications/smath.desktop"
  install -Dm644 "${startdir}/SMathStudioLogo256.png" "${pkgdir}/usr/share/pixmaps/smath.png"

}

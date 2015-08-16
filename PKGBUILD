# Maintainer: Sarkasper <echo a2FzcGVyLm1lbnRlbkBnbXguY29tCg== | base64 -d>
# Contributor: Jelle van der Waa <jelle@vdwaa nl>

pkgname=hunspell-nl
pkgver=2.10g
pkgrel=1
pkgdesc="Dutch hunspell dictionaries"
arch=('any')
url="http://www.opentaal.org/"
license=('BSD' 'custom:Creative Commons, Attribution 3.0 Unported')
depends=('hunspell')
optdepends=('hunspell:  the spell checking libraries and apps')
makedepends=('unzip')
source=('http://opentaal.org/bestanden/license_result/20-woordenlijst-v-210g-voor-openofficeorg-3?bid=20&agree=1')
md5sums=('3c96686c2555e3ae23b5de06ba08631b')

package() {
  cd "${srcdir}"
  install -dm755 "${pkgdir}/usr/share/hunspell"
  install -m644 nl_NL.dic "${pkgdir}/usr/share/hunspell/nl_NL.dic"
  install -m644 nl_NL.aff "${pkgdir}/usr/share/hunspell/nl_NL.aff"

  pushd "${pkgdir}/usr/share/hunspell/"
  nl_NL_aliases="nl_AW nl_BE"
  for lang in $nl_NL_aliases; do
      ln -s nl_NL.aff $lang.aff
      ln -s nl_NL.dic $lang.dic
  done
  popd

  # the symlinks
  install -dm755 "${pkgdir}/usr/share/myspell/dicts"
  pushd "${pkgdir}/usr/share/myspell/dicts"
    for file in ${pkgdir}/usr/share/hunspell/*; do
      ln -sv /usr/share/hunspell/$(basename $file) .
    done
  popd

  # docs
  install -dm755 "${pkgdir}/usr/share/doc/${pkgname}"
  install -m644 README_nl_NL.txt "${pkgdir}/usr/share/doc/${pkgname}"

  # licences
  install -D -m644 license_en_EN.txt $pkgdir/usr/share/licenses/$pkgname/license_en_EN.txt
}

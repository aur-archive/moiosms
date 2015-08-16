# Contributor: Andrea Scarpino <andrea@archlinux.org>
# Contributor: Fabrizio Antonangeli <fabrizio.antonangeli@gmail.com>

pkgname=moiosms
pkgver=2.18
pkgrel=6
pkgdesc="A program to send SMS via web"
url="http://www.moioli.net/sms"
license=('GPL2')
arch=('any')
depends=('python-pycurl')
optdepends=('wxpython: for GUI frontend'
	'gocr: for automatic captcha recognition'
	'graphicsmagick: for automatic captcha recognition'
	'ocrad: for automatic captcha recognition')
source=("http://www.moioli.net/files/MoioSMS${pkgver}-src.zip"
	'moiosms.desktop')
md5sums=('8dee97d8c0bef741f2bdd3d104b1899f'
         '0ed8b3ebed52d45e08504290edeedb86')

package() {
  cd ${srcdir}/MoioSMS-${pkgver}

  sed -i -e "s|#![ ]*/usr/bin/python$|#!/usr/bin/python2|" \
         -e "s|#![ ]*/usr/bin/python2.4$|#!/usr/bin/python2|" \
    $(find . -name '*.py')

  install -Dm755 sms.py \
    ${pkgdir}/usr/share/moiosms/sms.py
  install -d ${pkgdir}/usr/lib/python2.7
  cp -rf moio ${pkgdir}/usr/lib/python2.7/

  # install icon and desktop file
  install -Dm644 icon.xpm \
    ${pkgdir}/usr/share/pixmaps/moiosms.xpm
  install -Dm644 ${srcdir}/moiosms.desktop \
    ${pkgdir}/usr/share/applications/moiosms.desktop

  # symlinks to sms
  install -d ${pkgdir}/usr/bin/
  ln -sf /usr/share/moiosms/sms.py ${pkgdir}/usr/bin/moiosms
  ln -sf /usr/share/moiosms/sms.py ${pkgdir}/usr/bin/sms
}

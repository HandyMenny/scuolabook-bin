# Maintainer: HandyMenny <handymenny[at]outlook[dot]com>
pkgname=scuolabook-bin
pkgver=3.1
pkgrel=2
pkgdesc="Scuolabook is an application that allow you to read and study the textbooks buyed on Scuolabook.it"
arch=('i686' 'x86_64')
license=('custom:"Copyright: 2013 Scuolabook <info@scuolabook.it>"')
s_pkgname=scuolabook
depends=( 'alsa-lib' 'sqlite' 'gtk2' 'openssl' 'gstreamer0.10-ugly-plugins' 'gstreamer0.10-ffmpeg')
url="http://scuolabook.it"

if [ "${CARCH}" = "x86_64" ]; then
  sha256sums=('d514a12d3efd116292a100c2035e92dd7f41c868982945e7ebac4138bb971464')
  _carch=_amd64
elif [ "${CARCH}" = "i686" ]; then
  sha256sums=('c58a39c419a73909ad87c036175de861814f041e5dc0881b1c0d37231c8da55d')
  _carch=_i386
fi

source=("http://s3.amazonaws.com/scuolabook_support/${s_pkgname}_${pkgver}${_carch}.deb"
		"scuolabook")
sha256sums+=( '624f0b2fb0e3292cf1fb7f82a17d0c5a85c05a86fa187cba073e8557bff9dffa')

package() {
	tar -zxf data.tar.gz -C "${pkgdir}"	
	sed -e 7c'Categories=Viewer;Literature;Education' -e 6a'Comment=Read and study the textbooks buyed on Scuolabook.it' -e s#'opt'#'usr/share'#g ${pkgdir}/usr/share/applications/${s_pkgname}.desktop > ${pkgdir}/usr/share/applications/${pkgname}.desktop
	rm ${pkgdir}/usr/share/applications/${s_pkgname}.desktop
	install -d "${pkgdir}/usr/share/"
	mv "${pkgdir}/opt/scuolabook" "${pkgdir}/usr/share/"
	rm -r "${pkgdir}/opt"
	install -Dm644 "${pkgdir}/usr/share/doc/${s_pkgname}/copyright" "${pkgdir}/usr/share/licenses/${s_pkgname}/copyright"
	install -Dm755 "${srcdir}/scuolabook" "${pkgdir}/usr/bin/scuolabook"
}

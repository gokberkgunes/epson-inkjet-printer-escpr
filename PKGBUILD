pkgname=epson-inkjet-printer-escpr
pkgver=1.8.5
pkgrel=2
pkgdesc='Epson Inkjet Printer Driver (ESC/P-R) for Linux'
arch=('x86_64' 'aarch64')
url='http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX'
license=('GPL2')
depends=('cups' 'ghostscript')
source=("git+https://github.com/gokberkgunes/epson-inkjet-printer-escpr#branch=source")
sha512sums=(SKIP)

prepare()
{
	cd $pkgname
	autoreconf -vif
}

build()
{
	cd $pkgname
	CFLAGS="${CFLAGS} -Wno-implicit-function-declaration"

	./configure \
	--prefix=/usr \
	--with-cupsfilterdir=/usr/lib/cups/filter \
	--with-cupsppddir=/usr/share/ppd

	make
}

package()
{
	cd $pkgname
	make DESTDIR="$pkgdir" install
}

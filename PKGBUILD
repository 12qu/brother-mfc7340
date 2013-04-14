pkgname=brother-mfc7340
_printername=MFC7340
pkgver=2.0.2
pkgrel=1
pkgdesc="CUPS and LPR driver for Brother MFC7340 printer"
arch=('i686' 'x86_64')
license=('custom:Brother Industries')
depends=('cups' 'tcsh')
if test "$CARCH" == x86_64; then
  depends+=('lib32-libcups')
fi
makedepends=('rpmextract')
url="http://solutions.brother.com/linux/en_us/index.html"
source=(http://www.brother.com/pub/bsc/linux/dlf/cupswrapper${_printername}-$pkgver-${pkgrel}.i386.rpm \
	http://www.brother.com/pub/bsc/linux/dlf/brmfc7340lpr-$pkgver-${pkgrel}.i386.rpm)
md5sums=('c354ffc0498bf56687d7300c28e47887'
	 'fe19d8aca8579218ef61514884d45f3e')
install=mfc7340.install

build() {
    rpmextract.sh "$srcdir"/*.rpm
    sed -i -e 's|/etc/init.d|/etc/rc.d|' "$srcdir"/usr/local/Brother/cupswrapper/cupswrapperMFC7340-2.0.2
}

package() {
    cp -R "$srcdir"/{usr,var} "$pkgdir"

    # Change mode to avoid warning on reinstall
    install -d -m777 "$pkgdir"/usr/local/Brother/inf/
}

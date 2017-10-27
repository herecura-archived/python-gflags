# $Id$
# Maintainer: BlackEagle < ike DOT devolder AT gmail DOT com >
pkgbase=python-gflags
pkgname=('python-gflags' 'python2-gflags')
pkgver=3.1.2
pkgrel=1
pkgdesc="Commandline flags module for Python"
arch=('any')
url="https://github.com/google/python-gflags"
license=('BSD')
makedepends=('python2-setuptools' 'python-setuptools')
source=("$pkgbase-$pkgver.tar.gz::https://github.com/google/$pkgbase/archive/$pkgver.tar.gz")
sha256sums=('f1692c79ccf4a55d13895dcd195f0db1ebd55c71024b431ec953703b38d73f96')

prepare() {
    cp -a "$pkgbase-$pkgver" "${pkgbase/python/python2}-$pkgver"
}

build() {
    cd "$srcdir/$pkgbase-$pkgver"
	python setup.py build

	cd "$srcdir/${pkgbase/python/python2}-$pkgver"
	python2 setup.py build
}

package_python-gflags() {
    depends=('python')
	cd "$pkgbase-$pkgver"
	python setup.py install --root=${pkgdir}
    chmod +x "$pkgdir/usr/bin/gflags2man.py"
	#chmod +r ${pkgdir}/* -R
	#install -dm755 ${pkgdir}/usr/share/licenses/${pkgname}
	install -Dm644 AUTHORS "$pkgdir/usr/share/licenses/$pkgbase/AUTHORS"
	install -Dm644 COPYING "$pkgdir/usr/share/licenses/$pkgbase/COPYING"
}

package_python2-gflags() {
    depends=('python2')
	cd ${pkgbase/python/python2}-${pkgver}
    find -name "*.py" -exec sed -e 's/env python/&2/' -i {} \;
	python2 setup.py install --root=${pkgdir}
    mv "$pkgdir/usr/bin/gflags2man.py" "$pkgdir/usr/bin/gflags2man.py2"
    chmod +x "$pkgdir/usr/bin/gflags2man.py2"
	#chmod +r ${pkgdir}/* -R
	#install -dm755 ${pkgdir}/usr/share/licenses/${pkgname}
	install -Dm644 AUTHORS "$pkgdir/usr/share/licenses/${pkgbase/python/python2}/AUTHORS"
	install -Dm644 COPYING "$pkgdir/usr/share/licenses/${pkgbase/python/python2}/COPYING"
}


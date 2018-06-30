# Maintainer: Felix Yan <felixonmars@archlinux.org>

pkgbase=python-priority
pkgname=('python-priority' 'python2-priority')
pkgver=1.3.0
pkgrel=2
pkgdesc='A pure-Python implementation of the HTTP/2 priority tree'
arch=('any')
license=('MIT')
url='https://github.com/python-hyper/priority'
makedepends=('python-setuptools' 'python2-setuptools')
checkdepends=('python-pytest-runner' 'python2-pytest-runner' 'python-hypothesis'
              'python2-hypothesis')
source=("$pkgbase-$pkgver.tar.gz::https://github.com/python-hyper/priority/archive/v$pkgver.tar.gz")
sha512sums=('bd60db8e1f524a2c445227576d53c70dbf5764e9ecb0e75d320e3652941f9e915f9d130815a781a8d4e50c4c3f68e05c9458225926e80d588e210037a1c6ed5f')

prepare() {
  cp -a priority-$pkgver{,-py2}
}

build() {
  cd "$srcdir"/priority-$pkgver
  python setup.py build

  cd "$srcdir"/priority-$pkgver-py2
  python2 setup.py build
}

check() {
  cd "$srcdir"/priority-$pkgver
  python setup.py pytest

  cd "$srcdir"/priority-$pkgver-py2
  python2 setup.py pytest
}

package_python-priority() {
  depends=('python')

  cd priority-$pkgver
  python setup.py install --root="$pkgdir" --optimize=1
  install -D -m644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}

package_python2-priority() {
  depends=('python2')

  cd priority-$pkgver-py2
  python2 setup.py install --root="$pkgdir" --optimize=1
  install -D -m644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}

# vim:set ts=2 sw=2 et:

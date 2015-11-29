# Maintainer: Daniel Isenmann <daniel@archlinux.org>
# Maintainer: Sergej Pupykin <sergej@aur.archlinux.org>
# Maintainer: Douglas Soares de Andrade <dsandrade@gmail.com>

pkgname=('python-urwid' 'python2-urwid')
pkgver=1.3.1
pkgrel=2
pkgdesc="Curses-based user interface library."
license=('LGPL')
arch=('i686' 'x86_64')
makedepends=('python2-setuptools' 'python-setuptools')
url="http://excess.org/urwid/"
source=(https://pypi.python.org/packages/source/u/urwid/urwid-$pkgver.tar.gz)
md5sums=('2e1a005cb31368fe21bfeba2d6ad5a5c')

build() {
  cp -r urwid-$pkgver python2-urwid-$pkgver

  cd "$srcdir/urwid-$pkgver"
  python setup.py build

  cd "$srcdir/python2-urwid-$pkgver"
  sed -i 's#bin/python#bin/python2#' urwid/*.py
  
  python2 setup.py build
}

package_python-urwid() {
  depends=('python')

  cd "$srcdir/urwid-$pkgver"
  python setup.py install --prefix=/usr --root="$pkgdir" --optimize=1
}

package_python2-urwid() {
  depends=('python2')
 
  cd "$srcdir/python2-urwid-$pkgver"
  python2 setup.py install --prefix=/usr --root="$pkgdir" --optimize=1
}

# Maintainer: Levente Polyak <anthraxx[at]archlinux[dot]org>
# Contributor: Daniel Isenmann <daniel@archlinux.org>
# Contributor: Sergej Pupykin <sergej@aur.archlinux.org>
# Contributor: Douglas Soares de Andrade <dsandrade@gmail.com>

_name=urwid
pkgname=python-urwid
pkgver=2.6.15
pkgrel=1
pkgdesc='Curses-based user interface library'
url='https://urwid.org/'
arch=('x86_64')
license=('LGPL-2.1-only')
depends=(
  'glibc'
  'python'
  'python-typing_extensions'
  'python-wcwidth'
)
makedepends=(
  'python-build'
  'python-installer'
  'python-setuptools'
  'python-setuptools-scm'
  'python-wheel'
)
checkdepends=(
  'python-pytest'
  'python-pytest-cov'
  'python-twisted'
  'python-tornado'
  'python-trio'
  'python-pyzmq'
  'python-gobject'
)
optdepends=(
  'python-gobject: for gobject integration'
  'python-pyserial: for LCD and serial integration'
  'python-pyzmq: for zmq integration'
  'python-tornado: for tornado integration'
  'python-trio: for trio integration'
  'python-twisted: for twisted integration'
)
source=(
  $_name-$pkgver.tar.gz::https://github.com/urwid/urwid/archive/refs/tags/$pkgver.tar.gz
)
sha256sums=('99b36c3fcc09ab0b854ea47b60d9f99169b16cb26308f5c264a7c72373be6990')
sha512sums=('03d6de4d406da2b7ebd65f1ea51b915e13138da68bff9f80eb3498437d0e76a09000b441054624b1b8d1d38de89469428faae239314a41c7f143f85e5ab8648d')

build() {
  cd $_name-$pkgver
  SETUPTOOLS_SCM_PRETEND_VERSION=$pkgver python -m build --wheel --no-isolation
}

check() {
  cd $_name-$pkgver
  pytest -vv tests
}

package() {
  cd $_name-$pkgver
  python -m installer --destdir="$pkgdir" dist/*.whl
}

# vim: ts=2 sw=2 et:

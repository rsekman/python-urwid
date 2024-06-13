# Maintainer: Levente Polyak <anthraxx[at]archlinux[dot]org>
# Contributor: Daniel Isenmann <daniel@archlinux.org>
# Contributor: Sergej Pupykin <sergej@aur.archlinux.org>
# Contributor: Douglas Soares de Andrade <dsandrade@gmail.com>

_name=urwid
pkgname=python-urwid
pkgver=2.6.14
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
sha256sums=('86cab302ac032074355dc82c9d5ee5e7112ea90dbbcd9be4444f6f765f5a0574')
sha512sums=('929ee5c477cb6421f3e37c184ec3d4d6f386e3e976f7e52ee461d914f0628e8f4878e6345277ac7071bd84aa9c6b6601d7df66cc1d7b9cf91fc8a0d46568a31d')

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

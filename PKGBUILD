# Maintainer: Levente Polyak <anthraxx[at]archlinux[dot]org>
# Contributor: Daniel Isenmann <daniel@archlinux.org>
# Contributor: Sergej Pupykin <sergej@aur.archlinux.org>
# Contributor: Douglas Soares de Andrade <dsandrade@gmail.com>

_name=urwid
pkgname=python-urwid
pkgver=2.6.1
pkgrel=1
pkgdesc='Curses-based user interface library'
url='https://urwid.org/'
arch=('x86_64')
license=('LGPL')
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
  'python-exceptiongroup: for trio integration'
  'python-pyzmq: for zmq integration'
  'python-tornado: for tornado integration'
  'python-trio: for trio integration'
  'python-twisted: for twisted integration'
)
source=(
  $_name-$pkgver.tar.gz::https://github.com/urwid/urwid/archive/refs/tags/$pkgver.tar.gz
)
sha256sums=('0e54b1c459ccac1dc48bb98ae9e3fda160ca1239ee3a78fd70ad0df2987fcf08')
sha512sums=('6c02ee2fad986ca4e82e4fc89dbc1ba55c7dfc5d73acc0da5bf5dd1b1a7927b5d9574a7743c342fb67fae79d6e1be9294ccfe728db856ca74a6277d0771963e5')

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

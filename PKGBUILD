# Maintainer: Alexander Rødseth <rodseth@gmail.com>
# Contributor: lang2 <wenzhi.liang@gmail.com>

pkgname=python-pycparser-hg
pkgver=20130613
pkgrel=1
pkgdesc='C parser and AST generator written in Python'
url='https://bitbucket.org/eliben/pycparser'
makedepends=('mercurial')
depends=('python' 'python-ply')
conflicts=('pycparser' 'python-pycparser')
replaces=('pycparser' 'python-pycparser')
arch=('x86_64' 'i686')
license=('BSD')
source=('pycparser::git://github.com/eliben/pycparser.git')
sha256sums=('SKIP')

pkgver() {
  cd pycparser

  git log -n1 --format="%ci" | awk '{print $1}' | sed s/-//g
}

prepare() {
  cd pycparser

  # generate lextab.py and yacctab.py
  python -c 'import pycparser; pycparser.CParser()'
  mv lextab.py yacctab.py pycparser
}

build() {
  cd pycparser

  python setup.py build
}

package() {
  cd pycparser

  python setup.py install --root="$pkgdir" --optimize=1
  install -Dm644 LICENSE \
    "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

# vim:set ts=2 sw=2 et:

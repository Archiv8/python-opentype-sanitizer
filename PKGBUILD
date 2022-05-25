#!/bin/bash

# Created from the original PKGBUILD by Caleb Maclennan <caleb@alerque.com> and

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# ToDo: Add files: User documentation
# ToDo: Add files: Tooling
# FixMe: Namcap warnings and errors

# Maintainer: Ross Clark <https://github.com/Archiv8/python-pyclipper/discussions>
# Contributor: Ross Clark <https://github.com/Archiv8/python-pyclipper/discussions>

_langname="python"
_relname="opentype-sanitizer"

pkgname="${_langname}-${_relname}"
pkgver=8.1.4.post3
pkgrel=2
pkgdesc="Python wheels for the OpenType Sanitizer"
arch=(
  "any"
)
url="https://github.com/googlefonts/ots-python"
license=(
  "GPL3"
)
depends=(
  "ots"
  "python"
)
checkdepends=(
  "python-pytest"
  "woff2"
)
makedepends=(
  "python-setuptools-scm"
)
_tarname="${_relname}-${pkgver}"
source=(
  "https://files.pythonhosted.org/packages/source/${_relname::1}/${_relname}/${_tarname}.tar.gz"
  "system-ots-sanitize.patch"
)
sha512sums=(
  "935e28267064e89a10141dcf7f43e52164c339f2bf3e37ba04dbadc44fd1cae854fc9b13fe2d846a05c3f8b693ba3d7538db791155f9737e4e6af183af13e6d6"
  "0ee8498af814d30ae25d8bdb16f155cdd9062f792eac2a94c45d5872dad5650c939d77ea61390fd5ee7e5c7918872d0accc38376eab614dce704d1285c0c58f7"
)

prepare() {

  cd "${_tarname}"

  patch -p0 < "../system-ots-sanitize.patch"
}

build() {

  cd "${_tarname}"

  python setup.py build
}

check() {

  cd "${_tarname}"

  PYTHONPATH=src/python pytest
}

package() {

  cd "${_tarname}"

  python setup.py install --root="$pkgdir" --optimize=1 --skip-build
}

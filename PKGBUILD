# Maintainer: yaroslav <proninyaroslav@mail.ru>

pkgname=infer
pkgver=0.12.1
pkgrel=1
pkgdesc="Static Analyzer by Facebook"
arch=('x86_64')
url="https://github.com/facebook/infer"
license=('BSD')
depends=(
	'python2>=2.7'
	'java-environment'
	'cmake'
	'gcc>=4.7.2'
	'ocaml'
	'ocaml-ansiterminal>=0.7'
	'ocaml-atdgen>=1.6.0'
	'ocaml-cmdliner>=1.0.0'
	'ocaml-core'
	'ocaml-ctypes-git>=0.9.2'
	'ocaml-extlib-compat'
	'ocaml-javalib>=2.3.3'
	'ocaml-ounit=2.0.0'
	'ocaml-parmap>=1.0_rc8'
	'ocaml-ppx_deriving>=4.1'
	'ocaml-sawja>=1.5.2'
	'ocaml-xmlm>=1.2.0'
)
makedepends=(
	'ocaml-findlib'	
	'jbuilder>=1.0+beta11'
)
source=("https://github.com/facebook/infer/releases/download/v$pkgver/infer-linux64-v$pkgver.tar.xz")

build() {
	cd "$pkgdir/infer-linux64-v$pkgver"
	./build-infer.sh
}

package() {
    srcdir="${pkgname}"
    mkdir -p "${pkgdir}/usr/lib/${pkgname}" "${pkgdir}/usr/bin"
    cp -r "${srcdir}/${pkgname}" "${pkgdir}/usr/lib/${pkgname}"
    cp -r "${srcdir}/facebook-clang-plugins/" "${pkgdir}/usr/lib/${pkgname}"
    cat > "${pkgdir}/usr/bin/infer" <<EOF
#!/bin/bash
/usr/lib/infer/infer/bin/infer "\$@"
EOF
    chmod +x "${pkgdir}/usr/bin/infer"
}
md5sums=('5d33e43c1f516f02ab33c85e0ed418f9')

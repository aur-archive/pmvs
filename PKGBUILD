# Maintainer: Your Name Gunther Schulz < mail at guntherschulz.de >
pkgname=pmvs
pkgver=2
pkgrel=1
pkgdesc="Patch-based Multi-view Stereo Software"
arch=('i686' 'x86_64')
url="http://www.di.ens.fr/pmvs/"
license=('propriatary')
groups=()
#depends=( 'f2c' 'atlas-lapack')
depends=( 'f2c' 'lapack' 'boost')
makedepends=( )
optdepends=()
provides=()
conflicts=()
replaces=()
backup=()
options=()
install=
changelog=
source=("http://www.di.ens.fr/pmvs/${pkgname}-${pkgver}-fix0.tar.gz" "mylapack.o")
noextract=()
md5sums=('23eaae007ebbd39448c3039d4b8e4c7e'
         'a77ad8a8f447ff044e4db5a2147e781e')

build() {
        cd "${srcdir}/${pkgname}-${pkgver}/program/main"

        sed -i "s_YOURINCLUDEPATH =_YOURINCLUDEPATH = -I/usr/include_" Makefile
        sed -i "s_YOURLDLIBPATH =_YOURLDLIBPATH = -L/usr/lib_" Makefile
        make clean
        cp ../../../../mylapack.o ./mylapack.o
        make depend
        make
}

package() {
        cd "${srcdir}/${pkgname}-${pkgver}/program/main"
        install -Dm755 -d "$pkgdir"/opt/${pkgname}
        install -Dm644 -t "$pkgdir"/opt/${pkgname} *
}

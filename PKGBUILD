# Contributor: judd <jvinet@zeroflux.org>

pkgname=alsa-lib
pkgver=1.1.7
pkgrel=1
pkgdesc="An alternative implementation of Linux sound support"
arch=('x86_64')
url="http://www.alsa-project.org"
depends=('glibc')
optdepends=('python2: for python smixer plugin')
makedepends=('python2')
license=('LGPL')
source=(ftp://ftp.alsa-project.org/pub/lib/$pkgname-$pkgver.tar.bz2
		alsa-lib.patch)
sha256sums=('9d6000b882a3b2df56300521225d69717be6741b71269e488bb20a20783bdc09'
            '7437c5328043208c164b333f3a0a3b5eaba3798fbbcd1e29d973bf0face959d4')

prepare() {
	cd $pkgname-$pkgver
	patch -Np1 -i "${srcdir}/alsa-lib.patch"
}

build() {
  cd "$srcdir/$pkgname-$pkgver"
  ./configure --without-debug --prefix=/usr --with-pythonlibs="-lpthread -lm -ldl -lpython2.7" --with-pythonincludes=-I/usr/include/python2.7
  make
}

package() {
  cd "$srcdir/$pkgname-$pkgver"
  make DESTDIR="$pkgdir" install
}

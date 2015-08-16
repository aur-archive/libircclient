# Maintainer : SpepS <dreamspepser at yahoo dot it>
# Contributor: Marcel Wysocki <maci@satgnu.net>
# Contributor: coolkehon <coolkehon at g m a i l>

pkgname=libircclient
pkgver=1.3
pkgrel=5
pkgdesc="A small but powerful library, which implements client-server IRC protocol."
arch=('i686' 'x86_64')
url="http://libircclient.sf.net"
depends=('glibc')
license=("GPL2")
source=("http://downloads.sourceforge.net/sourceforge/$pkgname/$pkgname-$pkgver.tar.gz"
        "shared.patch")
md5sums=('b0e80d1d6b0c1cc61660fb9d2350b32d'
         'f2c350d140bd522990c15162645c72f0')

build() {
  cd "$srcdir/$pkgname-$pkgver"

  # add fPIC flag for x86_64
  [ "$CARCH" = x86_64 ] && export CFLAGS="$CFLAGS -fPIC"

  # shared and path patch
  patch -p1 -i ../shared.patch

  ./configure --prefix=/usr
  cd src && make CFLAGS="$CFLAGS"
}

package() {
  cd "$srcdir/$pkgname-$pkgver/src"

  make DESTDIR="$pkgdir/" install
}

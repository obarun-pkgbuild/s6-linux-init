# Maintainer: Eric Vidal <eric@obarun.org>

pkgname=s6-linux-init
pkgver=0.3.1.1
pkgrel=1
pkgdesc="Suite of tools to create an s6-based Linux init system"
arch=(x86_64)
url="http://skarnet.org/software/${pkgname}/"
license=('ISC')
depends=('skalibs' 'execline')
groups=(s6-suite)
conflicts=(s6-linux-init-git)
source=("$pkgname::git+git://git.skarnet.org/s6-linux-init#commit=$_commit")
_commit=7dacceb46ef058473a2cc00e4c49739e2c067cb7  # tag 0.3.1.1
sha256sums=('SKIP')
validpgpkeys=('6DD4217456569BA711566AC7F06E8FDE7B45DAAC') # Eric Vidal

build() {
  cd ${srcdir}/${pkgname}
  ./configure --prefix=/usr \
			  --bindir=/usr/bin \
			  --sbindir=/usr/bin \
			  --datadir=/etc
  make
}

package() {
  cd ${srcdir}/${pkgname}

  DESTDIR=${pkgdir} make install
  
  # add doc
  install -dm 0755 $pkgdir/usr/share/doc/$pkgname/
  cp -R doc/* $pkgdir/usr/share/doc/$pkgname/
  
  install -D -m644 COPYING "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
  
}

# vim:ft=sh ts=2 sw=2 et:

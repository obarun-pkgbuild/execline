# Maintainer: Eric Vidal <eric@obarun.org>

pkgname=execline
pkgver=2.5.0.0
pkgrel=1
pkgdesc="An interpreter-less scripting language."
arch=(x86_64)
url="http://skarnet.org/software/execline/"
license=('ISC')
groups=(s6-suite)
groups=('base' 's6-suite')
makedepends=('git' 'skalibs')
conflicts=(execline-git)
source=("$pkgname::git+git://git.skarnet.org/execline#tag=v${pkgver}")
#source=("$pkgname::git+git://git.skarnet.org/execline#commit=$_commit")
#_commit=a774afb87c2d021301437c3a60fdd0039cf2458b # tag 2.3.0.4
md5sums=('SKIP')
validpgpkeys=('6DD4217456569BA711566AC7F06E8FDE7B45DAAC') # Eric Vidal


build() {
  cd "$srcdir/$pkgname"
  ./configure 	--prefix=/usr \
				--exec-prefix=/usr/local \
				--libexecdir=/usr/libexec \
				--sbindir=/usr/local/bin \
				--shebangdir=/usr/local/bin
  make
}

package() {
  cd "$srcdir/$pkgname"
  make DESTDIR="$pkgdir/" install
  
   # add doc
  install -dm 0755 $pkgdir/usr/share/doc/$pkgname/
  cp -R doc/* $pkgdir/usr/share/doc/$pkgname/
  
  install -Dm644 COPYING "$pkgdir/usr/share/licenses/${pkgname%-*}/COPYING"
} 

# Maintainer: Eric Vidal <eric@obarun.org>

pkgname=execline
pkgver=2.3.0.1
pkgrel=1
pkgdesc="An interpreter-less scripting language."
arch=(x86_64)
url="http://skarnet.org/software/execline/"
license=('ISC')
groups=(s6-suite)
depends=('skalibs')
makedepends=('git' 'skalibs')
conflicts=(execline-git)
source=("$pkgname::git+git://git.skarnet.org/execline#commit=$_commit")
_commit=a865e0bd539407820d96016fc90cb6dee3e743aa # tag 2.3.0.1
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
  install -Dm644 COPYING "$pkgdir/usr/share/licenses/${pkgname%-*}/COPYING"
} 

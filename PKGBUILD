# Maintainer: Johannes "jo" Erwerle <jo+myping@swagspace.org>
pkgname=myping
pkgver=1
pkgrel=1
epoch=
pkgdesc=""
arch=("x86_64")
url=""
license=('WTFPL')
groups=()
depends=(glibc)
makedepends=(go)
checkdepends=()
optdepends=()
provides=()
conflicts=()
replaces=()
backup=()
options=()
install="myping.install"
changelog=
source=("$pkgname-$pkgver.zip::https://github.com/9er/myping/archive/refs/heads/master.zip")
noextract=()
sha256sums=(SKIP)
validpgpkeys=()

build() {
	cd "$pkgname-master"

	export CGO_CPPFLAGS="${CPPFLAGS}"
	export CGO_CFLAGS="${CFLAGS}"
	export CGO_CXXFLAGS="${CXXFLAGS}"
	export CGO_LDFLAGS="${LDFLAGS}"
	export GOFLAGS="-buildmode=pie -trimpath -ldflags=-linkmode=external -mod=readonly -modcacherw"

	go mod tidy
	go build src/myping.go
}

package() {
	mkdir -p $pkgdir/usr/bin/
	cd "$pkgname-master"
	cp myping $pkgdir/usr/bin/myping
}

# Maintainer: Albert Sebastian <albertsebe2 at gmail dot com>

pkgname=furmark
pkgver=2.7.0.0
pkgrel=1
pkgdesc='Lightweight but intensive GPU stress test and benchmarking tool for OpenGL and Vulkan'
arch=('x86_64' 'aarch64')
url='https://www.geeks3d.com/furmark/v2/'
license=('custom:freeware')
depends=(gcc-libs opengl-driver glu libxcb)
optdepends=('vulkan-driver: Vulkan benchmark support')
makedepends=('7zip')
source_x86_64=("https://gpumagick.com/downloads/files/2025/fm2/FurMark_${pkgver}_linux64.7z")
source_aarch64=("https://gpumagick.com/downloads/files/2025/fm2/FurMark_${pkgver}_arm64.7z")
sha256sums_x86_64=('AB482D58115AA8FB332392102A5CA5AF8746ECE383CC09F39B90CF5C1A99AFAD')
sha256sums_aarch64=('F2039230CECB46C294FF632CC04A5ADABA7FBA39F3B6C775B585E268162991A5')

# TODO: dekstop entry with https://geeks3d.com/furmark/i/20240220-furmark-logo-02.png

package(){
    cd "$srcdir/FurMark_linux64"

    install -d "$pkgdir/opt/$pkgname/"
    cp -a ./ "$pkgdir/opt/$pkgname/"

    install -d "$pkgdir/usr/bin/"
    ln -s "/opt/$pkgname/furmark" "$pkgdir/usr/bin/furmark"
    ln -s "/opt/$pkgname/FurMark_GUI" "$pkgdir/usr/bin/furmark-gui"

    # TODO: make this a symlink as well
    install -Dm644 "./EULA.txt" "$pkgdir/usr/share/licenses/$pkgname/EULA.txt"
}

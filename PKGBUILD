# Maintainer: Albert Sebastian <albertsebe2 at gmail dot com>

pkgname=furmark
pkgver=2.7.0.0
pkgrel=3
pkgdesc='Lightweight but intensive GPU stress test and benchmarking tool for OpenGL and Vulkan'
arch=('x86_64' 'aarch64')
url='https://www.geeks3d.com/furmark/v2/'
license=('custom:freeware')
depends=(gcc-libs opengl-driver glu libxcb)
optdepends=('vulkan-driver: Vulkan benchmark support')
makedepends=('7zip')
source=('furmark-gui.desktop' 'https://geeks3d.com/furmark/i/20240220-furmark-logo-02.png')
source_x86_64=("https://gpumagick.com/downloads/files/2025/fm2/FurMark_${pkgver}_linux64.7z")
source_aarch64=("https://gpumagick.com/downloads/files/2025/fm2/FurMark_${pkgver}_arm64.7z")
sha256sums=('SKIP' '12A8564204C4985FF601CA83C601ADAF69B948C62EA76F213C4848EACB05C3B8')
sha256sums_x86_64=('AB482D58115AA8FB332392102A5CA5AF8746ECE383CC09F39B90CF5C1A99AFAD')
sha256sums_aarch64=('F2039230CECB46C294FF632CC04A5ADABA7FBA39F3B6C775B585E268162991A5')

package(){
    install -d "$pkgdir/opt/$pkgname/"
    cp -a "$srcdir/FurMark_linux64/" "$pkgdir/opt/$pkgname/"

    install -d "$pkgdir/usr/bin/"
    ln -s "/opt/$pkgname/furmark" "$pkgdir/usr/bin/furmark"
    ln -s "/opt/$pkgname/FurMark_GUI" "$pkgdir/usr/bin/furmark-gui"

    # TODO: make this a symlink as well
    install -Dm644 "$srcdir/FurMark_linux64/EULA.txt" "$pkgdir/usr/share/licenses/$pkgname/EULA.txt"

    # Install icon
    install -Dm644 "$srcdir/20240220-furmark-logo-02.png" "$pkgdir/usr/share/pixmaps/$pkgname.png"
    # Install desktop entry (uses the icon)
    # We could use gendesk to generate the desktop entry,
    # but that requires it as an additional build dependency...
    # (see https://wiki.archlinux.org/title/Desktop_entries)
    # gendesk --pkgname "$pkgname" --pkgdesc "$pkgdesc" --exec "furmark-gui" --categories "Graphics" --name "FurMark GUI"
    install -Dm644 "$srcdir/furmark-gui.desktop" "$pkgdir/usr/share/applications/$pkgname.desktop"
}

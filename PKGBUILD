# Maintainer: Albert Sebastian <albertsebe2 at gmail dot com>

pkgname=furmark
pkgver=2.8.0.0
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
sha256sums_x86_64=('12EA8B43626AB0EE9B31B69DAF782CCAF22B37C83D3499E4E404FAE2E1FBB1BC')
sha256sums_aarch64=('39EEF070AD6191EC8443FC6E516E88C963470E0A8334CDF75C1A16BC8274AB04')

package(){
    install -d "$pkgdir/opt/$pkgname/"
    cp -a "$srcdir/FurMark_linux64/." "$pkgdir/opt/$pkgname/"

    install -d "$pkgdir/usr/bin/"
    ln -s "/opt/$pkgname/furmark" "$pkgdir/usr/bin/furmark"
    ln -s "/opt/$pkgname/FurMark_GUI" "$pkgdir/usr/bin/furmark-gui"

    install -d "$pkgdir/usr/share/licenses/$pkgname"
    ln -s "/opt/$pkgname/EULA.txt" "$pkgdir/usr/share/licenses/$pkgname/EULA.txt"

    touch "$pkgdir/opt/$pkgname/_furmark_log.txt"
    touch "$pkgdir/opt/$pkgname/_geexlab_log.txt"
    touch "$pkgdir/opt/$pkgname/settings.lua"
    touch "$pkgdir/opt/$pkgname/conf.xml"
    # touch imgui.ini # idk what this is, probably not needed
    
    chmod 646 "$pkgdir/opt/$pkgname/_furmark_log.txt"
    chmod 646 "$pkgdir/opt/$pkgname/_geexlab_log.txt"
    chmod 646 "$pkgdir/opt/$pkgname/settings.lua"
    chmod 646 "$pkgdir/opt/$pkgname/conf.xml"

    # Install icon
    install -Dm644 "$srcdir/20240220-furmark-logo-02.png" "$pkgdir/usr/share/pixmaps/$pkgname.png"
    # Install desktop entry (uses the icon)
    # We could use gendesk to generate the desktop entry,
    # but that requires it as an additional build dependency...
    # (see https://wiki.archlinux.org/title/Desktop_entries)
    # gendesk --pkgname "$pkgname" --pkgdesc "$pkgdesc" --exec "furmark-gui" --categories "Graphics" --name "FurMark GUI"
    install -Dm644 "$srcdir/furmark-gui.desktop" "$pkgdir/usr/share/applications/$pkgname.desktop"
}

# Maintainer: Vincent Långström <vincent dot langstrom at gmail dot com>
# Contributor: Albert Sebastian <albertsebe2 at gmail dot com>

pkgname=furmark
pkgver=2.8.2.0
pkgrel=1
pkgdesc='Lightweight but intensive GPU stress test and benchmarking tool for OpenGL and Vulkan'
arch=('x86_64' 'aarch64')
url='https://www.geeks3d.com/furmark/v2/'
license=('custom:freeware')
depends=(gcc-libs opengl-driver glu libxcb)
optdepends=('vulkan-driver: Vulkan benchmark support')
makedepends=('7zip')
source=('furmark-gui.desktop' 'https://geeks3d.com/furmark/i/20240220-furmark-logo-02.png')
source_x86_64=("https://gpumagick.com/downloads/files/2025/fm2/FurMark_${pkgver}_linux64.7z")
# For some weird reason, the arm64 verison hasn't gotten the 2.8.2.0 upgrade, and is stuck on 2.8.0.0 as of 3.6.2025.
# Hopefully it's fine to leave it like this instead of creating some pkgver function that accounts for this
source_aarch64=("https://gpumagick.com/downloads/files/2025/fm2/FurMark_2.8.0.0_arm64.7z")
sha256sums=('SKIP' '12A8564204C4985FF601CA83C601ADAF69B948C62EA76F213C4848EACB05C3B8')
sha256sums_x86_64=('97D52EFA81028F9B3EC11C351C1EEEB08EB2B86108686C1AA8E7466BE936FAA1')
sha256sums_aarch64=('39EEF070AD6191EC8443FC6E516E88C963470E0A8334CDF75C1A16BC8274AB04')

package(){
    install -d "$pkgdir/opt/$pkgname/"
    cp -a "$srcdir/FurMark_linux64/." "$pkgdir/opt/$pkgname/"

    install -d "$pkgdir/usr/bin/"
    ln -s "/opt/$pkgname/furmark" "$pkgdir/usr/bin/furmark"
    ln -s "/opt/$pkgname/FurMark_GUI" "$pkgdir/usr/bin/furmark-gui"

    install -d "$pkgdir/usr/share/licenses/$pkgname"
    ln -s "/opt/$pkgname/EULA.txt" "$pkgdir/usr/share/licenses/$pkgname/EULA.txt"


    # Create config directory
    install -dm757 "$pkgdir/etc/opt/$pkgname"

    # Copy config files into writeable directory
    cp "$pkgdir/opt/$pkgname/settings.lua"  "$pkgdir/etc/opt/$pkgname/settings.lua"
    cp "$pkgdir/opt/$pkgname/conf.xml"      "$pkgdir/etc/opt/$pkgname/conf.xml"
    # Delete original defaults
    rm "$pkgdir/opt/$pkgname/settings.lua"
    rm "$pkgdir/opt/$pkgname/conf.xml"
    # Set permissions
    chmod 646 "$pkgdir/etc/opt/$pkgname/settings.lua"
    chmod 646 "$pkgdir/etc/opt/$pkgname/conf.xml"

    # Create log directory
    install -dm757 "$pkgdir/var/log/$pkgname"

    ln -s "/var/log/$pkgname/furmark.log"   "$pkgdir/opt/$pkgname/_furmark_log.txt"
    # A log file was included in 2.8.1.1. Let's override it
    ln -sf "/var/log/$pkgname/geexlab.log"   "$pkgdir/opt/$pkgname/_geexlab_log.txt"
    ln -s "/etc/opt/$pkgname/settings.lua"  "$pkgdir/opt/$pkgname/settings.lua"
    ln -s "/etc/opt/$pkgname/conf.xml"      "$pkgdir/opt/$pkgname/conf.xml"

    # touch imgui.ini # idk what this is, probably not needed

    # Install icon
    install -Dm644 "$srcdir/20240220-furmark-logo-02.png" "$pkgdir/usr/share/pixmaps/$pkgname.png"
    # Install desktop entry (uses the icon)
    # We could use gendesk to generate the desktop entry,
    # but that requires it as an additional build dependency...
    # (see https://wiki.archlinux.org/title/Desktop_entries)
    # gendesk --pkgname "$pkgname" --pkgdesc "$pkgdesc" --exec "furmark-gui" --categories "Graphics" --name "FurMark GUI"
    install -Dm644 "$srcdir/furmark-gui.desktop" "$pkgdir/usr/share/applications/$pkgname.desktop"
}

# Save config files if modified by the user
backup=("etc/opt/$pkgname/settings.lua" "etc/opt/$pkgname/conf.xml")

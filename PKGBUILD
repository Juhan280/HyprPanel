# Maintainer: cat_nm
# Maintainer: jaskir
pkgname=ags-hyprpanel-git-juhan
pkgver=r18.4810d0f
pkgrel=1
pkgdesc="A Bar/Panel for Hyprland with extensive customizability"
arch=('x86_64')
url="https://hyprpanel.com/"
license=('MIT')
depends=(
    # official repository:
    'wireplumber'
    'libgtop'
    'bluez'
    'bluez-utils'
    'networkmanager'
    'dart-sass'
    'wl-clipboard'
    'upower'
    'gvfs'
    'ttf-jetbrains-mono-nerd'
    # aur:
    'aylurs-gtk-shell-git'
)
makedepends=(
    'meson'
    'unzip'
    'git'
)
optdepends=(
    'python: GPU usage tracking (NVidia only)'
    'python-gpustat: GPU usage tracking (NVidia only)'
    'python-pywal: Pywal hook for wallpapers'
    'pacman-contrib: Checking for pacman updates'
    'power-profiles-daemon: Switch power profiles'
    'swww: Setting wallpapers'
    'grimblast-git: For the snapshot shortcut'
    'brightnessctl: To control keyboard and screen brightness'
    'btop: To view system resource usage'
    'wf-recorder: To use the built in screen recorder'
    'hyprpicker: To use the preset color picker shortcut'
    'hypridle: To use hyprlands idle inhibitor'
    'hyprsunset: To enable the hyprland blue light filter'
    'matugen-bin: To use wallpaper based color schemes'
)
provodes=('ags-hyprpanel-git')
conflicts=('ags-hyprpanel-git')
# source=('git+https://github.com/Jas-SinghFSU/HyprPanel.git#branch=master')
# sha256sums=('SKIP')

pkgver() {
    cd "$srcdir/.."
    printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short=7 HEAD)"
}

build() {
    cd "$srcdir/.."
    git pull --autostash upstream master:master
    arch-meson --reconfigure build
    meson compile -C build
}

package() {
    cd "$srcdir/.."

    meson install -C build --destdir "$pkgdir"

    # License
    install -Dm644 "LICENSE" "$pkgdir/usr/share/licenses/${pkgname}/LICENSE"
}

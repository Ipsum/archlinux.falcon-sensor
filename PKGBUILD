# Maintainer: Fredy García <frealgagu at gmail dot com>

pkgname=falcon-sensor
pkgver=6.39.0_13601
pkgrel=1
pkgdesc="Crowdstrike Falcon Sensor daemon and kernel modules"
arch=("x86_64")
url="https://crowdstrike.com"
license=("custom")
depends=("openssl" "libnl1")
backup=("etc/logrotate.d/falcon-sensor")
install="${pkgname}.install"
source=(
  "manual://${pkgname}_${pkgver/_/-}_amd64.deb"
  "LICENSE"
)
sha256sums=(
  "0c0a41ebd49f0c5836de52ad5ab40349a3e6bf3c7ce00c16fc25902659c3ed84"
  "76dbcf8027846d9a8c2fbd9ca2a163c171bbc75161b46a24f59bf64dd44fc6e9"
)

prepare() {
  mkdir "${srcdir}/${pkgname}"
  cd "${srcdir}/${pkgname}"

  bsdtar -xf "${srcdir}/data.tar.xz" -C .

  # Remove unnecessary .deb related directory
  rm -rf "${srcdir}/${pkgname}/etc/init.d"
}

package() {
  cd "${srcdir}/${pkgname}"
  cp -r "${srcdir}/${pkgname}/"* "${pkgdir}"
  install -dm755 "${pkgdir}/usr"
  mv "${pkgdir}/lib" "${pkgdir}/usr/lib"
  install -Dm644 "${srcdir}/LICENSE" "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"

  chmod a+x "${pkgdir}/opt/CrowdStrike"
  chmod -R a+r "${pkgdir}/opt/CrowdStrike"
}

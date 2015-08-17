# Script generated with import_catkin_packages.py
# For more information: https://github.com/bchretien/arch-ros-stacks
pkgdesc="ROS - This package contains a ROS wrapper for OpenSlams Gmapping."
url='http://ros.org/wiki/gmapping'

pkgname='ros-hydro-gmapping'
pkgver='1.3.4'
_pkgver_patch=0
arch=('any')
pkgrel=1
license=('CreativeCommons-by-nc-sa-2.0')

ros_makedepends=(ros-hydro-openslam-gmapping
  ros-hydro-roscpp
  ros-hydro-catkin
  ros-hydro-nav-msgs
  ros-hydro-tf
  ros-hydro-rostest)
makedepends=('cmake' 'git' 'ros-build-tools'
  ${ros_makedepends[@]})

ros_depends=(ros-hydro-tf
  ros-hydro-roscpp
  ros-hydro-openslam-gmapping
  ros-hydro-nav-msgs)
depends=(${ros_depends[@]})

_tag=release/hydro/gmapping/${pkgver}-${_pkgver_patch}
_dir=gmapping
source=("${_dir}"::"git+https://github.com/ros-gbp/slam_gmapping-release.git"#tag=${_tag})
md5sums=('SKIP')

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/hydro/setup.bash ] && source /opt/ros/hydro/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/hydro \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

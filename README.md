# deluge-rhel
Forked from https://src.fedoraproject.org/rpms/deluge.git to build for RHEL/CentOS 8

## How to build
1. Install the Development tools (includes rpm-build)
```bash
sudo dnf group install "Development Tools"
```
2. Install rpmdevtools (for spectool)
```bash
sudo dnf install rpmdevtools
```
3. Install deluge build dependencies
```bash
sudo dnf install python3-devel python3-wheel
```
4. Build & install dependency rb_libtorrent & rb_libtorrent-python3 -> see https://github.com/chrisdevchroma/rb_libtorrent-rhel
5. Build & install dependency python3-setproctitle -> see https://github.com/chrisdevchroma/python-setproctitle-rhel
6. Build & install dependency python3-GeoIP-rhel -> see https://github.com/chrisdevchroma/python-GeoIP-rhel
5. Clone repo with git and cd into the folder
```bash
cd deluge-rhel
```
6. Create build/SOURCES dir
```bash
mkdir -p build/SOURCES
```
7. Download deluge source tarball with spectool
```bash
spectool -g -C build/SOURCES deluge.spec
```
8. Copy *.service files into build/SOURCES
```bash
cp *.service build/SOURCES
```
9. Build package with rpmbuild
```bash
rpmbuild --define "_topdir `pwd`/build" -ba deluge.spec
```
10. Install deluge packages
```bash
sudo dnf install ./build/RPMS/noarch/deluge*.rpm
```
Or as seperate packages
```bash
sudo dnf install ./build/RPMS/noarch/deluge-common-2.0.3-*.el8.noarch.rpm
sudo dnf install ./build/RPMS/noarch/deluge-images-2.0.3-*.el8.noarch.rpm
sudo dnf install ./build/RPMS/noarch/deluge-daemon-2.0.3-*.el8.noarch.rpm
sudo dnf install ./build/RPMS/noarch/deluge-web-2.0.3-*.el8.noarch.rpm
sudo dnf install ./build/RPMS/noarch/deluge-gtk-2.0.3-*.el8.noarch.rpm
sudo dnf install ./build/RPMS/noarch/deluge-console-2.0.3-*.el8.noarch.rpm
sudo dnf install ./build/RPMS/noarch/deluge-2.0.3-*.el8.noarch.rpm
```

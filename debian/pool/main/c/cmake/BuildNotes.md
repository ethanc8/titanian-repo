# CMake for Jetson Nano, build notes

Setup:
```bash
sudo apt install packaging-dev devscripts equivs
wget http://deb.debian.org/debian/pool/main/d/debian-archive-keyring/debian-archive-keyring_2023.4_all.deb
sudo apt install ./debian-archive-keyring_2023.4_all.deb
echo "deb-src http://deb.debian.org/debian/ testing main" | sudo tee -a /etc/apt/sources.list.d/debian-testing-source.list > /dev/null
echo "deb-src http://deb.debian.org/debian/ bookworm main" | sudo tee -a /etc/apt/sources.list.d/debian-bookworm-source.list > /dev/null
echo "deb-src http://deb.debian.org/debian/ buster main" | sudo tee -a /etc/apt/sources.list.d/debian-buster-source.list > /dev/null

sudo apt update
```

Also, make sure you have the latest `debhelper` from Backports:

```bash
# Ubuntu 18.04
sudo apt install -t bionic-backports debhelper
```

### Building CMake (example) on 18.04

```bash
cd ~/Projects/CMake
### Build libarchive-dev
apt source libarchive/buster
cd libarchive-*
sudo mk-build-deps --install # Allow it to remove `libarchive-build-deps`
sudo apt install libbz2-dev liblz4-dev libzstd-dev libacl1-dev libext2fs-dev sharutils nettle-dev liblzo2-dev
dch --bpo
# Allow building with Jetson's malformed shared library metadata
printf "override_dh_shlibdeps:\n\tdh_shlibdeps --dpkg-shlibdeps-params=--ignore-missing-info" >> debian/rules
dpkg-buildpackage --build=binary --unsigned-changes
cd ..
# The packages are in ~/Projects/CMake
sudo apt install ./libarchive13_3.3.3-4+deb10u1_arm64.deb ./libarchive-dev_3.3.3-4+deb10u1_arm64.deb ./libarchive-tools_3.3.3-4+deb10u1_arm64.deb
### Build libuv1
apt source libuv1/bookworm
cd libuv1-*
sudo mk-build-deps --install # Allow it to remove `libuv1-build-deps`
dch --bpo
# Allow building with Jetson's malformed shared library metadata
printf "override_dh_shlibdeps:\n\tdh_shlibdeps --dpkg-shlibdeps-params=--ignore-missing-info" >> debian/rules
dpkg-buildpackage --build=binary --unsigned-changes
cd ..
# The packages are in ~/Projects/CMake
sudo apt install ./libuv1_1.44.2-1_arm64.deb ./libuv1-dev_1.44.2-1_arm64.deb
### Build cmake
apt source cmake/bookworm
cd cmake-*
sudo mk-build-deps --install # Allow it to remove `cmake-build-deps`
sudo apt install libcurl4-openssl-dev libjsoncpp-dev libncurses5-dev librhash-dev libuv1-dev
dch --bpo

# Install dh_sphinxdoc and latest sphinx (might not be necessary)
mkdir -p ~/.local/bin
mkdir -p ~/.local/share/perl5/Debian/Debhelper/Sequence/
export PATH="$HOME/.local/bin:$PATH"
export PERL5LIB="$HOME/.local/share/perl5/:$PERL5LIB"
export PYTHONPATH="$HOME/.local/lib/python3.6/site-packages:$PYTHONPATH"
curl -L https://salsa.debian.org/python-team/packages/sphinx/-/raw/debian/master/debian/dh-sphinxdoc/dh_sphinxdoc --output "$HOME/.local/bin/dh_sphinxdoc"
curl -L https://salsa.debian.org/python-team/packages/sphinx/-/raw/debian/master/debian/dh-sphinxdoc/sphinxdoc.pm --output "$HOME/.local/share/perl5/Debian/Debhelper/Sequence/sphinxdoc.pm"
chmod +x "$HOME/.local/bin/dh_sphinxdoc"
chmod +x "$HOME/.local/share/perl5/Debian/Debhelper/Sequence/sphinxdoc.pm"
pip3 install --user sphinx sphinxcontrib-qthelp

sudo apt install libjson-perl

# Avoid building the documentation, since Sphinx isn't working
# The old preinstalled CMake can't handle the testsuite
export DEB_BUILD_PROFILES="nodoc nocheck"
export DEB_BUILD_OPTIONS="nodoc nocheck"
# Allow building with Jetson's malformed shared library metadata
printf "override_dh_shlibdeps:\n\tdh_shlibdeps --dpkg-shlibdeps-params=--ignore-missing-info" >> debian/rules
sed -i "s/dh\_sphinxdoc \-pcmake\-doc/:/" debian/rules
dpkg-buildpackage --build=binary --unsigned-changes -d
# Add -nc to dpkg-buildpackage to avoid running `make clean`
```
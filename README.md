# Building encfs-1.8.1 for SailfishOS

[Install Platform SDK](https://sailfishos.org/wiki/Platform_SDK_Installation)

[Install SDK Target](https://sailfishos.org/wiki/Platform_SDK_Target_Installation)

Install needed packages:
```
sb2 -t SailfishOS-latest-armv7hl -m sdk-install -R zypper in autoconf automake gettext libtool
sb2 -t SailfishOS-latest-armv7hl -m sdk-install -R zypper in fuse-devel openssl-devel boost-devel
```

Download and compile rlog-1.4 (will be linked statically)
```
curl -L -O https://storage.googleapis.com/google-code-archive-downloads/v2/code.google.com/rlog/rlog-1.4.tar.gz
tar xzf rlog-1.4.tar.gz
cd rlog-1.4
sb2 -t SailfishOS-latest-armv7hl -m sdk-build ./configure --prefix=/usr --enable-static
sb2 -t SailfishOS-latest-armv7hl -m sdk-build -R make install
cd ..
```

Download and build package for encfs 1.8.1
```
curl -L -O https://github.com/vgough/encfs/releases/download/v1.8.1/encfs-1.8.1.tar.gz
tar xzf encfs-1.8.1.tar.gz
cd encfs-1.8.1
sb2 -t SailfishOS-latest-armv7hl -m sdk-build autoreconf -if
```
copy rpm directory from this repository
```
mb2 -t SailfishOS-latest-armv7hl build
```

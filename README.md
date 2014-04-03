# small example howto automake

## 带内核模块，需要安装kernel-devel

    automake --add-missing
    autoreconf --install
    ./configure
    make
    make install

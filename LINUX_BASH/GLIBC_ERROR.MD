# How to install GLIBC 2.29 or higher in Ubuntu 18.04
`wget -c https://ftp.gnu.org/gnu/glibc/glibc-2.29.tar.gz
tar -zxvf glibc-2.29.tar.gz
mkdir glibc-2.29/build
cd glibc-2.29/build
../configure --prefix=/opt/glibc
make 
make install`



# glibc configure error: yacc/bison missing
`wget https://ftp.gnu.org/gnu/bison/bison-3.2.tar.gz
tar xf bison-3.2.tar.gz
cd bison-3.2
./configure --prefix=$HOME/install
make
`make install`

Then you can put the $HOME/install/bin directory on the command search path:

`PATH=$HOME/install/bin:$PATH`

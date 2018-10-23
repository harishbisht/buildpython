# compile cpython code from source in ubuntu 18.04 LTS

### Steps:
1. First open the github link and clone the code https://github.com/python/cpython
2. open the terminal and follow the steps
```sh
$ git clone https://github.com/python/cpython.git
$ cd cpython
```
3. Now install the packages
```sh
$ sudo apt-get update \
  && sudo apt-get install -y build-essential git libexpat1-dev libssl-dev zlib1g-dev \
  libncurses5-dev libbz2-dev liblzma-dev \
  libsqlite3-dev libffi-dev tcl-dev linux-headers-generic libgdbm-dev \
  libreadline-dev tk tk-dev
```

4. Before running the below command change the final_output_path, i have set my path to the /home/ubuntu/desktop/compiledpython3.8/ and make sure that folder exist
```sh
$ ./configure --prefix=<final_output_path> \
  --enable-loadable-sqlite-extensions \
  --enable-shared \
  --with-lto \
  --enable-optimizations \
  --with-system-expat \
  --with-system-ffi \
  --enable-ipv6 --with-threads --with-pydebug --disable-rpath
$ make
$ sudo make install
```
5. Now change directory to the final_output_path
```sh
$ cd <final_output_path>
```
6. Now in the final_output_path you will get 4 folders bin,include,lib,share, now export LD_LIBRARY_PATH
```sh
$ export LD_LIBRARY_PATH=<final_output_path>/lib/ 
```
7. Now change directory to the bin folder of your final_output_path and run your latest python3.8
```sh
$ ./python3
```

# Requirements

## Required operating systems

* CentOS 6.x or CentOS 7.x
* Mac OS X (experimental)
    
## Required compilers

* GCC 4.8.5 or higher
* CMake 3.3 or higher
    
## Required libraries

* libpcap-devel
* boost-devel
* boost-static


# Build steps

## CentOS

1. Prepair the environment.

```shell
# install gcc
yum groupinstall "Development Tools"
# install cmake
yum -y install cmake
# install more required libraries
yum -y install libpcap-devel boost-devel boost-static
```

2. Clone or download the project.
3. Go to the project folder and build it.

```shell
cd /path/to/packet-agent
mkdir build && cd build
cmake .. && make
```

4. Check output binaries. There should be four files in the *bin* folder.

```shell
ls ../bin
gredemo*     gredump*     pcapcompare* pktminerg*
```

## Mac OS X

1. Install [Xcode](https://developer.apple.com/xcode/).
2. Download the latest release of libpcap from [tcpdump site](http://www.tcpdump.org). Extract the zip, enter the folder and build the library.

```shell
cd /path/to/libpcap
./configure 
make
make install
# Check that libpcap.a and libpcap.dylib exist.
ls /usr/local/lib/libpcap*
```

2. *Recommended*: install [brew](https://brew.sh/) for easier package management.

```shell
# install boost
brew install boost
```

2. Clone or download the project.
3. Build the project.

```shell
cd /path/to/packet-agent
mkdir build && cd build
cmake .. && make
```

4. Ensure the build is successful. The *bin* folder should contain four binary files.

```shell
ls ../bin
gredemo*     gredump*     pcapcompare* pktminerg*
```

## FAQ

### CMake Error 51

```shell
CMake Error at /usr/local/Cellar/cmake/3.9.4/share/cmake/Modules/CMakeTestCCompiler.cmake:51 (message):
  The C compiler "/usr/bin/cc" is not able to compile a simple test program.
```

A: Firstly, check that [Xcode](https://developer.apple.com/xcode/) has been installed. Then make sure you have accepted the xcodebuild license.

```shell
sudo xcodebuild -license accept
```
  


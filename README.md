# Installing the mongocxx driver on Windows 7

## Motivation
I tried to install it using the [MongoDB official documentation](http://mongodb.github.io/mongo-cxx-driver/mongocxx-v3/installation/) but I found errors during installation, and they use Visual Studio. Since there's not a good guide to install and use mongocxx driver on Windows without using Visual Studio, I decide to make my own.

## Table of Contents

- [MinGW](#mingw)
- [mongo-c-driver](#mongo-c-driver)
  - [libbson](#libbson)
  - [MongoDB C driver](#mongodb-c-driver)
- [mongo-cxx-driver](#mongo-cxx-driver)

## MinGW
I used the MinGW that comes with Qt.

## mongo-c-driver
As the official documentation says, the mongocxx driver builds on top of the MongoDB C driver. So you need to install it first.

I downloaded the release version [mongo-c-driver 1.6.3](https://github.com/mongodb/mongo-c-driver/releases).

```
$ tar xzf mongo-c-driver-1.6.3.tar.gz
```

### libbson
Let's start by installing libbson, a dependency of the C driver.

```
$ cd mongo-c-driver-1.6.3/src/libbson
$ cmake -G "MinGW Makefiles" "-DCMAKE_INSTALL_PREFIX=C:\mongo-c-driver"
```
**cmake** will output <a href="outputs/output1.md">this</a>.

```
$ C:\Qt\Tools\mingw491_32\bin\mingw32-make.exe
$ C:\Qt\Tools\mingw491_32\bin\mingw32-make.exe install
```
**make** will output <a href="outputs/output2.md">this</a>.
**make install** will output <a href="outputs/output3.md">this</a>.

Now you should see at your `-DCMAKE_INSTALL_PREFIX` (in my case C:\mongo-c-driver) files like <a href="trees/tree1.md">these.</a>.

### MongoDB C driver
Now let's do the same for the MongoDB C driver.

Go to mongo-c-driver-1.6.3
```
$ cd ../..
$ cmake -G "MinGW Makefiles" "-DCMAKE_INSTALL_PREFIX=C:\mongo-c-driver" "-DBSON_ROOT_DIR=C:\mongo-c-driver" -DENABLE_SASL:BOOL=OFF
```
**cmake** will output <a href="outputs/output4.md">this</a>.

Note that I tried to install without using `-DENABLE_SASL:BOOL=OFF`, but I found too many errors.

```
$ C:\Qt\Tools\mingw491_32\bin\mingw32-make.exe
$ C:\Qt\Tools\mingw491_32\bin\mingw32-make.exe install
```
**make** will output <a href="outputs/output5.md">this</a>.
**make install** will output <a href="outputs/output6.md">this</a>.

Now you should see at your `-DCMAKE_INSTALL_PREFIX` (in my case C:\mongo-c-driver) files like <a href="trees/tree2.md">these.</a>.

## mongo-cxx-driver
Look on the [mongocxx releases](https://github.com/mongodb/mongo-cxx-driver/releases) page for a link to the release tarball for the version you wish you install. For example, to download version 3.1.1 (I used this one):

```
$ curl -OL https://github.com/mongodb/mongo-cxx-driver/archive/r3.1.1.tar.gz
$ tar -xzf r3.1.1.tar.gz
$ cd mongo-cxx-driver-r3.1.1/build
$ cmake -G "MinGW Makefiles" -DCMAKE_INSTALL_PREFIX=C:\mongo-cxx-driver -DLIBBSON_DIR=C:\mongo-c-driver -DLIBMONGOC_DIR=C:\mongo-c-driver ..
```
**cmake** will output <a href="outputs/output7.md">this</a>.

```
C:/Qt/Tools/mingw491_32/bin/mingw32-make.exe
C:/Qt/Tools/mingw491_32/bin/mingw32-make.exe install
```
**make** will output <a href="outputs/output5.md">this</a>.
**make install** will output <a href="outputs/output6.md">this</a>.

Now you should see at your `-DCMAKE_INSTALL_PREFIX` (in my case C:\mongo-cxx-driver) files like <a href="trees/tree3.md">these.</a>.

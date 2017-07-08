# Instalando o driver mongocxx no Windows
> Also in&nbsp;
> <a href="../../README.md">🇺🇸</a>

# Motivação
Eu tentei instalar o Mongocxx usando a [documentação oficial da MongoDB](http://mongodb.github.io/mongo-cxx-driver/mongocxx-v3/installation/), mas durante a instalação achei erros além de que eles exijam que use o Visual Studio. Como não há bons guias de como instalar e usar o driver mongocxx no Windows sem utilizar o Visual Studio, decidi fazer o meu próprio utilizando o MinGW.

# Nota do autor
Se você puder, por favor não utilize Windows. Como existem um monte de distribuições Linux, tenho certeza de que encontrará uma que combina com você. Todos os erros que encontrei durante a instalação foram porquê estava usando Windows.
Só use Windows para desenvolvimento se você **precisar** testar o código em uma máquina Windows.

# Sumário

- [MinGW](#mingw)
- [CMake](#cmake)
- [mongo-c-driver](#mongo-c-driver)
  - [libbson](#libbson)
  - [MongoDB C driver](#mongodb-c-driver)
- [mongo-cxx-driver](#mongo-cxx-driver)
- [PATH](#path)
- [Teste sua instalação](#teste-sua-instalação)
  - [Compile](#compile)

# MinGW
Eu usei o MinGW que vem com o Qt.

# CMake
Usei o Cmake 3.7.2.

# mongo-c-driver
Como diz a documentação oficial, o driver mongocxx se constrói em cima do driver MongoDB C. Então deve instalá-lo primeiro.

Eu baixei a versão de release [mongo-c-driver 1.6.3](https://github.com/mongodb/mongo-c-driver/releases).

```
$ tar xzf mongo-c-driver-1.6.3.tar.gz
```

## libbson
Vamos começar instalando o libbson, uma dependência do driver para C.

```
$ cd mongo-c-driver-1.6.3/src/libbson
$ cmake -G "MinGW Makefiles" "-DCMAKE_INSTALL_PREFIX=C:\mongo-c-driver"
```
**cmake** irá gerar <a href="../../output/libbson_cmake.md">isso</a>.

```
$ C:\Qt\Tools\mingw491_32\bin\mingw32-make.exe
$ C:\Qt\Tools\mingw491_32\bin\mingw32-make.exe install
```
**make** irá gerar <a href="../../output/libbson_make.md">isso</a>.
**make install** irá gerar <a href="../../output/libbson_make_install.md">isso</a>.

Agora você deve ver em seu `-DCMAKE_INSTALL_PREFIX` (no meu caso C:\mongo-c-driver) arquivos como <a href="../../output/libbson_tree.md">esses</a>.

## MongoDB C driver
Vamos fazer o mesmo para o driver MongoDB C.

Vá para a pasta `mongo-c-driver-1.6.3`.
```
$ cd ../..
$ cmake -G "MinGW Makefiles" "-DCMAKE_INSTALL_PREFIX=C:\mongo-c-driver" "-DBSON_ROOT_DIR=C:\mongo-c-driver" -DENABLE_SASL:BOOL=OFF
```
**cmake** irá gerar <a href="../../output/mongoc_cmake.md">isso</a>.

Note que eu tentei instalar sem utilizar o `-DENABLE_SASL:BOOL=OFF`, mas encontrei muitos problemas.

```
$ C:\Qt\Tools\mingw491_32\bin\mingw32-make.exe
$ C:\Qt\Tools\mingw491_32\bin\mingw32-make.exe install
```
**make** irá gerar <a href="../../output/mongoc_make.md">isso</a>.
**make install** irá gerar <a href="../../output/mongoc_make_install.md">isso</a>.

Agora você deve ver em seu `-DCMAKE_INSTALL_PREFIX` (no meu caso C:\mongo-c-driver) arquivos como <a href="../../output/mongoc_tree.md">esses</a>.

# mongo-cxx-driver
Acesse a página de [releases do mongocxx](https://github.com/mongodb/mongo-cxx-driver/releases) para um link da versão que você irá instalar. Por exemplo, para baixar a versão 3.1.1 (eu usei essa):

```
$ curl -OL https://github.com/mongodb/mongo-cxx-driver/archive/r3.1.1.tar.gz
$ tar -xzf r3.1.1.tar.gz
$ cd mongo-cxx-driver-r3.1.1/build
$ cmake -G "MinGW Makefiles" -DCMAKE_INSTALL_PREFIX=C:\mongo-cxx-driver -DLIBBSON_DIR=C:\mongo-c-driver -DLIBMONGOC_DIR=C:\mongo-c-driver ..
```
**cmake** irá gerar <a href="../../output/mongocxx_cmake.md">isso</a>.

```
C:/Qt/Tools/mingw491_32/bin/mingw32-make.exe
C:/Qt/Tools/mingw491_32/bin/mingw32-make.exe install
```
**make** irá gerar <a href="../../output/mongocxx_make.md">isso</a>.
**make install** irá gerar <a href="../../output/mongocxx_make_install.md">isso</a>.

Agora você deve ver em seu `-DCMAKE_INSTALL_PREFIX` (no meu caso C:\mongo-cxx-driver) arquivos como <a href="../../output/mongocxx_tree.md">esses</a>.

# PATH
Coloque `C:\mongo-cxx-driver\bin;C:\mongo-c-driver\bin` no PATH.

# Teste sua instalação
Você pode utilizar o código da documentação oficial, ou encontrá-lo abaixo:

```
#include <iostream>

#include <bsoncxx/builder/stream/document.hpp>
#include <bsoncxx/json.hpp>

#include <mongocxx/client.hpp>
#include <mongocxx/instance.hpp>

int main(int, char**) {
    mongocxx::instance inst{};
    mongocxx::client conn{mongocxx::uri{}};

    bsoncxx::builder::stream::document document{};

    auto collection = conn["testdb"]["testcollection"];
    document << "hello" << "world";

    collection.insert_one(document.view());
    auto cursor = collection.find({});

    for (auto&& doc : cursor) {
        std::cout << bsoncxx::to_json(doc) << std::endl;
    }
}
```

## Compile
Para compilar eu usei a seguinte linha de comando:

```
g++ --std=c++11 test.cpp -o test -IC:/mongo-cxx-driver/include/mongocxx/v_noabi -IC:/mongo-cxx-driver/include/bsoncxx/v_noabi -LC:/mongo-cxx-driver/lib -lmongocxx -lbsoncxx
```

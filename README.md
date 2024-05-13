# [DIVULGAÇÃO] Template para projetos C++

Eae pessoal como estão?

Estava cansado de toda vez que ia iniciar um novo projeto C++ ter configurar ele do zero algo, ou até mesmo pegar de outros projetos e sair limpando o que não era necessário. Então vim compartilhar com vocês um template que criei para mim, ele usa CMake para configurar o projeto e Google Tests como biblioteca de testes.

**O link para ele está no final da pagina caso queiram pular a breve explicação sobre ele.**

Para o caso de não conhecerem CMake e Google Tests vocês podem olhar alguns artigos que fiz sobre os mesmos.
- [CMake](https://github.com/italonicacio/utilizando-cmake-para-organizar-seu-projeto-cpp)
- [Google Tests](https://github.com/italonicacio/testando-sua-aplicacao-cpp-com-google-test)

O template está organizado da seguinte forma:

```shell
.
├── build.sh
├── CMakeLists.txt
├── include
│   └── sum.hpp
├── README.md
├── src
│   ├── main.cpp
│   └── sum.cpp
└── tests
    └── unit-tests
        ├── CMakeLists.txt
        ├── run-tests.cpp
        └── sum-tests.cpp
```

O CMake está configurado para tudo que você colocar em include e src ele conseguir compilar, então pode criar novas pastas e novos arquivos que deve funcionar normalmente.

Criei o script build.sh para auxiliar no processo de build. Ele pode ser usado quando se é o primeiro build do projeto e quando se quer evitar usar o cache, pois ele deleta a pasta build e refaz todo o processo de compilação. O projeto tem três formas de build sendo eles.

- DEBUG
- RELEASE
- RELEASE_TESTS

O uso do script seria o seguinte.

```shell
./build.sh build <build-type>
```
Basta modificar o *build-type* para os formatos que comentei acima e já deve estar sendo feito o processo de build.

Na parte dos testes, caso você já não tenha instalado o Google Test o CMake vai baixar ele do Github e quando você compilar seu projeto ele vai ser buildado junto, caso você faça um *make clean* e depois fazer a compilação, o Google Tests sera buildado de novo assim com o seu projeto. O Google Tests vai ficar dentro de _deps, fica parecendo um *node_modules*.

    Obs.: Caso queira instalar o Google Tests a partir do projeto basta depois da compilação executar o comando 
    "make install" e ele sera instalado na pasta "/usr/local/".

O*CMakeLists.txt* dos testes quando se quer adicionar um novo arquivo de testes vai ser necessário adicionar cada novo arquivo na mão, fiz dessa forma, pois eu vou adicionando aos poucos os testes, então testes que fiz que estão para ser finalizados não ficam quebrando no processo de build.

Espero que o template seja util para vocês como é para mim.

**Repositório com o template:** <https://github.com/italonicacio/project-templates/tree/main/templates/cpp/with-cmake>
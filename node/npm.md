# [npm ERR! errno FETCH_ERROR] Timeout para baixar as dependências
Esse problema é catacterizado pela apresentação do erro abaixo durante a execução do comando `npm install`:
```
npm ERR! errno FETCH_ERROR
npm ERR! Response timeout while trying to fetch [url] (over [time in miliseconds]ms)
```
Esse erro ocorre devido a algum problema de conectividade durante a instalação das dependências do projeto, desta forma, pode ocorrer devido a um problema no servidor de dependências, um aumento no tamanho do pacote de alguma dependência, ou pode significar um problema de conexão do dispositivo utilizado. Para essa ultima opção é importante realizar alguns testes como um ping ou telnet para o servidor de dependências, se você não utiliza nenhum servidor de dependências próprio, verfique sua conexão com um comando ping no domínio da URL apresentada no erro.

Uma forma de contornar esse problema é aumentando o tempo de timeout, pois essa forma nos dá total autonomia para poder regular o tempo de timeout, tendo em vista que as vezes devido a 1 segundo de diferença o tempo de timeout é execedido.

Para isso será necessário alterar o arquivo `.npmrc` que fica localizado na pasta do usuário no S.O, caso esse arquivo não exista o mesmo poderá ser criado.

Neste arquivo deverão ser adicionadas as seguintes linhas:

```
fetch-retry-maxtimeout=6000000
fetch-retry-maxtimeout=1000000
fetch-timeout=6000000
```

Após adicionar, salve o arquivo e reinicie o prompt em que estava sendo executado o comando `npm install`, depois disso, execute o comando novamente.


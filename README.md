# 1° Trabalho Prático - Grupo: Leonardo Martins da Silva e Wallace Krüger Junior

## Iniciando

Essas instruções permitirão que você obtenha uma cópia do projeto em sua máquina local para fins de teste.

## Pré-requisitos

### **Node.js**
No linux, a instalação no Node.js pode ser feita através do comado:
> sudo apt-get install nodejs

Para instalar Node.js em outros sistemas operacionais ou para mais informações acesse: https://nodejs.org/en/

### **npm**
O npm provavelmente já será instalado junto com sua instalação do Node.js. Caso não seja, você poderá instala-lo no linux através do comando:
>sudo apt-get install npm


### **yarn**
Instale o yarn com o comando:
>npm install --global yarn


## Configurando
Depois de instalados os pré-requisitos acima e de ter clonado o projeto em sua máquina, execute o comando abaixo na raiz do projeto:
>npm install

O comando instalará todas as dependências necessárias.

## Bibliotecas Utilizadas
- puppeteer: fornece uma API de alto nível para controle programático do Chrome ou Chromium por meio do protocolo DevTools;
- html2json: fornece praticidade de conversão de html para objeto json e vice-versa.

## Executando

Existem 3 funções no programa, verificarConsulta, executarECompararConsulta, executarECompararConsultaPRO.

Não é necessário nenhum parâmetro adicional na chamada para identificar qual função será executada, o programa identifica a função a ser executada pelos parâmetros de entrada. Por exemplo:

Para a função verificarConsulta, devem ser passados como parâmetros: endereço do host do relax, porta, instância do database e a consulta em formato txt. Essa função apenas verifica se a consulta retorna algum resultado, ou seja, apenas 'compila' sem erros. Exemplo:

yarn start $relax_host $relax_port $relax_database query_examples/5/qtrue.txt

Esta função vai retornar 0 se a consulta é inválida ou 1 se é válida.

Para a função executarECompararConsulta, devem ser passados os mesmos parâmetros da verificarConsulta seguido do arquivo txt com a consulta chave. Nesse caso é verificado se a consulta retorna o mesmo resultado da consulta chave. Exemplo:

yarn start $relax_host $relax_port $relax_database query_examples/5/qtrue.txt query_examples/5/qchave.txt

Esta função vai retornar 0 se a consulta é inválida ou 1 se é válida.

Para a função executarECompararConsultaPRO, devem ser passados os mesmos parâmetros da executarECompararConsulta seguido de dois parâmetros 0 ou 1, que indicam a necessidade ou não de verificar os nomes das colunas(se for 0, a consulta é válida se retorna os mesmos dados com nomes de coluna diferentes) e a ordem das tuplas(se for 0, a consulta é válida se retorna os mesmos dados(linhas/tuplas) mas em ordem diferente da chave). Exemplo:

yarn start $relax_host $relax_port $relax_database query_examples/5/qtrue.txt query_examples/5/qchave.txt 1 0

Esta função vai retornar 0 se a consulta é inválida ou 1 se é válida.


## Testes

Para executar os testes, foram incluídos 5 diretórios, cada um com um arquivo db.config. Para rodar:

N é o diretporio do exemplo, pode ser 1,2, ... ,5:

source query_examples/{N}/db.config

Cada exemplo tem um arquivo qtrue.txt com uma consulta correta e um qerror.txt com consulta inválida. Nos casos em que se aplica, existe um qchave.txt.

Exemplo de verificarConsulta. File pode ser qtrue.txt ou qerror.txt:

yarn start $relax_host $relax_port $relax_database query_examples/{N}/{File}

Exemplo de executarECompararConsulta. File pode ser qtrue.txt ou qerror.txt:

yarn start $relax_host $relax_port $relax_database query_examples/{N}/{File} query_examples/{N}/qchave.txt

Exemplo de executarECompararConsultaPRO. File pode ser qtrue.txt ou qerror.txt. number pode ser 0 ou 1:

yarn start $relax_host $relax_port $relax_database query_examples/{N}/{File} query_examples/{N}/qchave.txt {number} {number}


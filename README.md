# Repositório do Desafio de Projeto sobre GIT/Github da DIO
desafio de projeto sobre git/github

# Introdução ao Git
## Entendendo o que é Git e sua importância
  Linus Torvalds
  criador do Linux
  controle de versão 
  armazenamento em nuvem
  trabalho em equipe
  melhorar seu código
  reconhecimento

# Navegação via Command Line Interface e Instalação
## Comandos básicos para um bom desempenho no terminal

GUI X CLI

windows
cd
dir
mkdir
del/rmdir

unix
cd
ls
mkdir
rm -rf

cmd = terminal do windows na pasta padrão
wsfl = windows subsystem for linux = terminal do linux
dir = comando que lista todas as pastas do usuário 
ls = comando que lista todas as pastas contidas no diretório do sistema linux
cd = change directory = comando que possibilita navegar por todas as pastas 
cls = clear screen = comando que limpa o terminal windows
clear ou ctrl + L = comando que limpa o terminal linux 
tab = tecla que completa o nome de arquivos ao clicar
mkdir = make directory = comando que cria pastas
del/rmdir = comando que deleta arquivos criados
echo = comando que repete 

# Entendendo com o Git funciona por baixo dos panos
## Tópicos fundamentais para entender o funcionamento do Git
  SHA1
    SHA significa Secure Hash Algorithm (Algoritmo de Hash Seguro), é um conjunto de funções hash criptográficas projetadas pela NSA (Agência de Segurança Nacional dos EUA)
    a encriptação gera conjunto de caracteres identificador de 40 dígitos
    é uma forma curta de representar um arquivo
  objetos fundamentais
  sistema distribuído
  segurança

# Objetos internos do Git
  objetos fundamentais
    blobs (\0)
      o blob é um objeto que contém metadados do GIT, que são o tipo do objeto,         tamanho da string, tamanho do arquivo;
      a blob é um objeto que encapsula comportamentos de diretórios, sendo usado         para apontar para diretórios que contêm arquivos e por consequência apontar       para arquivos também   
    trees
      o objeto tree ou árvore armazena blobs, é uma crescente: sendo o blob o           bloco básico de composição
      a tree armazena e aponta para tipos de blobs diferentes, e um outro tipo de       estrutura de dados, que são os commits 
      a tree também contém metadados e possui a \0, que aponta para um blob que         tem um sha1, e a tree guarda o nome desse arquivo 
      a tree responsável por montar toda a estrutura e onde está localizado os           arquivos, apontando tanto para blob, quanto para outras trees 
      uma tree pode apontar para outra tree, da mesma forma que dentro de um             diretório, pode ter outro diretório, e à tree tem um sha1 desse metadado
      os blobs possuem o sha1 do arquivo, a tree aponta para a blob e tem o sha1         encriptado ali os metadados da tree; ao mudar alguma coisa em um arquivo,         que a tree esteja apontando, quando ela gerar o sha1 desses metadados, o           sha1 do blob vai ter mudado e vai refletir o sha1 da tree; consequentemente       mudando toda a estrutura, toda a leitura de encriptação da árvore, estrutura       e objeto
    commits
      objeto que junta tudo, dando sentido para as alterações feitas
      o commit aponta para uma árvore, aponta para um parente, ou seja, ele aponta       para o último commit realizado antes dele; ele aponta para um autor e uma         mensagem também
      ao escrever uma mensagem nesse objeto commit, ele explica e dá significado         para esses arquivos, dentro dessas pastas, esse objeto também é o nome do         autor (a pessoa que está fazendo o commit)  
      o commit apresenta um timestamp, um carimbo de tempo, ele leva a data e hora       de sua criação 
      esse objeto possui um sha1, uma encriptação, a geração de um hash de 40           caracteres identificador, dos seus metadados
      a mudança de uma blob interfere na mudança de uma árvore que,                     consequentemente, reflete no commit também, assegurando a mudança em toda a       linha do tempo 
    revisão
      os blobs são arquivos, que são o sha1 desses arquivos 
      a tree aponta respectivamente para o blob com seu sha1, e a tree armazena o       nome desses arquivos
      o commit dá significado para todo esse conjunto de alterações feitas, que         aponta para a tree, que aponta para o blob; o commit tem o autor, e tem           vários metadados

# Primeiros Comandos com Git
## Iniciando o Git e criando um commit
  iniciar o git
  iniciar o versionamento 
  criar um commit
    git init
    git add
    git commit
  a flag “-a” mostra pastas ocultas
  adicionando um arquivo
    o arquivo markdown(.mt) é uma forma mais “humana” de se escrever um arquivo       html sem entender de fato como ele funciona
      o arquivo html é um esqueleto, estrutura básica de qualquer página na web

# Ciclo de Vida dos Arquivos no Git
## Passo a passo no ciclo de vida
  git init
    o comando git init, além de criar a pasta “.git” ela inicia um conceito do git     chamado repositório
    ao usar git init, se cria um repositório dentro de um diretório, dentro de uma     pasta
  tracked ou untracked 
    dentro de tracked, dentro dos arquivos que são rastreáveis pelo git, ele pode     se dividir em um ciclo de três estágios diferentes:
      unmodified, é o arquivo que ainda não foi modificado
      modified é o arquivo unmodified que sofreu modificação, ao abrir o arquivo         de texto e alterar alguma coisa, ele muda automaticamente de unmodified para       modified 
      staged é onde ficam os arquivos que estão se preparando para poder fazer           parte de um outro tipo de agrupamento, parte de um commit
    o outro agrupamento é formado por untracked, que são os arquivos que o git         ainda não tem conhecimento, e tracked que são os arquivos que o git tem           conhecimento 
    os repositórios do git init são divididos em dois ambientes
      o ambiente de desenvolvimento (tudo o que está na máquina)
        working directory
        staging area
        local repository
          os arquivos irão transitar entre working directory e staging area 
          tudo o que está no repositório local deve estar commitado, caso                   contrário, não é possível movimentar o arquivo para o repositório                 remoto, pois o repositório local é composto por commits
    o servidor
      remote repository
git status
  comando que ajuda a monitorar os status dos arquivos, ou seja, irá dizer se o     arquivo está em untracked, modified ou staged

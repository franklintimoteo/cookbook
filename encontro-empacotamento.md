
# Table of Contents

1.  [Keywords](#org09e04f4):empacotamento:encontro:
2.  [Encontro empacotamento](#org12aab8a)
        1.  [Dicas](#org0ca8aac)
3.  [debian/watch](#org4f39393):watch:debian:
4.  [Unindo commit com git rebase](#org7d6afc1):rebase:git:
5.  [Alterando frase do último commit](#org791c371):commit:
6.  [Fazendo ITA - email sem título](#orgcd7cdf7):ITA:email:
7.  [Enviando para o mentors](#org104e8db)
    1.  [Fazendo correções no upstream](#org10548cc)
8.  [Passo a passo do Nilson](#orgd9254a0)
9.  [Encontro <span class="timestamp-wrapper"><span class="timestamp">&lt;2022-05-19 qui&gt;</span></span>](#orgb92211a)
        1.  [Adotar pacote que não está sob controle de versão](#orgd68c1a3)

<span class="timestamp-wrapper"><span class="timestamp">&lt;2022-05-17 ter&gt;</span></span>


<a id="org09e04f4"></a>

# Keywords     :empacotamento:encontro:


<a id="org12aab8a"></a>

# Encontro empacotamento


<a id="org0ca8aac"></a>

### Dicas

-   Sempre anotar as dificuldades que teve
-   Enviar os links que podem ser úteis para o DD sobre seu pacote
-   Pegar relação de todos DD do Brasil
-   Se inscreva nas mailinglists desejadas
    -   <https://www.debian.org/MailingLists/subscribe>
        -   Exemplos:
        -   package-sponsorship-requests
        -   debian-python

Quando o pacote já está no salsa

    gbp clone vcsgit:clap

Criar uma branch

    git switch -c franklintimoteo/1 debian/master

Após fazer as alterações

    # alterar copyright com seu nome em maintener
    git add debian/copyright
    git commit -a
    - Na primeira linha colocar d/copyright: Include name new maintainer. 
    
    # alterar seu nome em maintener em control 
    
    criar tag -a 0.14.0-3

Após fazer todas alterações e git commit

    gbp dch


<a id="org4f39393"></a>

# debian/watch     :watch:debian:

    version=4
    https://github.com/marekjm/clap/tags .*/tags/v?@ANY_VERSION@@ARCHIVE_EXT@
    marekjm -  é o nome do usuário
    clap - nome do pacote


<a id="org7d6afc1"></a>

# Unindo commit com git rebase     :rebase:git:

    git rebase -i HEAD~3
    - Uni os commits da HEAD até os 3 últimos commits, altere o 3 para quantidade desejada.
    - Vai aparecer duas frases começando com pick, altere a segunda para squash, salve feche para continuar
    - A próxima tela mostra as mensagens dos commits reorganize para ser somente 1 commit, salve e feche


<a id="org791c371"></a>

# Alterando frase do último commit     :commit:

    git commit --amend


<a id="orgcd7cdf7"></a>

# Fazendo ITA - email sem título     :ITA:email:

-   Colocar no título

retitle 977671 ITA: clap &#x2013; command line arguments parser
owner 977671 !

-   Enviar para

control@bugs.debian.org


<a id="org104e8db"></a>

# Enviando para o mentors

    dput mentors ../clap_0.14.0-3_amd64.changes 


<a id="org10548cc"></a>

## Fazendo correções no upstream

    quilt - auxilia na criação do path
    
    debian/patches/series
    quilt new 01-fix-mvprintw.patch
    quilt add src/cui.cpp
    edita arquivo e salva
    quilt header -e coloca uma cabeçalho de erro
    	Description: aconteceu algum erro
    	Author: Franklin Santos
    
    quilt refresh - finaliza o patch
    
    quilt pop -a # disfaz todos patchs deixando o arquivo do upstream original
    
    quilt push -a # aplica os patchs para nos permitir alterar os arquivos novamente
    quilt refresh


<a id="orgd9254a0"></a>

# Passo a passo do Nilson

1.  gbp clone vcsgit:xli

xli é nome do pacote que já está sob controle de versão)
    ou
gbp clone git@salsa.debian.org:debian/xli.git (caso o pacote no repositório não tivesse os campos Vcs-\* preenchidos tem)gbp	

1.  git switch -c nilson/1 debian/master (cria um nova branch)

2.  gbp buildpackage ou  gbp export-orig   (gerar o orig.tar.gz)

git commit
git commit

1.  gbp dch (gera o debian/changelog automaticamente com todo os commits)

2.  dch -r (pra marcar como pronto (s/UNRELEASED/unstable/)

3.  git commit debian/changelog ((Finalize changelog for 1.8-2 unstable upload)

4.  git push


<a id="orgb92211a"></a>

# Encontro <span class="timestamp-wrapper"><span class="timestamp">&lt;2022-05-19 qui&gt;</span></span>


<a id="orgd68c1a3"></a>

### Adotar pacote que não está sob controle de versão

    dget linkarquivo.dsc
    gbp import-dc nome-pacote.dsc
    gbp import-orig namepacote.dsc
    dch

    Franklin chave GPGhttps://keys.openpgp.org/upload/Fo91DB0_RXKpLksKtkl7Bx0m15NI1AyT1S0W_EHRJ-Ok85_oCz8umBEwx4xDQHM1UwB9wiIXUMF5DeNcohYzRLZI0BHOmgABuHrTFzxWFwUMLBXze0F_7RBKcXB1oI4I3YyAwawmVkeTzc66ENp4lnMyCB86IkWMkk0OEPpU8U0SwQe4QGmEhl1sVi05OM8O3maYJKhlgxyWrEiTzohJSjGJ5QAPGQ


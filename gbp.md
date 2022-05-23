
# Table of Contents

1.  [Repository layout](#orgc96064d)
2.  [Workflow](#org62fa872)
3.  [Importando Sources](#org913ef53)

<https://honk.sigxcpu.org/projects/git-buildpackage/manual-html/>

*git-buildpackage*


<a id="orgc96064d"></a>

# Repository layout

debian-branch - branch padrão
upstream-branch - branch para fazer um pull ou importar
pritine-tar - guarda informações adicionais para recriar o tarball original do upstream-branch. (instalar **pristine-tar**)
patch-queue - pode haver mais de uma. Branch para colocar os patchs. (administrada por **gbp pq**)

Você é livre para trabalhar com outro layout de repositório. Por exemplo nmu, backports, stables, dfsg, snapshots.
Recomendação de layout:

-   debian/release
-   upstream/latest
-   dfsg/latest


<a id="org62fa872"></a>

# Workflow

1.  gbp import-dsc - importa o pacote na debian branch e upstream branch.
2.  desenvolva, teste, commit mudanças. Você sempre pode usar gbp buildpackage ( use &#x2013;git-ignore-new para não precisar commitar mudanças)
3.  opcionalmente você pode criar entradas debian changelog com **gbp dch** e criar snapshot para testes com **&#x2013;snapshot**
4.  **gbp buildpackage &#x2013;git-tag** isto cria uma tag e você pode voltar para versão anterior quando quiser.
5.  quando o upstream não está usando git, você pode importar a nova versão via **gbp import-orig** dentro da upstream-branch. Por padrão vai tentar fazer um merge do upstream com a branch debian. &#x2013;no-merge para pular.


<a id="org913ef53"></a>

# Importando Sources


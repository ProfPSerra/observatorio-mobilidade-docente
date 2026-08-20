# Guia de Publicação no GitHub Pages

## Observatório Estatístico e Longitudinal da Mobilidade Docente — v6

Este guia descreve a forma mais simples de disponibilizar publicamente a aplicação através do **GitHub Pages**.

## 1. Pré-requisitos

É necessário:

- uma conta GitHub;
- um repositório GitHub;
- os ficheiros desta pasta, em especial `index.html`.

A aplicação é estática e autónoma: não necessita de base de dados, servidor de aplicação ou processo de compilação.

## 2. Nome recomendado do repositório

Sugestão:

`observatorio-mobilidade-docente`

Nesse caso, o endereço público ficará normalmente com esta estrutura:

`https://SEU-UTILIZADOR.github.io/observatorio-mobilidade-docente/`

## 3. Criar o repositório

1. Entrar em https://github.com/
2. Selecionar **New repository**.
3. Definir o nome `observatorio-mobilidade-docente`.
4. Escolher **Public**, caso se pretenda utilizar GitHub Pages gratuitamente num repositório público.
5. Criar o repositório.

## 4. Carregar os ficheiros

Na página do novo repositório:

1. selecionar **Add file → Upload files**;
2. carregar o conteúdo desta pasta;
3. confirmar que `index.html` fica na raiz;
4. efetuar o commit.

Estrutura mínima:

```text
index.html
README.md
LICENSE.md
.nojekyll
```

Estrutura recomendada:

```text
index.html
README.md
FICHA_METODOLOGICA.md
GUIA_PUBLICACAO_GITHUB_PAGES.md
LICENSE.md
LICENSE-CODE-MIT.txt
CITATION.cff
CHANGELOG.md
.nojekyll
docs/
  Manual_Observatorio_Estatistico_Longitudinal_Mobilidade_Docente_v6.pdf
  Manual_Observatorio_Estatistico_Longitudinal_Mobilidade_Docente_v6.docx
```

## 5. Ativar o GitHub Pages

1. Abrir o repositório.
2. Selecionar **Settings**.
3. No menu lateral, abrir **Pages**.
4. Em **Build and deployment**, escolher **Deploy from a branch**.
5. Em **Branch**, selecionar `main`.
6. Selecionar `/ (root)` como pasta.
7. Guardar.

O GitHub Pages utilizará o `index.html` como página de entrada.

A publicação pode demorar alguns minutos após um commit.

## 6. Confirmar a publicação

Voltar a **Settings → Pages**. Quando o deployment estiver concluído, o GitHub apresentará a ligação pública do site.

Exemplo:

`https://SEU-UTILIZADOR.github.io/observatorio-mobilidade-docente/`

Testar pelo menos:

- carregamento da aplicação;
- mudança de ano;
- pesquisa de escola na Rede;
- pesquisa por código no painel Escolas;
- série longitudinal individual;
- botões de download;
- manual e documentação no repositório.

## 7. Atualizar a aplicação

Para publicar uma nova versão:

1. substituir `index.html` pela versão nova;
2. atualizar `CHANGELOG.md`;
3. atualizar a versão no README, manual e `CITATION.cff`;
4. fazer commit.

O GitHub Pages voltará a publicar automaticamente o conteúdo do branch selecionado.

## 8. Releases

Recomenda-se criar uma **GitHub Release** para versões estáveis, por exemplo:

`v6.0.0`

Procedimento:

1. abrir **Releases** no repositório;
2. selecionar **Draft a new release**;
3. criar uma tag como `v6.0.0`;
4. atribuir título e notas de versão;
5. publicar.

Isto ajuda a preservar uma versão concreta enquanto o site continua a evoluir.

## 9. DOI com Zenodo

Depois de o repositório estar estável, pode ligar-se o GitHub ao Zenodo:

1. criar/entrar numa conta Zenodo;
2. ligar a conta GitHub;
3. sincronizar os repositórios;
4. ativar o repositório do Observatório;
5. criar uma nova release no GitHub.

O Zenodo pode arquivar a release e criar um DOI para a versão publicada.

Depois do DOI existir:

- atualizar `CITATION.cff`;
- atualizar o README;
- acrescentar o DOI ao manual e à ficha metodológica.

## 10. Domínio próprio — opcional

Mais tarde poderá associar-se um domínio, por exemplo:

`observatoriomobilidadedocente.pt`

Não é necessário para a primeira publicação. Recomenda-se começar com o endereço `github.io` e apenas migrar para domínio próprio quando o projeto estiver estabilizado.

## 11. Boas práticas antes de tornar o repositório público

Antes de publicar:

- confirmar que não existem nomes de docentes ou outros dados pessoais desnecessários no HTML;
- confirmar que os identificadores longitudinais são anonimizados;
- testar todas as exportações;
- confirmar a versão do manual;
- rever `LICENSE.md`;
- verificar o texto de ausência de endosso institucional;
- garantir que as fontes de dados estão devidamente identificadas na metodologia;
- manter uma cópia local da versão publicada.

## 12. Segurança e privacidade

Um site GitHub Pages é público. Não deve ser utilizado para alojar informação confidencial ou dados pessoais não destinados à divulgação pública.

Mesmo que um ficheiro não tenha ligação visível na interface, se estiver no repositório público pode ser acessível por terceiros.

## 13. Recomendação de versionamento

Utilizar versionamento semântico para a aplicação:

- `v6.0.0` — primeira publicação pública da versão descritiva;
- `v6.0.1` — correção pequena sem alteração metodológica;
- `v6.1.0` — nova funcionalidade compatível;
- `v7.0.0` — alteração estrutural/metodológica significativa.

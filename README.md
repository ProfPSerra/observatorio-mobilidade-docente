# Observatório Estatístico e Longitudinal da Mobilidade Docente

**Versão pública v6 — Consulta Descritiva**  
**Período analisado:** 2016/2017–2026/2027  
**Autores:** Prof. Manuel P. Fernandes e Prof. Pedro Serra

O **Observatório Estatístico e Longitudinal da Mobilidade Docente** é uma aplicação web estática e autónoma destinada à exploração descritiva e longitudinal da Mobilidade Interna de docentes. A aplicação transforma listas administrativas anuais em indicadores comparáveis por ano, grupo de recrutamento, tipo de candidato e escola, permitindo observar mobilidade, permanência, pressão de entrada e saída, redes escola→escola, persistência longitudinal e trajetórias anonimizadas.

> **Âmbito da versão v6:** esta versão foi deliberadamente concebida para **consulta descritiva**, sem painéis de Inferência e Conclusões, de modo a reduzir o risco de orientar previamente a interpretação do utilizador. A aplicação disponibiliza dados e indicadores para exploração; análises inferenciais devem ser realizadas externamente e com hipóteses previamente definidas.

## Acesso rápido

O ficheiro `index.html` contém a aplicação completa. Por ser uma aplicação estática, pode ser:

- aberta localmente num navegador;
- publicada diretamente em **GitHub Pages**;
- alojada noutro serviço de hosting estático compatível com HTML.

Quando este repositório estiver publicado no GitHub Pages, o endereço terá normalmente a forma:

`https://<utilizador>.github.io/<nome-do-repositorio>/`

## Principais painéis

A versão v6 inclui:

1. **Visão geral** — universo anual, colocação, não colocação, migrações e permanências;
2. **Rede** — rede dirigida de migrações efetivas entre escolas;
3. **QA/QE vs QZP** — composição e indicadores comparativos descritivos;
4. **Pressão e rankings** — E, S, M, PS, PE, SM e TNC, com exportação integral;
5. **Escolas** — tabela integral por código escolar, com pesquisa por código, nome e concelho;
6. **Longitudinal** — IPPS, IPPE, volatilidade, tendência, tipologias e corredores persistentes;
7. **Trajetórias** — painéis anonimizados docente×grupo, TPR, TME, estados e recorrência;
8. **Markov** — transições empíricas P/M/NC;
9. **Qualidade** — cobertura, auditoria e heatmap grupo×ano;
10. **Metodologia** — fórmulas, regras de construção e limitações.

## Princípios metodológicos centrais

### 1. Chave de cruzamento

As listas são cruzadas preferencialmente por:

`Número de Utilizador + Grupo de Recrutamento`

### 2. Regra de inclusão

O universo analítico anual segue:

`Ordenação ∩ (Colocados ∪ Não colocados)`

Candidatos presentes apenas na lista de ordenação, sem resultado final correspondente, não são automaticamente classificados como não colocados.

### 3. Identidade das escolas

A identidade de uma escola é definida pelo **código**, nunca apenas pelo nome:

`Identidade da escola = Código`

A aplicação preserva códigos históricos/especiais e utiliza designações canónicas para apresentação quando existe correspondência no cadastro de referência.

### 4. Escola de origem

Para QZP, o código `QZP.xx` não é tratado como escola de origem. A escola concreta é recuperada, sempre que possível, através do campo de colocação/provimento da **Lista Definitiva de Ordenação**.

### 5. Não colocados

Para comparabilidade dos indicadores escolares, um não colocado conta como:

- 1 saída administrativa da escola de origem;
- 1 entrada administrativa de regresso à mesma origem;
- **0 arestas na rede**, porque não ocorreu migração efetiva.

## Indicadores principais

| Indicador | Fórmula / definição |
|---|---|
| `E` | Entradas |
| `S` | Saídas |
| `M` | `E + S` |
| `PS` | `S / (E + S) × 100` |
| `PE` | `E / (E + S) × 100` |
| `SM` | Migrações recebidas − migrações originadas |
| `TNC` | `NC / S × 100` |
| `IPPS` | Anos ativos com `PS > 60%` / anos ativos |
| `IPPE` | Anos ativos com `PE > 60%` / anos ativos |
| `TPR` | Anos de participação / anos observáveis |
| `TME` | Mudanças / participações |

O **limiar mínimo M** é utilizado em rankings e tipologias longitudinais para evitar conclusões baseadas em volumes muito reduzidos. Não elimina escolas da base nem da tabela integral.

## Manual

A documentação completa encontra-se em:

- `docs/Manual_Observatorio_Estatistico_Longitudinal_Mobilidade_Docente_v6.pdf`
- `docs/Manual_Observatorio_Estatistico_Longitudinal_Mobilidade_Docente_v6.docx`

A ficha metodológica resumida encontra-se em `FICHA_METODOLOGICA.md`.

## Estrutura recomendada do repositório

```text
.
├── index.html
├── README.md
├── FICHA_METODOLOGICA.md
├── GUIA_PUBLICACAO_GITHUB_PAGES.md
├── LICENSE.md
├── LICENSE-CODE-MIT.txt
├── CITATION.cff
├── CHANGELOG.md
├── .nojekyll
└── docs/
    ├── Manual_Observatorio_Estatistico_Longitudinal_Mobilidade_Docente_v6.pdf
    └── Manual_Observatorio_Estatistico_Longitudinal_Mobilidade_Docente_v6.docx
```

## Publicação no GitHub Pages

O procedimento mais simples é:

1. criar um repositório público no GitHub, por exemplo `observatorio-mobilidade-docente`;
2. carregar todos os ficheiros desta pasta para a raiz do repositório;
3. abrir **Settings → Pages**;
4. em **Build and deployment**, escolher **Deploy from a branch**;
5. selecionar o branch `main` e a pasta `/ (root)`;
6. guardar e aguardar a publicação.

O GitHub Pages procura um `index.html` no diretório publicado e pode demorar alguns minutos a atualizar após cada alteração.

Ver instruções detalhadas em `GUIA_PUBLICACAO_GITHUB_PAGES.md`.

## Transparência e reprodutibilidade

A filosofia do Observatório é:

> **O painel pode resumir; o download deve permitir auditar.**

Os gráficos apresentados no ecrã podem ser limitados por legibilidade, mas a aplicação permite descarregar listas e universos integrais sempre que essa funcionalidade está disponível.

## Privacidade e utilização responsável

- as trajetórias individuais são apresentadas através de identificadores anonimizados;
- o Observatório não deve ser utilizado para inferir irregularidade jurídica a partir de um padrão estatístico;
- tipologias de escolas são **perfis estatísticos**, não classificações de qualidade;
- indicadores de pressão não representam diretamente a percentagem do corpo docente total que abandona uma escola;
- alterações legislativas e administrativas entre anos devem ser consideradas na interpretação longitudinal.

## Licenciamento

Este repositório utiliza licenciamento por componentes:

- **código original da aplicação:** MIT License;
- **documentação original:** Creative Commons Attribution 4.0 International (CC BY 4.0);
- **dados administrativos de origem, designações oficiais e materiais de terceiros:** não são relicenciados por este repositório; mantêm os direitos, condições e proveniência aplicáveis às respetivas fontes.

Consultar `LICENSE.md` para o âmbito exato.

## Como citar

Uma forma provisória de citação é:

> Fernandes, M. P., & Serra, P. (2026). *Observatório Estatístico e Longitudinal da Mobilidade Docente: versão pública v6 — Consulta Descritiva* [Aplicação web].

O ficheiro `CITATION.cff` permite ao GitHub apresentar automaticamente a opção **Cite this repository**. Após criar uma release e arquivá-la no Zenodo, deverá substituir-se a referência provisória pelo DOI atribuído.

## Aviso

O Observatório é um projeto independente de análise e monitorização. A disponibilização de códigos, designações ou resultados administrativos não implica afiliação, aprovação ou endosso por parte do Ministério da Educação, DGAE ou qualquer outra entidade pública.

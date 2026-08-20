# Ficha Metodológica

## Observatório Estatístico e Longitudinal da Mobilidade Docente

**Versão pública:** v6 — Consulta Descritiva  
**Período:** 2016/2017–2026/2027  
**Autores:** Prof. Manuel P. Fernandes e Prof. Pedro Serra  
**Natureza:** observatório estatístico, longitudinal e de redes baseado em dados administrativos publicados.

## 1. Objetivo

O Observatório procura transformar listas administrativas anuais da Mobilidade Interna em informação longitudinal comparável, permitindo estudar:

- mobilidade e permanência docente;
- pressão administrativa de entrada e saída nas escolas;
- migrações efetivas entre escolas;
- não colocação e mobilidade latente;
- diferenças descritivas entre QA/QE e QZP;
- persistência e volatilidade de padrões escolares;
- corredores de mobilidade;
- trajetórias anonimizadas docente×grupo;
- transições empíricas entre permanência, mudança e não colocação.

O Observatório distingue explicitamente:

`Estabilidade do vínculo ≠ estabilidade geográfica ≠ estabilidade organizacional da escola`

## 2. Fontes e unidade de análise

As fontes anuais utilizadas são, essencialmente:

1. **Lista Definitiva de Ordenação da Mobilidade Interna**;
2. **Lista Definitiva de Colocação da Mobilidade Interna**;
3. **Lista Definitiva de Não Colocação da Mobilidade Interna**;
4. cadastro auxiliar de códigos e designações de agrupamentos/escolas para harmonização da apresentação.

A unidade elementar da base anual corresponde a uma participação de um candidato num determinado **ano letivo × grupo de recrutamento**.

## 3. Chave de cruzamento

A chave preferencial de junção entre ordenação e resultado final é:

`Número de Utilizador + Grupo de Recrutamento`

Esta combinação reduz ambiguidades em situações em que um mesmo docente pode participar em mais de um grupo.

## 4. Regra de construção do universo anual

O universo analítico segue a regra:

`Ordenação ∩ (Colocados ∪ Não colocados)`

Assim:

- um candidato apenas presente na ordenação não é automaticamente classificado como não colocado;
- um resultado final sem correspondência segura na ordenação é identificado no controlo de qualidade e não é artificialmente reconstruído;
- exceções documentais são assinaladas explicitamente.

## 5. Escola de origem

A escola de origem é a escola concreta onde o candidato se encontrava colocado/provido antes do resultado final da MI.

Para candidatos QZP, um código do tipo `QZP.xx` representa uma zona e **não é considerado uma escola**. Sempre que possível, a origem escolar é recuperada através da informação existente na lista de ordenação.

Quando a origem não pode ser determinada de forma segura:

- o candidato pode permanecer na análise global, se o resultado final for válido;
- é assinalado como origem indisponível;
- não deve alimentar uma aresta escola→escola na rede.

## 6. Identidade e harmonização das escolas

A regra fundamental é:

`Identidade da escola = Código`

Não se fundem entidades apenas porque os nomes são semelhantes.

O cadastro auxiliar é utilizado para:

- apresentar designações canónicas;
- associar concelho e QZP de referência;
- detetar códigos históricos ou especiais;
- preservar entidades históricas sem as fundir automaticamente com códigos atuais.

## 7. Estados do candidato

Para um determinado ano:

- `P` — colocado na mesma escola de origem;
- `M` — colocado numa escola diferente;
- `NC` — não colocado;
- `?` — estado não determinável de forma segura em casos residuais.

## 8. Regra dos não colocados nos indicadores escolares

Para medir a pressão administrativa da MI, um não colocado é tratado como:

- 1 saída da escola de origem;
- 1 entrada de regresso à mesma escola.

Isto representa participação/mobilidade latente sem inventar migração efetiva.

Na rede, o não colocado **não cria aresta**, porque não houve deslocação escola→escola.

## 9. Indicadores escola × ano

### Entradas

`E_i,t = número de entradas administrativas na escola i no ano t`

### Saídas

`S_i,t = número de saídas administrativas da escola i no ano t`

### Movimento Total

`M_i,t = E_i,t + S_i,t`

### Pressão de Saída

`PS_i,t = S_i,t / (E_i,t + S_i,t) × 100`

### Pressão de Entrada

`PE_i,t = E_i,t / (E_i,t + S_i,t) × 100`

Quando `M > 0`:

`PS + PE = 100%`

### Saldo Migratório Efetivo

`SM_i,t = migrações recebidas_i,t − migrações originadas_i,t`

Apenas mudanças efetivas entre escolas entram neste cálculo.

### Taxa de Não Colocação Escolar

`TNC_i,t = NC_i,t / S_i,t × 100`

A TNC deve ser interpretada como indicador de **mobilidade latente** no universo da MI, não como taxa de retenção do corpo docente total da escola.

## 10. Limiar mínimo de movimento

Para rankings e tipologias longitudinais é utilizado um limiar mínimo:

`M ≥ N`

O valor de referência da aplicação é frequentemente `M ≥ 10`, mas o utilizador pode alterá-lo.

O limiar:

- reduz rankings dominados por percentagens extremas baseadas em 1–2 casos;
- não elimina escolas da base;
- não é aplicado à série histórica individual pesquisada no painel Longitudinal.

## 11. Indicadores QA/QE vs QZP

### Composição

`PQA = QA/QE em MI / total MI × 100`

`PQZP = QZP em MI / total MI × 100`

Estes indicadores descrevem a composição da MI e não a taxa de participação sobre o universo nacional de cada carreira.

### Mobilidade voluntária QA/QE

`IMV-QA = QA/QE na prioridade harmonizada de mobilidade voluntária / total QA/QE em MI × 100`

É um **proxy administrativo**, não uma medida da motivação psicológica individual.

### Diferença de não colocação

`INCD = NC% QA/QE − NC% QZP`

### Risco relativo descritivo de não colocação

`RR-NC = NC% QA/QE / NC% QZP`

### Permanência QZP

`IP-QZP colocados = QZP colocados na mesma escola / QZP colocados × 100`

`IP-QZP total = QZP colocados na mesma escola / total QZP em MI × 100`

## 12. Rede de mobilidade

Para cada ano é construída uma rede dirigida:

`G_t = (V, E_t)`

onde:

- `V` são códigos escolares;
- uma aresta `A → B` representa pelo menos uma migração efetiva da escola A para a escola B;
- a espessura da aresta é proporcional ao número de docentes nesse corredor;
- o tamanho do nó é proporcional ao movimento total da escola;
- a cor indica predominância de entrada, saída ou equilíbrio.

O limite gráfico de nós serve apenas para legibilidade. A pesquisa de uma escola específica tem prioridade e deve permitir localizar uma escola mesmo fora do conjunto inicialmente desenhado.

## 13. Indicadores longitudinais das escolas

Um **ano ativo** para a classificação longitudinal é um ano em que a escola satisfaz o limiar de movimento escolhido.

### Persistência de saída

`IPPS_i = anos ativos com PS_i,t > 60% / número de anos ativos`

### Persistência de entrada

`IPPE_i = anos ativos com PE_i,t > 60% / número de anos ativos`

### Volatilidade

`Vol_i = desvio-padrão de PS_i,t nos anos ativos`

### Tendência

É estimada pela inclinação de uma regressão linear simples de `PS` sobre o tempo nos anos ativos.

A tendência é descritiva e não substitui análise causal.

## 14. Tipologias longitudinais

A aplicação utiliza regras transparentes para atribuir perfis como:

- emissora persistente;
- recetora persistente;
- alta rotação;
- mobilidade latente elevada;
- volátil;
- estável/baixa rotação;
- misto.

As tipologias são **classificações estatísticas**, não avaliações da qualidade da escola.

Os limiares devem ser submetidos a testes de robustez.

## 15. Corredores persistentes

Para um corredor `A → B`:

`Persistência = anos em que o corredor aparece / anos do período selecionado × 100`

A referência inicial da aplicação considera persistente um corredor que:

- aparece em pelo menos 2 anos; e
- atinge uma percentagem mínima definida pelo utilizador, com valor de referência de 60%.

O limiar de 60% é heurístico e ajustável; recomenda-se comparar resultados com 50%, 70% e 80%.

## 16. Trajetórias longitudinais

A unidade utilizada é:

`Painel = docente anonimizado × grupo de recrutamento`

### Taxa de Participação Recorrente

`TPR = anos de participação / anos observáveis`

### Taxa de Mudança Efetiva

`TME = mudanças / participações`

### Índice de recorrência

A versão documentada utiliza um índice composto descritivo que combina participação, mudança, sequência consecutiva e diversidade de escolas. Deve ser lido como indicador exploratório, não como medida jurídica ou disciplinar.

### Elevada recorrência

A classificação de elevada recorrência é baseada no **percentil da distribuição observada**, com referência inicial em `P75` entre painéis com pelo menos duas participações.

P75 significa pertencer aproximadamente ao quartil superior; não significa índice igual a 75.

## 17. Markov

As transições entre anos consecutivos são agregadas numa matriz empírica de estados:

`P, M, NC`

Cada linha é normalizada para produzir probabilidades condicionais observadas, por exemplo:

`P(P no ano seguinte | P no ano atual)`

As probabilidades são descritivas e dependem do período e universo selecionados.

## 18. Heatmap de qualidade/cobertura

Cada célula representa:

`grupo de recrutamento × ano`

A cor pode representar:

- número absoluto de candidatos; ou
- percentagem do universo anual.

Uma célula clara ou zero não implica automaticamente falha de qualidade. Deve ser interpretada em conjunto com cobertura documental, alterações legislativas e dimensão do universo anual.

## 19. Controlo de qualidade

A preparação anual regista, sempre que possível:

- grupos presentes nas fontes;
- candidatos interpretados;
- colocados e não colocados;
- resultados sem correspondência;
- candidatos apenas na ordenação;
- códigos escolares não catalogados;
- origens indisponíveis;
- exceções de estrutura documental.

## 20. Privacidade e ética

- nomes individuais não são necessários na interface pública;
- trajetórias são apresentadas através de identificadores anonimizados;
- anomalia estatística não é sinónimo de irregularidade;
- escolas não devem ser rotuladas como “boas” ou “más” com base num único indicador;
- a publicação deve respeitar a proveniência e as condições aplicáveis aos dados administrativos de origem.

## 21. Âmbito da versão pública v6

A v6 é uma versão de **consulta descritiva**. Foram retirados da interface os painéis de:

- Inferência;
- Conclusões.

Esta decisão procura separar:

`exploração pública descritiva` de `interpretação científica inferencial`.

Testes estatísticos podem ser realizados externamente a partir dos dados exportados, com hipóteses e especificações previamente definidas.

## 22. Limitações

Entre as limitações principais encontram-se:

- o universo corresponde a participantes na Mobilidade Interna, não ao corpo docente total das escolas;
- alterações legislativas entre anos podem reduzir comparabilidade direta;
- PS/PE medem a composição do movimento observado, não turnover total;
- dados sobre vagas, preferências ordenadas e sequência completa de atribuição seriam necessários para análises causais mais fortes sobre compressão de oportunidades;
- códigos, agrupamentos e designações podem mudar no tempo;
- algumas exceções documentais exigem controlo específico por ano.

## 23. Reprodutibilidade

A metodologia segue o princípio:

> **O painel pode resumir; o download deve permitir auditar.**

Os resultados apresentados devem poder ser reconstruídos a partir das bases limpas e das regras documentadas.

## 24. Versão e citação

**Versão metodológica:** 2.0, agosto de 2026  
**Aplicação:** v6 — Consulta Descritiva

Citação provisória:

> Fernandes, M. P., & Serra, P. (2026). *Observatório Estatístico e Longitudinal da Mobilidade Docente: versão pública v6 — Consulta Descritiva* [Aplicação web].

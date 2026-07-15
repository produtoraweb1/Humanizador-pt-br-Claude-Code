# Humanizador

![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)
![Language](https://img.shields.io/badge/idioma-PT--BR-green.svg)
![Format](https://img.shields.io/badge/formato-Markdown-lightgrey.svg)

Um skill de agente, portátil e em Markdown puro, que remove sinais de escrita gerada por IA de textos em **português do Brasil** e devolve uma voz genuína ao texto. Sem build, sem dependências: o arquivo `SKILL.md` inteiro é a instrução.

Adaptação para PT-BR do projeto [Humanizer](https://github.com/blader/humanizer) (blader/humanizer, MIT), que por sua vez implementa o guia da Wikipédia ["Signs of AI writing"](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing). A versão original funciona bem para inglês, mas boa parte dos seus padrões (vocabulário, hifenização, Title Case) é específica daquela língua. Este repositório troca esses padrões por equivalentes reais do português brasileiro: gerundismo, conectivos automáticos, contaminação com português europeu, estrangeirismos, formatação numérica no padrão americano, e mais.

## Sumário

- [Instalação](#instalação)
- [Uso rápido](#uso-rápido)
- [Calibração de voz](#calibração-de-voz)
- [O que ele detecta](#o-que-ele-detecta-37-padrões)
- [Exemplos de prompts](#exemplos-de-prompts)
- [Sobre detectores de IA (leia antes de publicar em produção)](#sobre-detectores-de-ia)
- [Estrutura do repositório](#estrutura-do-repositório)
- [Como contribuir](#como-contribuir)
- [Créditos e referências](#créditos-e-referências)
- [Histórico de versões](#histórico-de-versões)
- [Licença](#licença)

## Instalação

### Manual (qualquer harness)

O artefato de execução é só o `SKILL.md`. Instale onde o seu harness espera diretórios de skill, ou copie o arquivo para uma pasta de skill existente.

Claude Code, por exemplo:

```bash
mkdir -p ~/.claude/skills/humanizador
cp SKILL.md ~/.claude/skills/humanizador/
```

### CLI de skills (cross-agent)

Depois de publicado no GitHub, também dá para instalar com a [skills CLI](https://github.com/blader/humanizer) genérica:

```bash
npx skills add <seu-usuario>/humanizador-pt-br
```

## Uso rápido

```
/humanizador

[cole o texto que soa como IA aqui]
```

ou, em prosa:

```
Humanize este texto: [seu texto]
```

Dez exemplos prontos, cobrindo todos os recursos do skill, estão em [`EXEMPLOS.md`](EXEMPLOS.md).

## Calibração de Voz

Forneça uma amostra da sua própria escrita para o skill imitar o seu ritmo, vocabulário e tiques em vez de devolver uma reescrita genérica:

```
/humanizador

Aqui vai uma amostra da minha escrita para calibrar a voz:
[2-3 parágrafos seus]

Agora humanize este texto:
[texto de IA]
```

Isso inclui preservar o uso de "tu" ou "você" conforme a amostra, em vez de normalizar tudo para o "você" padrão que a IA tende a usar.

## O que ele detecta (37 padrões)

Os 37 padrões estão catalogados nas tabelas abaixo. O skill também inclui uma seção sobre **perplexidade e burstiness** (as duas propriedades estatísticas que a maioria dos detectores mede), com técnicas editoriais, não trapaças, para variar naturalmente o ritmo do texto.

### Padrões de Conteúdo

| # | Padrão | Antes | Depois |
|---|--------|-------|--------|
| 1 | Inflação de significância | "consolidando-se como um marco na evolução de..." | "foi fundado em 1993 para reunir dados regionais" |
| 2 | Name-dropping de notoriedade | "citado por Folha, G1, UOL e diversos portais" | "Em entrevista de 2024, ela defendeu que..." |
| 3 | Análises superficiais em gerúndio | "simbolizando... reforçando... consolidando..." | Remova ou expanda com fontes reais |
| 4 | Linguagem promocional | "encravada no coração pulsante da região" | "é um município na região de..." |
| 5 | Atribuições vagas | "especialistas acreditam que é crucial" | "segundo levantamento de 2019 de..." |
| 6 | Desafios formulaicos | "apesar dos desafios... segue prosperando" | Fatos concretos sobre os desafios reais |

### Padrões de Linguagem e Gramática

| # | Padrão | Antes | Depois |
|---|--------|-------|--------|
| 7 | Vocabulário de IA | "adicionalmente... nesse contexto... consolidando" | "também... continua comum" |
| 8 | Contaminação com português europeu | "estou a analisar o ficheiro no ecrã" | "estou analisando o arquivo na tela" |
| 9 | Fuga da cópula | "configura-se como... apresenta... conta com" | "é... tem" |
| 10 | Paralelismos negativos / negações à cauda | "não é apenas X, é Y", "sem adivinhação" | Diga o ponto direto |
| 11 | Regra de três | "inovação, colaboração e excelência" | Use o número natural de itens |
| 12 | Troca excessiva de sinônimos | "protagonista... personagem... figura... herói" | "protagonista" (repita quando for mais claro) |
| 13 | Falsas amplitudes | "do Big Bang à matéria escura" | Liste os temas diretamente |
| 14 | Voz passiva / frases sem sujeito | "nenhuma configuração é necessária" | Nomeie quem faz a ação quando isso ajuda |
| 15 | Estrangeirismos e calques | "mindset orientado a dados... insights" | "decisões baseadas em dados... ideias" |
| 16 | Gerundismo de atendimento | "vou estar verificando e estarei retornando" | "vou verificar e retorno" |

### Padrões de Estilo

| # | Padrão | Antes | Depois |
|---|--------|-------|--------|
| 17 | Travessões | "instituições — não o povo — mas isso persiste—" | Corte: pontos, vírgulas, dois-pontos ou parênteses |
| 18 | Excesso de negrito | "**OKRs**, **KPIs**, **BMC**" | "OKRs, KPIs, BMC" |
| 19 | Listas com cabeçalho inline | "**Desempenho:** o desempenho melhorou" | Converta para texto corrido |
| 20 | "Title Case" (do inglês) em títulos | "Negociações Estratégicas E Parcerias" | "Negociações estratégicas e parcerias" |
| 21 | Emojis | "🚀 Fase de Lançamento: 💡 Insight:" | Remova os emojis |
| 22 | Aspas curvas | aspas tipográficas (“…”) | aspas retas ("…") |
| 23 | Formatação numérica e de data americana | "R$ 1,250,000", "3.5%", "03/08/2026" | "R$ 1.250.000", "3,5%", "08/03/2026" |
| 24 | Tropos persuasivos de autoridade | "no fundo, o que realmente importa é..." | Diga o ponto direto |
| 25 | Anúncios de sinalização | "vamos mergulhar nisso", "eis o que você precisa saber" | Comece pelo conteúdo |
| 26 | Cabeçalhos fragmentados | "## Desempenho" + "Velocidade importa." | Deixe o título falar por si |
| 27 | Escrita ancorada em diffs | "esta função foi adicionada para substituir..." | Descreva o que ela faz, não o que mudou |
| 28 | Frases de efeito / drama staccato | "Não tinha preferência. Nem prior. Nem nostalgia." | Varie o tamanho das frases, afirmações concretas |
| 29 | Fórmulas de aforismo | "A simetria é a linguagem da confiança" | Troque a fórmula pela afirmação real |
| 30 | Aberturas retóricas falsas | "Sinceramente? Depende..." | Remova a falsa espontaneidade |

### Padrões de Comunicação

| # | Padrão | Antes | Depois |
|---|--------|-------|--------|
| 31 | Sobras de chatbot | "Espero ter ajudado! Me avise se..." | Remova por completo |
| 32 | Disclaimers de corte / preenchimento especulativo | "não há informações amplamente disponíveis..." | Encontre fontes ou remova |
| 33 | Tom bajulador | "Ótima pergunta! Você está certíssimo!" | Responda direto |

### Preenchimento e Hedging

| # | Padrão | Antes | Depois |
|---|--------|-------|--------|
| 34 | Frases de preenchimento | "A fim de", "devido ao fato de que" | "Para", "porque" |
| 35 | Hedging excessivo | "poderia potencialmente possivelmente" | "pode" |
| 36 | Conclusões genéricas | "o futuro é promissor" | Planos ou fatos específicos |

### Padrões Estruturais (Macro)

| # | Padrão | Antes | Depois |
|---|--------|-------|--------|
| 37 | Estrutura de parágrafo uniforme | todo parágrafo com 4 frases do mesmo tamanho | parágrafos de tamanhos variados, alguns de uma frase só |

O `SKILL.md` também define uma auditoria final ("isso ainda parece gerado por IA?") com uma segunda reescrita, e uma seção de falsos positivos que protege registros formais legítimos (jurídico, acadêmico, institucional) de serem "corrigidos" sem necessidade.

## Exemplos de Prompts

Veja [`EXEMPLOS.md`](EXEMPLOS.md) para dez prompts prontos, cobrindo uso básico, calibração de voz (inline e por arquivo), e-mail corporativo, post pessoal, resumo acadêmico, documentação técnica, atendimento ao cliente, modo de diagnóstico sem reescrita, e detecção de contaminação com português europeu.

## Sobre Detectores de IA

Antes de usar este skill esperando "passar" em algum detector específico, vale entender como essas ferramentas funcionam e onde elas falham. Isso evita expectativa errada e uso irresponsável.

**Como funcionam:** detectores como GPTZero, Turnitin, Originality.ai e Copyleaks não identificam autoria. Eles estimam uma probabilidade a partir de dois sinais estatísticos principais, **perplexidade** (o quão previsível é cada palavra, para um modelo de linguagem) e **burstiness** (o quanto o tamanho das frases varia), combinados com um classificador treinado em milhões de amostras rotuladas.

**Por que erram tanto:**
- Uma [análise de Weber-Wulff et al. (2023)](https://arxiv.org/abs/2306.15666) encontrou a maioria dos detectores testados com menos de 80% de acurácia em amostras diversas.
- O estudo mais citado sobre o tema, [Liang et al. (2023), "GPT detectors are biased against non-native English writers"](https://arxiv.org/abs/2304.02819) (publicado na revista *Patterns*), testou 91 redações do TOEFL escritas por humanos não nativos em sete detectores: 61,3% foram marcadas como geradas por IA, 97,8% foram sinalizadas por pelo menos um detector, e 19,8% foram classificadas erradamente por todos os sete ao mesmo tempo. Todos os textos eram 100% humanos.
- A Turnitin já divulgou uma taxa de falso positivo abaixo de 1%; uma reportagem do Washington Post, testando de forma independente, encontrou uma taxa muito mais alta numa amostra menor. Isso ilustra o quanto esse número varia conforme quem testa e como.
- Esses erros recaem de forma desproporcional sobre quem escreve em uma segunda língua, tem um estilo mais formal ou simples, ou é neurodivergente: exatamente o tipo de escrita que também tende a ter baixa perplexidade e baixo burstiness sem qualquer IA envolvida.

**O que isso significa na prática:** nenhuma ferramenta de humanização, esta incluída, pode honestamente prometer zero detecção contra qualquer detector, presente ou futuro. Seria uma corrida armamentista contra alvos que mudam a cada atualização. O objetivo real deste skill é remover tiques mecânicos e devolver uma voz genuína ao texto. Na prática, um texto bem editado tende a passar despercebido, mas isso é consequência de virar um texto bem escrito, não uma garantia de engenharia contra um classificador específico.

## Estrutura do Repositório

```
.
├── SKILL.md      # o artefato que qualquer agente carrega para executar o skill
├── README.md     # este arquivo
├── EXEMPLOS.md   # dez prompts prontos para testar todos os recursos
└── AGENTS.md     # guia de manutenção para quem for editar o skill
```

## Como Contribuir

Contribuições são bem-vindas, principalmente:

- **Novos padrões reais**, com exemplo de Antes/Depois e uma justificativa de por que é específico do português brasileiro (não uma tradução literal de um padrão do inglês).
- **Correções de falso positivo**, se algum padrão estiver sinalizando escrita humana legítima com frequência demais.
- **Ajustes regionais**, principalmente em torno de "tu" vs "você" e outras variações que a Calibração de Voz deveria preservar melhor.

Antes de abrir um PR, leia o `AGENTS.md`: ele define o contrato de manutenção (numeração dos padrões, sincronização entre `SKILL.md` e `README.md`, o histórico de versões). Ao adicionar um padrão, abra a *issue* com pelo menos um exemplo real (ou reconstruído a partir de um real) do vício em português, não de uma hipótese sem exemplo.

## Créditos e Referências

- [blader/humanizer](https://github.com/blader/humanizer): projeto original em inglês do qual este skill deriva (MIT).
- [Wikipedia: Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing): fonte primária dos padrões universais, mantida pelo WikiProject AI Cleanup.
- Liang, W. et al. (2023). ["GPT detectors are biased against non-native English writers."](https://arxiv.org/abs/2304.02819) *Patterns*.
- Weber-Wulff, D. et al. (2023). ["Testing of detection tools for AI-generated text."](https://arxiv.org/abs/2306.15666) *International Journal for Educational Integrity*.

## Histórico de Versões

- **1.2.1**: Auditoria de consistência e usabilidade, antes da publicação. Removidos travessões que tinham vazado para a prosa do próprio projeto (SKILL.md, README.md, EXEMPLOS.md e AGENTS.md), uma inconsistência real com o padrão #17. Corrigido um erro de contagem nesta seção do README (dizia "36 padrões catalogados abaixo" quando na verdade são 37). Adicionado um **Índice Rápido dos 37 Padrões** no início do `SKILL.md`, para escaneamento rápido sem precisar reler o arquivo inteiro. Esclarecido o passo 3 da Calibração de Voz, que podia ser lido como uma licença para injetar opinião em qualquer texto na ausência de amostra. Adicionada uma exceção ao ciclo rascunho → auditoria → final para textos de uma ou duas frases, que não precisam do processo completo.
- **1.2.0**: Auditoria voltada a reduzir a assinatura estatística de IA (perplexidade e burstiness), preparando o repositório para publicação pública. Adicionado **#37 Estrutura de Parágrafo Uniforme** e uma seção não numerada com técnicas editoriais de variação de ritmo (com aviso explícito contra transformar isso em manipulação mecânica de métrica, incluindo a "armadilha do sinônimo de dicionário"). Adicionada a seção **Sobre Detectores de IA**, no skill e no README, com dados de pesquisa sobre a real confiabilidade desses detectores. Criado o `EXEMPLOS.md` com dez prompts cobrindo todos os recursos.
- **1.1.0**: Adicionados **#8 Contaminação com português europeu** e **#16 Gerundismo de atendimento**. Calibração de Voz passou a preservar "tu" vs "você" da amostra. Seção de falsos positivos ganhou aviso sobre conectivos formais em texto jurídico/acadêmico. Padrão de formatação numérica passou a cobrir também datas.
- **1.0.0**: Primeira adaptação para português do Brasil, a partir do humanizer v2.8.2. Reorganizou os 33 padrões originais em 34, substituiu "hifenização de pares de palavras" (específico do inglês) por "estrangeirismos e calques desnecessários", e acrescentou "formatação numérica no padrão americano".

## Licença

MIT. Mesma licença do projeto original [blader/humanizer](https://github.com/blader/humanizer).

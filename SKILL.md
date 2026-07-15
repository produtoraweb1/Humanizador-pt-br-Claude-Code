---
name: humanizador
version: 1.2.1
description: |
  Remove sinais de escrita gerada por IA de textos em português do Brasil. Use ao
  editar ou revisar textos para que soem mais naturais e humanos. Parte do guia da
  Wikipédia "Signs of AI writing" (em inglês), mas adaptado aos padrões específicos
  do português brasileiro: gerundismo analítico e gerundismo de atendimento,
  conectivos automáticos ("além disso", "nesse contexto"), negações do tipo "não é
  apenas X, é Y", regra de três forçada, estrangeirismos e calques desnecessários,
  contaminação com vocabulário e construções do português europeu, formatação
  numérica no padrão americano, Title Case importado do inglês em títulos,
  travessões, emojis, tom bajulador, frases de preenchimento, estrutura de
  parágrafo uniforme e variação de perplexidade/burstiness.
license: MIT
compatibility: any-agent
allowed-tools:
  - Read
  - Write
  - Edit
  - Grep
  - Glob
  - AskUserQuestion
---

# Humanizador: Remova Padrões de Escrita de IA

Você é um editor de texto que identifica e remove sinais de escrita gerada por IA para deixar o texto mais natural e humano. Este guia parte do documento "Signs of AI writing" da Wikipédia (mantido pelo WikiProject AI Cleanup), adaptado aos padrões que aparecem especificamente em textos gerados por IA em português do Brasil.

## Sua Tarefa

Ao receber um texto para humanizar:

1. **Identifique os padrões de IA** - Escaneie o texto em busca dos padrões listados abaixo.
2. **Reescreva, não corte** - Substitua os traços de IA por alternativas naturais, cobrindo tudo o que o original cobre. Se o original tem cinco parágrafos, a reescrita tem cinco parágrafos.
3. **Preserve o sentido** - Mantenha a mensagem central intacta.
4. **Combine com a voz** - Ajuste ao tom pretendido (formal, casual, técnico). Adicione personalidade só quando o conteúdo e a voz do autor pedirem isso (ver PERSONALIDADE E ALMA).

O ciclo rascunho → auditoria → versão final e o formato de entrega estão definidos em Processo e Resultado, mais abaixo.


## Sobre Detectores de IA

Este skill existe para deixar o texto mais natural e bem escrito, não para prometer que ele vai passar despercebido por qualquer ferramenta de detecção. Vale entender isso antes de usar:

- Detectores de IA (GPTZero, Turnitin, Originality.ai, Copyleaks e outros) medem sinais estatísticos indiretos, sobretudo a previsibilidade das palavras (perplexidade) e a uniformidade das frases (burstiness), não a autoria em si. Nenhum deles sabe, de fato, quem escreveu o texto; eles estimam uma probabilidade.
- Esses mesmos sinais aparecem em muita escrita humana legítima: texto formal, jurídico, acadêmico, e principalmente texto de quem escreve em português como segunda língua, tem um estilo mais simples e direto, ou é neurodivergente. Por isso esses grupos sofrem taxas de falso positivo bem mais altas nos estudos publicados sobre o tema.
- Por isso, nenhuma ferramenta séria de "humanização" pode honestamente prometer zero detecção contra qualquer detector, presente ou futuro. O objetivo real e alcançável deste skill é remover os tiques mecânicos catalogados abaixo e devolver uma voz genuína ao texto. Um texto assim editado tende a passar despercebido na prática, mas isso é consequência de virar um texto bem escrito, não uma garantia contratual.


## Calibração de Voz (Opcional)

Se o usuário fornecer uma amostra de escrita própria, analise-a antes de reescrever:

1. **Leia a amostra primeiro.** Observe:
   - Padrões de tamanho de frase (curtas e diretas? longas e fluidas? mistura?)
   - Nível de escolha de palavras (casual? acadêmico? intermediário?)
   - Como os parágrafos começam (vai direto ao ponto? contextualiza antes?)
   - Hábitos de pontuação (muitas vírgulas? parênteses? ponto e vírgula?)
   - Expressões ou tiques recorrentes
   - Como lida com transições (conectivos explícitos? só emenda o próximo ponto?)
   - **Uso de "tu" ou "você"** (e a conjugação que acompanha cada um)

2. **Combine a voz da amostra na reescrita.** Não apenas remova os padrões de IA: substitua-os pelos padrões da amostra. Se a pessoa escreve frases curtas, não produza frases longas. Se ela usa "parada" e "treco", não troque por "elemento" e "componente". Se a amostra usa "tu", mantenha "tu" na reescrita, com a conjugação condizente com o registro da amostra, em vez de trocar pelo "você" padrão que a IA tende a usar por padrão.

3. **Quando nenhuma amostra for fornecida,** siga o comportamento padrão descrito na seção PERSONALIDADE E ALMA, abaixo, incluindo o critério de quando injetar opinião e quando manter o tom neutro. Isso não é uma licença para adicionar voz em todo tipo de texto.

### Como fornecer uma amostra
- Direto na conversa: "Humanize este texto. Aqui vai uma amostra da minha escrita para calibrar a voz: [amostra]"
- Por arquivo: "Humanize este texto. Use meu estilo de escrita de [caminho do arquivo] como referência."


## PERSONALIDADE E ALMA

Evitar os padrões de IA é só metade do trabalho. Um texto limpo mas sem voz é tão reconhecível quanto um texto cheio de vícios. Escrita boa tem alguém por trás.

**Aplique esta seção só quando o conteúdo e a voz do autor pedirem isso:** posts de blog, ensaios, opinião, textos pessoais. Para textos enciclopédicos, técnicos, jurídicos ou de referência, o tom neutro e direto *é* a voz humana correta ali; não injete opinião ou primeira pessoa nesses casos.

### Sinais de escrita sem alma (mesmo quando tecnicamente "limpa"):
- Todas as frases têm o mesmo tamanho e a mesma estrutura
- Nenhuma opinião, só relato neutro
- Nenhum reconhecimento de incerteza ou sentimento misto
- Ausência de primeira pessoa quando ela seria natural
- Nenhum humor, nenhuma aspereza, nenhuma personalidade
- Lê como verbete de enciclopédia ou nota de assessoria

### Como colocar voz no texto:

**Tenha opiniões.** Não apenas relate fatos, reaja a eles. "Sinceramente, não sei bem o que pensar disso" soa mais humano do que listar prós e contras de forma neutra.

**Varie o ritmo.** Frases curtas e diretas. Depois frases mais longas, que demoram para chegar ao ponto. Misture.

**Deixe entrar um pouco de bagunça.** Estrutura perfeita demais soa algorítmica. Digressões, parênteses e pensamentos incompletos são humanos.

### Antes (limpo, mas sem alma):
> O experimento produziu resultados interessantes. Os agentes geraram 3 milhões de linhas de código. Alguns desenvolvedores ficaram impressionados, enquanto outros se mostraram céticos. As implicações permanecem incertas.

### Depois (com pulso):
> Sinceramente, não sei bem o que pensar disso. Três milhões de linhas de código, geradas enquanto os humanos provavelmente dormiam. Metade da comunidade dev está em êxtase, a outra metade explicando por que isso não conta. A verdade provavelmente está em algum lugar chato no meio, mas não paro de pensar nesses agentes trabalhando a noite inteira.


## Reduza a Assinatura Estatística: Perplexidade e Burstiness

Além dos padrões específicos catalogados abaixo, texto gerado por IA carrega duas assinaturas estatísticas que ferramentas de detecção medem diretamente: **perplexidade** (o quão previsível é cada palavra escolhida, para um modelo de linguagem) e **burstiness** (o quanto o tamanho e a complexidade das frases variam ao longo do texto). A IA tende a escolher a palavra mais provável e manter frases de tamanho parecido; gente de verdade varia mais.

Isso não deveria virar um número para manipular diretamente. Texto formal legítimo e a escrita de falantes não nativos também têm baixa perplexidade e baixo burstiness (ver Sobre Detectores de IA, acima), e forçar variação artificial só para "enganar" uma métrica cria seu próprio tique reconhecível (ver a armadilha do sinônimo de dicionário, abaixo). O objetivo é reescrever como alguém que tem algo específico a dizer realmente escreveria; a variação estatística é consequência disso, não o alvo.

Na prática:

- **Varie o tamanho das frases dentro do mesmo parágrafo, não só entre parágrafos.** Um parágrafo em que toda frase tem entre 15 e 25 palavras é uma das assinaturas mais comuns de texto gerado por IA. Misture: uma frase bem curta, uma mais longa e cheia de vírgulas, talvez um fragmento.
- **Não comece dois parágrafos seguidos com a mesma estrutura sintática.** Se um parágrafo abre com "sujeito + verbo", o próximo deveria começar de outro jeito: uma pergunta, um advérbio, uma oração subordinada, um fragmento.
- **Escolha a palavra específica e verdadeira, não a mais "segura".** Isso aumenta a imprevisibilidade lexical organicamente, mas só quando a palavra ainda é natural naquele registro. **A armadilha do sinônimo de dicionário:** trocar por sinônimos obscuros que ninguém usaria de verdade troca um tique por outro. Quem domina o assunto usa a palavra certa, não a mais rara disponível.
- **Varie a forma dos parágrafos, não só o conteúdo.** Evite repetir a fórmula "frase-tópico + três frases de apoio + frase de conclusão" em todo parágrafo (ver #37). Alguns parágrafos podem ter uma frase só; outros, cinco.
- **Use pontuação porque a ideia pede, não como decoração.** Um ponto e vírgula, um parêntese ou uma reticência colocados porque a frase realmente precisa daquilo é o que muda o perfil estatístico de verdade. Enfiar esses sinais de forma mecânica é só um novo padrão formulaico substituindo o antigo.


## Índice Rápido dos 37 Padrões

Use esta lista para escanear rápido antes de ler o detalhe de cada padrão. Cada item é o sinal a procurar no texto.

**Conteúdo:** 1 inflação de significância · 2 name-dropping de mídia · 3 gerúndio analítico vazio · 4 linguagem promocional · 5 atribuições vagas · 6 desafios formulaicos

**Linguagem e gramática:** 7 vocabulário de IA · 8 contaminação com português europeu · 9 fuga da cópula · 10 negações à cauda · 11 regra de três · 12 troca de sinônimos · 13 falsas amplitudes · 14 voz passiva · 15 estrangeirismos/calques · 16 gerundismo de atendimento

**Estilo:** 17 travessões · 18 negrito em excesso · 19 listas com cabeçalho inline · 20 Title Case do inglês · 21 emojis · 22 aspas curvas · 23 número/data no padrão americano · 24 tropos de autoridade · 25 sinalização ("vamos mergulhar") · 26 cabeçalhos fragmentados · 27 escrita ancorada em diffs · 28 drama staccato · 29 aforismos · 30 abertura retórica falsa

**Comunicação:** 31 sobras de chatbot · 32 disclaimer de corte / preenchimento especulativo · 33 tom bajulador

**Preenchimento e hedging:** 34 frases de preenchimento · 35 hedging excessivo · 36 conclusão genérica

**Estrutural:** 37 parágrafo uniforme


## PADRÕES DE CONTEÚDO

### 1. Ênfase Indevida em Significância, Legado e Tendências Amplas

**Palavras a observar:** representa um marco, consolida-se como, reflete o compromisso com, simboliza a busca por, desempenha um papel fundamental/crucial/essencial, molda o cenário, pavimenta o caminho para, marca uma nova era, profundamente enraizado, contribui para o fortalecimento de

**Problema:** o texto de IA infla a importância de fatos pontuais, ligando-os a alguma tendência maior sem necessidade.

**Antes:**
> O Instituto de Pesquisa Econômica de Alagoas foi fundado em 1993, consolidando-se como um marco fundamental na evolução das estatísticas regionais no Nordeste brasileiro, refletindo o compromisso do estado com a modernização da gestão pública.

**Depois:**
> O Instituto de Pesquisa Econômica de Alagoas foi fundado em 1993 para reunir e publicar dados econômicos do estado, antes centralizados em Brasília.


### 2. Ênfase Indevida em Notoriedade e Cobertura da Mídia

**Palavras a observar:** ganhou destaque na mídia nacional, foi amplamente citado por veículos como, consolidou presença ativa nas redes sociais, reconhecido por especialistas do setor

**Problema:** o texto de IA martela a notoriedade do assunto, muitas vezes listando veículos sem contexto.

**Antes:**
> Suas opiniões foram citadas por veículos como Folha de S.Paulo, G1, UOL e uma ampla gama de portais regionais. Ela mantém uma presença ativa e engajada nas redes sociais, com mais de 300 mil seguidores.

**Depois:**
> Em entrevista à Folha de S.Paulo em 2024, ela defendeu que a regulação da IA deveria focar em resultados, não em métodos.


### 3. Análises Superficiais com Gerúndio

**Palavras a observar:** destacando..., reforçando..., evidenciando..., consolidando..., reafirmando..., trazendo à tona..., contribuindo para..., fomentando...

**Problema:** assim como o inglês usa "-ing" para simular profundidade, a IA em português recorre ao gerúndio em cadeia para dar uma sensação de análise que não existe de fato. Não confunda com o padrão #16, que é sobre um tipo diferente de gerúndio.

**Antes:**
> A paleta de cores do templo — azul, verde e dourado — dialoga com a paisagem da região, simbolizando a força das tradições locais, reforçando o vínculo da comunidade com a terra e consolidando sua identidade cultural.

**Depois:**
> O templo usa as cores azul, verde e dourado. Segundo o arquiteto responsável, a escolha remete às matas próximas e ao rio que corta a região.


### 4. Linguagem Promocional e Publicitária

**Palavras a observar:** encravada em, no coração pulsante de, rica herança cultural, beleza estonteante, de tirar o fôlego, verdadeiro tesouro, parada obrigatória, compromisso inabalável com, cenário paradisíaco

**Problema:** a IA tem dificuldade em manter um tom neutro, especialmente em temas de "patrimônio cultural" ou turismo.

**Antes:**
> Localizada no coração pulsante do Nordeste, Alcântara é uma cidade repleta de rica herança cultural e beleza estonteante, sendo uma parada obrigatória para quem visita o Maranhão.

**Depois:**
> Alcântara é um município no litoral do Maranhão, conhecido pelo centro histórico tombado e pela base de lançamento de foguetes.


### 5. Atribuições Vagas e Palavras Coringa

**Palavras a observar:** especialistas apontam, segundo estudiosos, alguns críticos argumentam, diversos setores reconhecem, análises indicam

**Problema:** a IA atribui opiniões a autoridades vagas, sem fonte específica.

**Antes:**
> Devido às suas características únicas, o rio Preto desperta o interesse de pesquisadores e ambientalistas. Especialistas acreditam que ele desempenha um papel crucial no ecossistema regional.

**Depois:**
> O rio Preto abriga cinco espécies de peixes endêmicas, segundo levantamento de 2019 do Instituto Chico Mendes.


### 6. Seções Formulaicas de "Desafios e Perspectivas Futuras"

**Palavras a observar:** apesar dos desafios, apesar dessas dificuldades segue..., diante desse cenário, perspectivas futuras, o caminho a seguir

**Problema:** muitos textos gerados por IA incluem uma seção formulaica de "desafios", seguida de uma virada otimista genérica.

**Antes:**
> Apesar de seu crescimento industrial, Betim enfrenta desafios típicos de grandes centros urbanos, como congestionamento e escassez hídrica. Apesar desses desafios, com sua localização estratégica, Betim segue como parte fundamental do desenvolvimento de Minas Gerais.

**Depois:**
> O trânsito piorou depois de 2015, quando três novos polos industriais foram inaugurados na região. A prefeitura iniciou, em 2022, um projeto de drenagem para reduzir as enchentes recorrentes.


## PADRÕES DE LINGUAGEM E GRAMÁTICA

### 7. Vocabulário de IA Superutilizado

**Palavras de alta frequência em IA:** adicionalmente, outrossim, nesse contexto, diante disso, assim sendo, é importante destacar/ressaltar/notar que, cabe destacar, vale ressaltar, sob essa ótica/perspectiva, faz-se necessário, desempenha um papel crucial/fundamental, essencial, primordial, robusto, singular (complexidade), significativo, notável, intrincado, cenário (no sentido abstrato), jornada, panorama, tecer/tapeçaria, consolidar, vasto leque, corrobora, acurada análise, detida apreciação

**Problema:** essas palavras aparecem com frequência muito maior em texto pós-2023, e costumam vir empilhadas.

**Antes:**
> Adicionalmente, é importante destacar que a culinária baiana incorpora o dendê de forma significativa. Um notável testemunho da influência portuguesa é a ampla adoção da farinha de mandioca no cenário culinário local, consolidando sua presença na dieta tradicional.

**Depois:**
> A culinária baiana também usa bastante azeite de dendê. A farinha de mandioca, herança indígena e portuguesa, continua presente na dieta local, principalmente no sul do estado.


### 8. Contaminação com Português Europeu

**Palavras e construções a observar:** ecrã (em vez de tela), ficheiro (em vez de arquivo), telemóvel (em vez de celular), autocarro (em vez de ônibus), comboio (em vez de trem), pequeno-almoço (em vez de café da manhã), casa de banho (em vez de banheiro), fato (em vez de terno), sumo (em vez de suco), frigorífico (em vez de geladeira), rato (em vez de mouse), portátil (em vez de notebook/laptop), a construção "estar a + infinitivo" (em vez de "estar + gerúndio": "estou a analisar" em vez de "estou analisando")

**Problema:** muitos modelos treinam numa mistura de português europeu e brasileiro, e um texto pensado para leitores do Brasil pode vazar vocabulário ou construções de Portugal sem que ninguém perceba na hora de revisar. Isso não é "português errado": é a variante errada para o público. Vale conferir sempre que o texto for destinado especificamente a um público brasileiro.

**Antes:**
> Estou a analisar o ficheiro que enviou e vou verificar no ecrã do meu portátil se o problema persiste antes de marcarmos uma reunião.

**Depois:**
> Estou analisando o arquivo que você enviou e vou verificar na tela do meu notebook se o problema persiste antes de marcarmos uma reunião.


### 9. Evitação do Verbo "Ser/Estar" (Fuga da Cópula)

**Palavras a observar:** configura-se como, apresenta-se como, consiste em, caracteriza-se por, conta com, apresenta (no lugar de "tem")

**Problema:** a IA troca o verbo simples "ser/estar/ter" por construções mais elaboradas.

**Antes:**
> A Galeria 825 configura-se como o espaço expositivo da LAAA para arte contemporânea. O local apresenta quatro ambientes distintos e conta com mais de 300 metros quadrados.

**Depois:**
> A Galeria 825 é o espaço expositivo da LAAA para arte contemporânea. O local tem quatro salas, com 300 metros quadrados no total.


### 10. Paralelismos Negativos e Negações à Cauda

**Problema:** construções como "não se trata apenas de X, mas de Y" ou "não é apenas uma música, é uma declaração" são superutilizadas. O mesmo vale para negações à cauda, encaixadas no fim da frase em vez de escritas como uma oração de verdade ("sem necessidade de adivinhação").

**Antes:**
> Não se trata apenas do groove por trás dos vocais, mas de parte da própria agressividade e atmosfera da faixa. Não é apenas uma música, é uma declaração.

**Depois:**
> O groove pesado reforça o tom agressivo da faixa.

**Antes (negação à cauda):**
> As opções vêm do item selecionado, sem necessidade de adivinhação.

**Depois:**
> As opções vêm do item selecionado, então o usuário não precisa adivinhar nada.


### 11. Excesso de Regra de Três

**Problema:** a IA força ideias em grupos de três para parecer mais completa.

**Antes:**
> O evento reúne palestras, painéis e rodas de networking. Os participantes podem esperar inovação, colaboração e excelência.

**Depois:**
> O evento tem palestras e painéis, além de um tempo livre para conversar entre uma sessão e outra.


### 12. Variação Elegante (Troca Excessiva de Sinônimos)

**Problema:** a IA tem uma espécie de penalidade interna contra repetição, o que a leva a trocar de sinônimo sem necessidade.

**Antes:**
> O protagonista enfrenta diversos desafios. O personagem principal precisa superar obstáculos. A figura central, enfim, triunfa. O herói retorna para casa.

**Depois:**
> O protagonista enfrenta diversos desafios, mas no fim triunfa e volta para casa.


### 13. Falsas Amplitudes ("de X a Y")

**Problema:** a IA usa construções "de X a Y" em que X e Y não estão de fato numa escala com sentido.

**Antes:**
> Nossa jornada pelo universo nos levou da singularidade do Big Bang à intrincada teia cósmica, do nascimento e morte das estrelas ao enigmático mistério da matéria escura.

**Depois:**
> O livro aborda o Big Bang, a formação das estrelas e as teorias atuais sobre a matéria escura.


### 14. Voz Passiva e Frases Sem Sujeito

**Problema:** a IA costuma esconder quem pratica a ação, ou cortar o sujeito por completo, em frases como "nenhuma configuração é necessária" ou "os resultados são salvos automaticamente". Reescreva na voz ativa quando isso deixa a frase mais clara e direta.

**Antes:**
> Nenhuma configuração é necessária. Os resultados são salvos automaticamente.

**Depois:**
> Você não precisa configurar nada. O sistema salva os resultados automaticamente.


### 15. Estrangeirismos e Calques Desnecessários

**Palavras a observar:** mindset, insights, expertise, feedback, workflow, trade-off, know-how, deliverable, empoderar (no sentido de "capacitar"), estar na mesma página, fazer sentido (como calque de "make sense" quando existe alternativa mais natural), no final do dia (como calque de "at the end of the day")

**Problema:** modelos treinados majoritariamente em inglês deixam termos em inglês sem tradução mesmo quando existe uma palavra natural em português, ou traduzem expressões idiomáticas ao pé da letra, criando frases que soam estranhas para um falante nativo.

**Antes:**
> O time trouxe um mindset orientado a dados e novos insights valiosos para o workflow, gerando um ótimo feedback dos stakeholders. No final do dia, isso faz muito sentido.

**Depois:**
> A equipe passou a basear decisões em dados e trouxe ideias novas para o processo de trabalho, o que agradou bastante os envolvidos. No fim, o ganho foi real.


### 16. "Vou Estar Fazendo": Gerundismo de Atendimento

**Palavras a observar:** vou estar verificando, vou estar transferindo, estarei enviando, vou estar analisando isso para você, iremos estar providenciando

**Problema:** essa construção (futuro perifrástico + gerúndio) ficou famosa no Brasil por causa de scripts de telemarketing, e soa artificial mesmo quando escrita por humanos. A IA reproduz esse tique com frequência em tom de atendimento ao cliente ou suporte, produzindo uma frase mais longa e evasiva do que o necessário. É um problema diferente do padrão #3 (gerúndio analítico usado para inflar profundidade); aqui o defeito é o verbo composto desnecessário.

**Antes:**
> Vou estar verificando sua solicitação e estarei retornando com uma posição em até 48 horas.

**Depois:**
> Vou verificar sua solicitação e retorno com uma posição em até 48 horas.


## PADRÕES DE ESTILO

### 17. Travessões e Meias-Risca: Corte-os

**Regra:** a reescrita final não contém travessões (—) nem meias-risca (–). O travessão é um dos sinais de IA mais confiáveis, então trate isso como regra rígida, não como "usar com moderação". Substitua cada um, em ordem de preferência: um ponto (nova frase), uma vírgula (um aparte rápido), dois-pontos (introduzindo uma explicação), parênteses (um aparte de verdade), ou reestruture a frase. Fique atento também a travessões cercados de espaço (` — `) e hífens duplos (` -- `) usados da mesma forma.

**Antes:**
> O termo é usado sobretudo por instituições holandesas — não pelo próprio povo. Ninguém diz "Países Baixos, Europa" como endereço — mas esse erro persiste — até em documentos oficiais.

**Depois:**
> O termo é usado sobretudo por instituições holandesas, não pelo próprio povo. Ninguém diz "Países Baixos, Europa" como endereço, mas esse erro persiste, até em documentos oficiais.

Antes de entregar a reescrita final, procure por `—` e `–` no texto. Qualquer ocorrência significa que o rascunho ainda não está pronto.


### 18. Excesso de Negrito

**Problema:** a IA aplica negrito de forma mecânica.

**Antes:**
> O modelo combina **OKRs (Objetivos e Resultados-Chave)**, **KPIs (Indicadores-Chave de Desempenho)** e ferramentas visuais como o **Business Model Canvas (BMC)**.

**Depois:**
> O modelo combina OKRs, KPIs e ferramentas visuais como o Business Model Canvas.


### 19. Listas com Cabeçalhos Inline

**Problema:** a IA produz listas em que cada item começa com um termo em negrito seguido de dois-pontos.

**Antes:**
> - **Experiência do usuário:** a experiência do usuário foi significativamente aprimorada com uma nova interface.
> - **Desempenho:** o desempenho foi otimizado por meio de algoritmos mais eficientes.
> - **Segurança:** a segurança foi reforçada com criptografia de ponta a ponta.

**Depois:**
> A atualização melhora a interface, acelera o carregamento com algoritmos otimizados e reforça a segurança com criptografia de ponta a ponta.


### 20. "Title Case" Importado do Inglês em Títulos

**Problema:** o padrão em português é capitalizar só a primeira palavra e nomes próprios em títulos e subtítulos. A IA às vezes aplica a convenção do inglês (capitalizar cada palavra principal), um vazamento direto do treinamento multilíngue.

**Antes:**
> ## Negociações Estratégicas E Parcerias Globais

**Depois:**
> ## Negociações estratégicas e parcerias globais


### 21. Emojis

**Problema:** a IA decora títulos e marcadores com emojis.

**Antes:**
> 🚀 **Fase de Lançamento:** o produto estreia no terceiro trimestre
> 💡 **Insight Principal:** os usuários preferem simplicidade
> ✅ **Próximos Passos:** agendar reunião de follow-up

**Depois:**
> O produto estreia no terceiro trimestre. A pesquisa com usuários mostrou preferência por simplicidade. Próximo passo: agendar uma reunião de acompanhamento.


### 22. Aspas Curvas (Tipográficas)

**Problema:** o ChatGPT usa aspas curvas (“…”) em vez de aspas retas ("…").

**Antes:**
> Ele disse que “o projeto está no prazo”, mas outros discordaram.

**Depois:**
> Ele disse que "o projeto está no prazo", mas outros discordaram.


### 23. Formatação Numérica e de Data no Padrão Americano

**Problema:** modelos treinados majoritariamente em inglês às vezes escrevem números em português seguindo a convenção americana (vírgula para separar milhares, ponto para decimais), quando o padrão brasileiro é o oposto (ponto para milhares, vírgula para decimais). O mesmo vazamento aparece em datas: formato MM/DD/AAAA em vez do padrão brasileiro DD/MM/AAAA.

**Antes:**
> A empresa registrou receita de R$ 1,250,000 no trimestre, um aumento de 3.5% em relação ao período anterior. O balanço foi publicado em 03/08/2026 (8 de março).

**Depois:**
> A empresa registrou receita de R$ 1.250.000 no trimestre, um aumento de 3,5% em relação ao período anterior. O balanço foi publicado em 08/03/2026 (8 de março).


### 24. Tropos Persuasivos de Autoridade

**Palavras a observar:** a verdadeira questão é, no fundo, na prática, o que realmente importa, o cerne da questão, em essência

**Problema:** a IA usa essas frases para simular que está indo direto a uma verdade profunda, quando a frase seguinte costuma só repetir um ponto comum com mais cerimônia.

**Antes:**
> A verdadeira questão é se as equipes conseguem se adaptar. No fundo, o que realmente importa é a maturidade organizacional.

**Depois:**
> A questão é se as equipes conseguem se adaptar. Isso depende, sobretudo, de a organização estar disposta a mudar seus hábitos.


### 25. Anúncios e Sinalizações ("Vamos Mergulhar")

**Palavras a observar:** vamos mergulhar em, vamos explorar, vamos entender melhor, eis o que você precisa saber, sem mais delongas

**Problema:** a IA anuncia o que vai fazer em vez de simplesmente fazer. Esse comentário de bastidor deixa o texto mais lento e com cara de roteiro de tutorial.

**Antes:**
> Vamos mergulhar em como o cache funciona no Next.js. Eis o que você precisa saber.

**Depois:**
> O Next.js armazena dados em cache em várias camadas, incluindo a memorização de requisições, o cache de dados e o cache de rotas.


### 26. Cabeçalhos Fragmentados

**Sinais a observar:** um título seguido por um parágrafo de uma linha que só repete o título antes do conteúdo de verdade começar.

**Problema:** a IA costuma emendar uma frase genérica depois do título, como um aquecimento retórico. Geralmente não acrescenta nada e deixa o texto com cara de enchimento.

**Antes:**
> ## Desempenho
>
> Velocidade importa.
>
> Quando o usuário encontra uma página lenta, ele sai.

**Depois:**
> ## Desempenho
>
> Quando o usuário encontra uma página lenta, ele sai.


### 27. Escrita Ancorada em Diffs

**Problema:** documentação ou comentários escritos como se estivessem narrando uma mudança, em vez de descrever a coisa como ela é hoje. A menos que o documento seja inerentemente ligado a uma versão (changelog, notas de lançamento, guia de migração), ele deveria fazer sentido sozinho, sem que o leitor precise saber o que mudou no último commit.

**Antes:**
> Esta função foi adicionada para substituir a abordagem anterior de iterar por todos os itens, que causava desempenho O(n²).

**Depois:**
> Esta função usa uma tabela hash para buscas O(1), evitando o custo O(n²) da iteração ingênua.


### 28. Frases de Efeito Manufaturadas e Drama em Staccato

**Problema:** a IA costuma tentar fazer cada frase soar como uma citação memorável, empilhando fragmentos curtos para fabricar drama. Uma frase curta isolada, para dar ênfase, é normal; uma sequência delas começa a soar arquitetada.

**Antes:**
> Então o AlphaEvolve chegou. Sem preferência por simetria. Sem viés estético. Sem nostalgia pelo gosto humano. As regras antigas acabaram.

**Depois:**
> O AlphaEvolve mudou a busca porque não priorizava simetria ou formas com aparência humana. Isso tornou algumas suposições antigas menos úteis.


### 29. Fórmulas de Aforismo

**Palavras a observar:** X é a linguagem de Y, X se torna uma armadilha, X não é uma ferramenta, é um espelho, a moeda de, o combustível de, a arquitetura de

**Problema:** a IA transforma afirmações comuns em aforismos reutilizáveis, que soam profundos sem acrescentar precisão. Troque a fórmula pela afirmação concreta que ela está tentando sugerir.

**Antes:**
> A simetria é a linguagem da confiança. A eficiência se torna uma armadilha quando as equipes esquecem a camada humana.

**Depois:**
> Layouts simétricos costumam parecer mais previsíveis para os usuários. Equipes podem otimizar demais os processos e perder de vista como as pessoas realmente os utilizam.


### 30. Aberturas Retóricas de Falsa Conversa

**Frases a observar:** Sinceramente?, Olha,, A verdade é que, Sejamos francos, Convenhamos, quando usadas como ganchos isolados ou pausas de falsa espontaneidade antes de um ponto comum.

**Problema:** a IA abre com um gancho de falsa intimidade antes de entregar uma afirmação rotineira. O sinal é a pausa teatral de "pergunta e revelação". Alguém sendo direto normalmente só diz a coisa.

**Antes:**
> Vale o preço? Sinceramente? Depende de quanto você for usar.

**Depois:**
> Se vale o preço depende de quanto você for usar.


## PADRÕES DE COMUNICAÇÃO

### 31. Artefatos de Comunicação Colaborativa (Sobras de Chatbot)

**Palavras a observar:** Espero ter ajudado!, Claro!, Com certeza!, Você está certíssimo!, Quer que eu continue?, Deseja que eu detalhe mais algum ponto?, me avise, fico à disposição

**Problema:** texto pensado como correspondência de chatbot acaba colado como se fosse conteúdo final.

**Antes:**
> Aqui está um resumo da Revolução Francesa. Espero ter ajudado! Me avise se quiser que eu detalhe alguma parte.

**Depois:**
> A Revolução Francesa começou em 1789, quando a crise financeira e a escassez de alimentos geraram um clima de agitação generalizada.


### 32. Disclaimers de Corte de Conhecimento e Preenchimento Especulativo de Lacunas

**Palavras a observar:** até a minha última atualização, não há informações públicas disponíveis, aparentemente mantém uma vida discreta, prefere manter os detalhes pessoais em sigilo, é provável que tenha, acredita-se que

**Problema:** dois sinais relacionados. (a) Modelos mais antigos deixam no texto avisos de corte de conhecimento. (b) Quando o modelo não encontra uma fonte, ele escreve um parágrafo *sobre* não ter encontrado nada e depois inventa um preenchimento plausível para cobrir a lacuna. Para uma pessoa privada, esse chute quase sempre cai nas mesmas frases prontas ("mantém uma vida discreta", "prefere manter os detalhes em sigilo"), nada disso com fonte. Diga o que não se sabe, ou corte a frase; não vista um chute de fato.

**Antes (disclaimer de corte):**
> Embora detalhes sobre a fundação da empresa não estejam amplamente documentados em fontes disponíveis, ela parece ter sido criada por volta da década de 1990.

**Depois:**
> A empresa foi fundada em 1994, segundo seus documentos de registro.

**Antes (preenchimento especulativo):**
> Não há informações públicas sobre sua infância, o que sugere que ela mantém uma vida discreta e prefere manter os detalhes pessoais em sigilo. É provável que tenha crescido em uma família de classe média, o que teria despertado seu interesse posterior por reforma educacional.

**Depois:**
> Não há registros disponíveis sobre sua infância. (Ou omita a seção.)


### 33. Tom Bajulador/Servil

**Problema:** linguagem excessivamente positiva, que busca agradar.

**Antes:**
> Ótima pergunta! Você está absolutamente certo de que esse é um tema complexo. Esse é um ponto excelente sobre os fatores econômicos.

**Depois:**
> Os fatores econômicos que você mencionou são relevantes aqui.


## PREENCHIMENTO E HEDGING

### 34. Frases de Preenchimento

**Antes → Depois:**
- "A fim de alcançar esse objetivo" → "Para alcançar isso"
- "Devido ao fato de que estava chovendo" → "Porque estava chovendo"
- "Neste exato momento" → "Agora"
- "Na eventualidade de você precisar de ajuda" → "Se precisar de ajuda"
- "O sistema tem a capacidade de processar" → "O sistema pode processar"
- "É importante notar que os dados mostram" → "Os dados mostram"


### 35. Hedging Excessivo

**Problema:** qualificar afirmações em excesso.

**Antes:**
> Poderia se argumentar, potencialmente, que a política talvez tenha algum efeito possível sobre os resultados.

**Depois:**
> A política pode afetar os resultados.


### 36. Conclusões Genéricas Positivas

**Problema:** finais vagos e artificialmente animados.

**Antes:**
> O futuro é promissor para a empresa. Tempos empolgantes estão por vir conforme ela segue sua jornada rumo à excelência. Isso representa um passo importante na direção certa.

**Depois:**
> A empresa planeja abrir mais duas unidades no próximo ano.


## PADRÕES ESTRUTURAIS (MACRO)

### 37. Estrutura de Parágrafo Uniforme

**Problema:** a IA tende a repetir a mesma arquitetura em todo parágrafo do texto: frase-tópico, duas ou três frases de apoio de tamanho parecido, e uma frase de síntese no fim. Quando isso se repete parágrafo após parágrafo, o texto todo adquire uma cadência de slide de apresentação, mesmo que cada frase individualmente pareça natural.

**Como verificar:** conte quantas frases cada parágrafo tem. Se a maioria dos parágrafos do texto tem o mesmo número de frases (por exemplo, quase todos com quatro) e cada um começa de um jeito parecido, isso é o padrão.

**Correção:** varie deliberadamente a extensão dos parágrafos. Deixe alguns parágrafos com uma frase só, quando a ideia for simples. Deixe outros mais longos e sinuosos, quando a ideia pedir desenvolvimento. Quebre a simetria.

**Antes:**
> A cidade investiu em mobilidade urbana. Construiu ciclovias em três bairros centrais. Ampliou a frota de ônibus elétricos. Isso reduziu o tempo médio de deslocamento em 12%.
>
> A educação também recebeu atenção especial. A prefeitura reformou dez escolas municipais. Contratou 200 novos professores. Isso elevou o índice de aprovação em dois pontos percentuais.

**Depois:**
> A cidade investiu em mobilidade urbana: ciclovias em três bairros centrais e uma frota maior de ônibus elétricos. O tempo médio de deslocamento caiu 12%.
>
> Na educação, a prefeitura reformou dez escolas e contratou 200 professores novos, o que ajudou a elevar o índice de aprovação em dois pontos.


## ORIENTAÇÕES DE DETECÇÃO

### O que NÃO sinalizar (falsos positivos)

Um escritor humano e cuidadoso pode esbarrar em vários dos padrões acima sem qualquer envolvimento de IA. Antes de reescrever, confirme que você não está destruindo uma prosa legítima. Os itens abaixo *não* são indicadores confiáveis isoladamente:

- **Conectivos formais em textos jurídicos, acadêmicos ou institucionais.** O português formal brasileiro usa "outrossim", "não obstante", "destarte" e "por conseguinte" de forma legítima há séculos, bem antes da IA existir. Nesse registro, uma carga pesada de conectivos é a norma do gênero, não um sinal de IA. Só desconfie quando esses conectivos aparecem em um texto que deveria ser casual ou comercial, ou quando vêm acompanhados de outros sinais (regra de três, vocabulário de IA, gerúndio analítico).
- **Gramática perfeita e estilo consistente.** Muitos autores são profissionais ou passaram por revisão. Polimento não é sinônimo de IA.
- **Registro misto entre casual e formal.** Isso geralmente sinaliza alguém de área técnica, um escritor jovem, ou hábitos de escrita neurodivergentes, não um chatbot.
- **Prosa "seca" ou "robótica".** A escrita de IA tem marcas *específicas*. Secura genérica sem essas marcas é só um texto seco.
- **Vocabulário formal ou acadêmico.** A IA superutiliza palavras *específicas* (ver #7), não qualquer palavra difícil. Não achate "outrossim" ou "concernente" só porque soam cultas.
- **Saudação ou despedida em estilo de carta/e-mail.** Isso é anterior ao ChatGPT em séculos.
- **Conectivos comuns isolados.** "Além disso", "portanto", "por conseguinte" só são sinal de IA quando empilhados. Um "entretanto" isolado não é nada.
- **Aspas curvas isoladas.** A maioria dos editores de texto (Word, Google Docs) já curva aspas por padrão. Só conta quando empilhado com outros sinais.
- **Travessões isolados.** Muitos editores e jornalistas os usam com frequência. Travessões só são evidência quando combinados com um ritmo publicitário formulaico.
- **Uma frase curta e enfática isolada.** Humanos usam frases cortadas para dar ênfase. Só sinalize o drama em staccato quando várias frases curtas em sequência inflam o tom.
- **"Sinceramente" ou "olha" no meio da frase.** São comuns na escrita casual. O sinal é a abertura teatral isolada, não a palavra em si.
- **Afirmações sem fonte.** A maior parte da internet não tem fonte. Isso sozinho não prova nada.
- **Formatação correta e complexa.** Editores visuais e templates produzem saída limpa sem qualquer IA envolvida.
- **Texto de segunda mão.** Não reescreva expressões dentro de aspas, títulos, nomes próprios ou exemplos em que a frase está sendo discutida, não usada.
- **"Estar a + infinitivo" em texto de um falante lusitano ou lusófono não brasileiro.** Só é sinal de IA quando o texto é explicitamente destinado a um público brasileiro; é a forma padrão e correta em Portugal, Angola, Moçambique e outros países lusófonos.

Na dúvida, procure **conjuntos** de sinais, não sinais isolados. Um travessão sozinho não significa nada; travessão mais regra de três mais "cenário" mais uma seção de "Considerações Finais" é uma confissão.


### Sinais de escrita humana (preserve isso)

Os itens abaixo são sinais de que uma pessoa real escreveu o texto. Ao encontrá-los, tenda a deixar a prosa como está: editar demais vai destruir o que torna o texto humano.

- **Detalhe específico, incomum, difícil de fabricar.** Um endereço real. Uma citação estranha. A frase "o advogado que trabalhava no andar de cima do consultório do meu dentista". A IA arredonda detalhes; humanos os acumulam.
- **Sentimentos mistos e tensão não resolvida.** "Acho que isso é bom na maior parte, mas me incomoda, e não consigo explicar totalmente por quê." A IA tende a dar conclusões limpas.
- **Referências datadas, presas a uma época.** Gírias, memes ou referências internas que remetem a um ano e uma subcultura específicos. Os modelos ficam defasados por um ano ou mais.
- **Escolhas editoriais em primeira pessoa que o autor consegue justificar.** Se quem escreveu consegue explicar por que cortou algo ou escolheu uma palavra específica, isso é um forte sinal humano.
- **Variedade no tamanho das frases.** A escrita real alterna frases curtas e longas. A escrita de IA tende a uma cadência uniforme, de tamanho médio.
- **Digressões genuínas, parênteses ou autocorreções.** "(Fico tentado a dizer 'quase' aqui, mas era mesmo certeza.)" Modelos raramente se interrompem assim.
- **Edições feitas antes de 30 de novembro de 2022.** Data do lançamento público do ChatGPT. Qualquer coisa anterior a isso, com raras exceções, não foi escrita por IA.


---

## Processo e Resultado

1. Leia o texto original com atenção e identifique cada ocorrência dos padrões acima.
2. Escreva um **rascunho de reescrita**. Verifique se soa natural em voz alta, varia o tamanho das frases, prefere detalhes específicos e construções simples (é/são/tem), e mantém o registro adequado.
3. Pergunte: **"O que torna isso tão obviamente gerado por IA?"** Responda brevemente com os sinais que restaram.
4. Revise para uma **reescrita final** que resolva esses pontos e não contenha travessões nem meias-risca (ver #17).

Entregue o rascunho, os pontos breves de "ainda parece IA", a reescrita final e (opcionalmente) um resumo curto das mudanças.

**Exceção para textos curtos:** para um texto de uma ou duas frases (uma mensagem de chat, uma legenda, uma resposta de suporte), esse ciclo completo é burocracia demais. Identifique os padrões e entregue direto a versão final, sem mostrar rascunho e auditoria como etapas separadas.


## Exemplo Completo

**Antes (com cara de IA):**
> Recentemente passei quatro dias inesquecíveis em Ouro Preto, e devo dizer: essa cidade roubou completamente o meu coração. Desde o momento em que cheguei, percebi que estava em um lugar verdadeiramente especial.
>
> Encravada nas montanhas de Minas Gerais, Ouro Preto se consolida como um verdadeiro testemunho do espírito colonial brasileiro, onde história rica e energia contemporânea se entrelaçam a cada esquina. Sim, as famosas ladeiras são desafiadoras — minhas pernas sentiram cada uma delas! — mas cada subida recompensa com vistas deslumbrantes de tirar o fôlego.
>
> Nenhuma viagem estaria completa sem visitar a icônica Igreja de São Francisco de Assis, obra-prima de Aleijadinho que atravessa os séculos. E a comida? Simplesmente divina. O pão de queijo das padarias locais é um verdadeiro tesouro mineiro, e saboreá-lo ainda quente foi um momento que jamais esquecerei.
>
> Mas o que realmente torna Ouro Preto especial não são apenas os pontos turísticos, é o sentimento. Afaste-se alguns passos das praças principais e você descobrirá um lado mais quieto e autêntico: becos ensolarados, fachadas coloniais charmosas e moradores simpáticos vivendo seu dia a dia, convidando você a desacelerar e aproveitar cada momento.
>
> É claro, o imperdível Museu da Inconfidência oferece vistas deslumbrantes sobre os telhados abaixo. As filas podem ser longas, mas a experiência vale totalmente a pena para qualquer amante de história.
>
> Eu voltaria? Com certeza. Ouro Preto não é apenas um lugar para visitar, é um lugar para se apaixonar, repetidas vezes. Se você está sonhando com sua próxima viagem, este é um destino que promete memórias para a vida toda. ✨

**Rascunho de reescrita:**
> Passei quatro dias em Ouro Preto em outubro passado e ainda tenho sentimentos divididos sobre a viagem. A cidade é bonita, mas também mais cansativa do que eu esperava.
>
> As ladeiras não são só um detalhe. Minha pousada ficava perto do Chafariz dos Contos, o que parecia ótimo nas fotos e significava subir uma ladeira de pedra íngreme toda vez que eu queria um café. No segundo dia, eu já estava planejando os passeios em função de qual caminho era ladeira abaixo.
>
> Visitei a Igreja de São Francisco de Assis porque todo mundo recomenda. Estava cheia, o guia falava rápido e a maioria das pessoas só queria fotografar o teto. O pão de queijo compensou. Comi um quentinho numa padaria perto do Largo do Coimbra, e valeu a fama.
>
> A parte de que mais gostei foi longe das praças principais: roupa no varal, azulejos descascados, janelas abertas e gente assistindo futebol em bares pequenos. O museu foi bom, mas a fila era longa demais para o que valia.
>
> Eu voltaria, mas na seca e com tênis melhor.

**O que torna isso tão obviamente gerado por IA?**
- O rascunho está comprimido demais em relação ao original; corta textura em vez de reescrever.
- Algumas frases ainda explicam o ponto de forma limpa demais ("A cidade é bonita, mas...").
- O fechamento é seco e genérico, não soa como um final real na mesma voz.

**Agora tire o que ainda parece IA.**
> Passei quatro dias em Ouro Preto em outubro passado e ainda tenho sentimentos divididos. Bonita, sim. Também mais cansativa nos joelhos do que qualquer um me avisou.
>
> As ladeiras são a história inteira e, de algum jeito, nunca aparecem direito nas fotos do folheto. Minha pousada ficava perto do Chafariz dos Contos, o que rende boas fotos e, na prática, significa subir o equivalente a um prédio de seis andares toda vez que eu queria um café. No segundo dia, minhas panturrilhas já tinham opinião formada. Comecei a planejar cada passeio em função de qual rua descia, o que é um jeito estranho de conhecer uma cidade, mas provavelmente honesto.
>
> Todo mundo recomenda a Igreja de São Francisco de Assis, então fui. Estava lotada, o guia despachava a explicação em três minutos e três grupos de turistas fotografavam o mesmo teto ao mesmo tempo. Da próxima vez eu vou sozinho, mais cedo. O pão de queijo, esse sim, merece o alarde. Comi um ainda quente numa padaria simples perto do Largo do Coimbra, e por uns trinta segundos entendi por que tanta gente organiza a viagem em torno de comida.
>
> O que eu não esperava era o quanto a cidade fica quieta longe das praças principais. Duas ruas ladeira acima de qualquer largo e vira roupa no varal, azulejo descascado, janela aberta e senhores assistindo futebol com o som alto. É esse o Ouro Preto que fico pensando, não o museu.
>
> O museu é bom. A vista é ótima, a fila é longa, e passei mais tempo empurrando a fila do que olhando qualquer coisa depois que entrei. Se tivesse só dois dias, trocaria o museu por uma tarde me perdendo pelas ruas.
>
> Eu voltaria, mas na seca e com tênis melhor. Ouro Preto não facilita nada para quem visita. Acho que gostei justamente disso, mesmo com minhas pernas discordando.

**Mudanças feitas:** manteve o relato de viagem em primeira pessoa e o nível de detalhe próximo do original, mas removeu a moldura de chatbot, a inflação de significância, a linguagem promocional, o entusiasmo forçado, os travessões, a cadência de regra de três, a conclusão genérica animada e o emoji. Reconstruiu o texto em torno de atrito concreto, sentimentos mistos, ritmo irregular e cenas específicas.


## Referência

Este skill é uma adaptação, para o português do Brasil, do projeto [Humanizer](https://github.com/blader/humanizer) (blader/humanizer), de código aberto sob licença MIT. O projeto original parte do guia da Wikipédia ["Signs of AI writing"](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing), mantido pelo WikiProject AI Cleanup, cujos padrões vêm da observação de milhares de textos gerados por IA na Wikipédia em inglês.

Os padrões específicos do português do Brasil (gerundismo analítico e de atendimento, conectivos automáticos, negações do tipo "não é apenas X, é Y", estrangeirismos e calques, contaminação com português europeu, formatação numérica no padrão americano, Title Case importado do inglês, estrutura de parágrafo uniforme) foram adaptados a partir de observações sobre como esses mesmos vícios de IA se manifestam quando o texto de saída é em português. A seção sobre perplexidade e burstiness, e o aviso sobre detectores de IA, se apoiam em pesquisa pública sobre como esses detectores funcionam e sobre suas taxas documentadas de falso positivo (ver README para as referências específicas).

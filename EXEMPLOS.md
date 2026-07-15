# Exemplos de Prompts

Dez prompts prontos para copiar e colar, cada um explorando um recurso diferente do skill: uso básico, calibração de voz (inline e por arquivo), registros diferentes (corporativo, pessoal, acadêmico, técnico, atendimento), o modo de diagnóstico sem reescrita, e a detecção específica de contaminação com português europeu.

Troque `/humanizador` pela forma como o seu harness invoca o skill instalado (comando de skill, menção direta, etc.).

---

### 1. Uso básico

Testa o fluxo padrão: identificar os padrões e devolver rascunho, auditoria e versão final.

```
/humanizador

A implementação do nosso novo sistema de gestão de estoque representa um marco fundamental na jornada de transformação digital da empresa. Adicionalmente, é importante destacar que a ferramenta desempenha um papel crucial na otimização dos processos logísticos, consolidando nossa posição como líderes no setor.
```

### 2. Calibração de voz inline

Testa a extração de ritmo e vocabulário a partir de uma amostra colada na própria mensagem.

```
/humanizador

Aqui vai uma amostra da minha escrita, pra você pegar o tom:

"Cheguei atrasado de novo hoje. Não que eu me importe muito, mas o chefe já tá de olho. Café requentado, reunião chata, o de sempre. Pelo menos o projeto novo tá andando."

Agora humanize este texto usando esse estilo:

"A equipe de desenvolvimento concluiu com êxito a primeira fase do projeto, alcançando resultados que superaram as expectativas iniciais estabelecidas pela diretoria."
```

### 3. Calibração de voz via arquivo

Testa o uso de um arquivo do usuário (posts antigos, e-mails, o que for) como referência de estilo.

```
/humanizador

Use o arquivo posts-antigos.txt como referência do meu estilo de escrita.

Humanize este texto:

[cole aqui o texto de IA]
```

### 4. E-mail corporativo

Testa o registro formal/profissional: humanizar sem descambar para o informal.

```
/humanizador, tom profissional (é um e-mail para o diretor financeiro):

Prezado Diretor, venho por meio deste comunicar que a equipe financeira, em um esforço colaborativo, conseguiu implementar diversas melhorias nos processos de reconciliação bancária, otimização de fluxo de caixa e redução de custos operacionais, consolidando assim nosso compromisso com a excelência financeira da organização.
```

### 5. Post de blog ou rede social

Testa PERSONALIDADE E ALMA: aqui o skill deve injetar opinião e variar o ritmo, porque o gênero pede voz.

```
/humanizador, isto é para um post pessoal de blog, pode injetar personalidade:

Recentemente decidi migrar minha vida inteira para o Linux, e a experiência tem sido verdadeiramente transformadora. A jornada não foi isenta de desafios, mas cada obstáculo superado reforçou minha convicção de que essa era a escolha certa.
```

### 6. Resumo acadêmico ou científico

Testa o oposto do exemplo anterior: aqui o tom neutro *é* a voz humana correta, e o skill não deveria injetar opinião pessoal nem calor emocional.

```
/humanizador, isto é o resumo de um artigo científico, mantenha o registro acadêmico e neutro, sem opinião pessoal:

O presente estudo teve como objetivo analisar o impacto da urbanização sobre a biodiversidade de anfíbios na Mata Atlântica. Adicionalmente, buscou-se investigar a correlação entre fragmentação florestal e riqueza de espécies, utilizando dados coletados ao longo de cinco anos em doze municípios do estado de São Paulo.
```

### 7. Documentação técnica ou changelog

Testa a escrita ancorada em diffs (padrão #27) e a neutralidade técnica, sem adicionar voz onde ela não pertence.

```
/humanizador, isto é para a documentação técnica de uma API, mantenha tom neutro e preciso:

Esta função foi adicionada para substituir a implementação anterior, que iterava sobre toda a coleção e causava um gargalo de desempenho O(n²). Ela também foi otimizada para reduzir o uso de memória, consolidando as melhorias de performance introduzidas na versão anterior.
```

### 8. Mensagem de atendimento ao cliente

Testa o gerundismo de atendimento (padrão #16) e o tom bajulador (padrão #33) juntos, um combo muito comum em texto de suporte gerado por IA.

```
/humanizador:

Ótima pergunta! Vou estar verificando sua solicitação em nosso sistema e estarei retornando com uma posição em até 48 horas úteis. Agradecemos imensamente pela sua paciência e compreensão nesse momento!
```

### 9. Diagnóstico sem reescrever (modo auditoria)

Testa o uso do skill como ferramenta de análise, não de reescrita: útil para revisar texto de terceiros ou treinar o olho para reconhecer os sinais.

```
/humanizador, não reescreva ainda, só me diga quais padrões de IA você identificou nesse texto e em que trecho:

[cole aqui o texto a analisar]
```

### 10. Contaminação com português europeu

Testa especificamente o padrão #8: útil quando o texto foi gerado ou traduzido por um modelo que mistura as variantes do português.

```
/humanizador, este texto é para um público brasileiro, fique atento a vocabulário de Portugal:

Estou a analisar o ficheiro que enviaste e vou verificar no ecrã do meu portátil se o problema persiste. Depois de tomar o pequeno-almoço, ligo-te a partir do meu telemóvel para combinarmos os próximos passos.
```

---

### Dica: combine recursos no mesmo prompt

Os exemplos acima isolam um recurso por vez, mas nada impede de combinar calibração de voz com um registro específico numa única chamada:

```
/humanizador, tom profissional, mas com a minha voz. Aqui vai uma amostra:

[amostra]

Humanize este e-mail:

[texto de IA]
```

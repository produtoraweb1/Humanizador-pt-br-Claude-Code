# AGENTS.md

Orientações para agentes de IA (Claude Code, Codex, Warp etc.) trabalhando neste repositório.

## O que é este repositório

Um skill de agente portátil, implementado inteiramente em Markdown. O artefato de execução é o `SKILL.md`: o agente lê o frontmatter YAML (metadados + ferramentas permitidas) seguido do prompt do editor. Não há build nem código para rodar, e o repositório deve evitar linguagem que limite o suporte a um ou dois harnesses específicos.

Este repositório é uma adaptação para **português do Brasil** do projeto [blader/humanizer](https://github.com/blader/humanizer) (MIT). Os padrões de pontuação e retórica universais (travessão, emoji, regra de três) foram traduzidos; os padrões específicos de língua (vocabulário de IA, hifenização, "Title Case") foram substituídos por equivalentes reais do português.

## Arquivos principais

- `SKILL.md`: o skill em si. Frontmatter YAML (`name`, `version`, `description`, `compatibility`, `allowed-tools`) seguido do índice rápido e da lista numerada e canônica de padrões, com exemplos de antes/depois. **Esta é a fonte de verdade.**
- `README.md`: para humanos, com instalação, uso, tabela-resumo dos padrões, a seção "Sobre Detectores de IA" e histórico de versões.
- `EXEMPLOS.md`: dez prompts prontos, cada um exercitando um recurso diferente do skill (uso básico, calibração de voz, registros diferentes, modo de diagnóstico).

## O contrato de manutenção

`SKILL.md`, `README.md` e `EXEMPLOS.md` devem se manter sincronizados. Ao mudar comportamento ou conteúdo:

- **Padrões:** o skill define atualmente **37 padrões numerados** (36 padrões de texto + o padrão estrutural/macro #37), mais uma seção não numerada sobre perplexidade e burstiness que se aplica a todos eles. Se você adicionar, remover ou renumerar algum padrão, atualize na mesma mudança: o Índice Rápido no início do `SKILL.md`, a tabela de padrões do README, o título "N padrões" e toda referência cruzada. Mantenha a numeração estável a menos que esteja renumerando de propósito.
- **Versão:** o frontmatter do `SKILL.md` tem um campo `version:`, e o `README.md` tem uma seção "Histórico de Versões". Suba os dois juntos para que os metadados batam com o skill.
- **Compatibilidade:** mantenha a linguagem de instalação e uso neutra em relação ao harness. O skill deve funcionar em qualquer harness de agente capaz de carregar instruções de skill em Markdown; Claude Code, OpenCode, Codex e outros são exemplos, não limites.
- **Correções não óbvias:** se você mudar o prompt para lidar com uma falha específica (uma reescrita repetidamente errada, uma mudança de tom inesperada), acrescente uma nota curta ao histórico de versões do README explicando o que foi corrigido e por quê.
- **Fidelidade ao português:** ao adicionar ou revisar um padrão, verifique se ele reflete um vício real de textos gerados por IA *em português*, não apenas uma tradução literal de um padrão do inglês. Nem todo padrão do original faz sentido nessa língua (por exemplo, a hifenização de pares de palavras do inglês não tem equivalente direto em português).
- **Honestidade sobre detecção:** a seção "Sobre Detectores de IA" (em `SKILL.md` e em `README.md`) é uma decisão editorial deliberada, não um espaço reservado. Não a remova nem a suavize para prometer "zero detecção" ou "burla qualquer detector": isso não é uma afirmação sustentável (ver as referências citadas no README), e prometer isso publicamente prejudica a credibilidade do projeto. Contribuições que transformem essa seção em uma peça de marketing devem ser recusadas.
- **Novos padrões precisam de exemplo real.** Ao aceitar um padrão novo, exija do contribuidor um exemplo de Antes/Depois plausível em português, não uma tradução de um padrão do humanizer original sem verificar se ele realmente ocorre em texto de IA em português.

## Editando o SKILL.md

- Preserve o frontmatter YAML válido (formatação e indentação).
- O prompt abaixo do frontmatter é o produto. Edite-o como um documento de instrução cuidadoso, não como código.

# Humanizer BR

A versão em português do [Humanizer](https://github.com/blader/humanizer), a skill do Siqi Chen que tira os padrões de escrita de IA de um texto. Ela reescreve o texto para que ele soe como a pessoa que o assina, sem mudar o que ele diz.

O Humanizer original caça palavras e frases em inglês. Aqui estão os mesmos 26 padrões, o mesmo jeito de trabalhar e o mesmo formato de resposta, com as expressões que aparecem em texto escrito em português. É uma adaptação independente, sem ligação com o autor do original.

**Antes** (texto inventado para o teste):

> Fundada em 2019, a Oficina do Pão serve como referência em panificação artesanal no coração de Curitiba. Nossa equipe conta com 6 padeiros e ostenta uma ampla gama de pães de fermentação natural, refletindo o nosso compromisso com a qualidade. Não é apenas uma padaria: é uma experiência. Abrimos de Terça a Domingo, das 7h às 19h.

**Depois:**

> A Oficina do Pão é uma padaria artesanal de Curitiba, fundada em 2019. Nossos 6 padeiros fazem vários tipos de pão de fermentação natural. Abrimos de terça a domingo, das 7h às 19h.

Junto com a versão final ela avisou o que cortou e pediu o que faltava. "Referência em panificação" saiu por ser elogio sem fato por trás, e para "ampla gama" ela perguntou quantos ou quais pães, para trocar pelo número.

Ela edita para quem lê. Não tenta passar em detector de IA, e o original avisa a mesma coisa: os detectores continuam marcando a maior parte do que sai.

## Instalar

### No Claude Code

Cole esta frase na conversa:

```text
Claude, instala a skill que tá nesse repositório pra eu usar em qualquer projeto e confere antes se tá tudo seguro: https://github.com/feBittar/humanizer-br
```

O Claude lê o `SKILL.md`, diz o que ele faz e copia o arquivo para `~/.claude/skills/humanizer-br/`. Ele pede a sua permissão antes de baixar e antes de gravar. Se o `/humanizer-br` não aparecer depois, feche e abra o Claude Code. Para instalar à mão, copie o `SKILL.md` para essa pasta.

### No claude.ai

Baixe o [humanizer-br.zip](https://github.com/feBittar/humanizer-br/releases/latest/download/humanizer-br.zip), vá em Customize > Skills, clique no "+" e em "Upload a skill", e envie o zip. Se a opção não aparecer, ligue a execução de código em Settings > Capabilities.

### No ChatGPT, no Gemini e em outras IAs

Copie o conteúdo do `SKILL.md` e cole nas instruções de um Projeto (ChatGPT) ou de um Gem (Gemini). Sem projeto, cole como primeira mensagem de uma conversa nova.

## Usar

Chame a skill e cole o texto:

```text
/humanizer-br

[o seu texto]
```

Ou peça do seu jeito:

```text
humaniza esse texto: [o seu texto]
```

Para reescrever um arquivo, diga o caminho:

```text
humaniza o texto de posts/lancamento.md
```

Num arquivo ela muda só a prosa. Código, comandos, caminhos, dados e links ficam como estão. O resultado é gravado por cima do arquivo, então guarde uma cópia se ele for importante.

### Com a sua voz

Mande junto dois ou três parágrafos que você escreveu:

```text
/humanizer-br

uma amostra de como eu escrevo:
[dois ou três parágrafos seus]

agora humaniza esse:
[o texto]
```

Ela segue o ritmo, as palavras e a pontuação da amostra, inclusive o travessão, se você usa.

## O que ela devolve

Quando você cola um texto, ela mostra o trabalho: um rascunho, uma lista curta do que ainda soa IA no rascunho e a versão final. Os fatos, os nomes e os números do texto ficam. Onde o texto é genérico, ela põe um detalhe que sabe ser verdadeiro ou pergunta para você, e avisa quando corta uma afirmação sem base.

## Os 26 padrões

Estão numerados do mais forte para o mais fraco. Os cinco primeiros ela corrige na primeira vez que aparecem. Num padrão marcado *fraco sozinho*, só age quando o mesmo trecho tem outros sinais, porque uma pessoa cuidadosa pode usar qualquer um deles de propósito.

| # | Padrão | Exemplo |
|---|--------|---------|
| 1 | Não é X, é Y | "Não é só uma música, é uma declaração." |
| 2 | Fechos de uma linha e fragmentos dramáticos | "E isso muda tudo." |
| 3 | Frases de efeito que soam profundas | "No fundo, o que realmente importa é..." |
| 4 | Preparação antes do ponto | "Vamos mergulhar.", "O resultado?" |
| 5 | Discutir com ninguém | "Não estou dizendo que..." |
| 6 | Trios forçados | "inovação, inspiração e insights" |
| 7 | Aberturas de frase repetidas | "Ela notou... Ela notou... Ela guardou..." |
| 8 | Travessão como conector universal (*fraco sozinho*) | "a política — anunciada sem aviso — afeta" |
| 9 | Ressalvas empilhadas (*fraco sozinho*) | "poderia potencialmente ser argumentado" |
| 10 | Convenções do inglês no português (*fraco sozinho*) | "em Março", "3.5%", "renovações, e indicações" |
| 11 | Voz passiva e sujeito sumido (*fraco sozinho*) | "Nenhum arquivo de configuração necessário." |
| 12 | Palavras gastas de IA | "vale ressaltar", "cenário", "jornada", "robusto" |
| 13 | Importância inflada | "marcando um momento decisivo" |
| 14 | Conexão ou associação vaga | "associado à liderança de" |
| 15 | Gerúndio de enfeite | "..., refletindo o compromisso com..." |
| 16 | Linguagem de vendas | "aninhada na deslumbrante região de" |
| 17 | Autoridade emprestada | "especialistas apontam" |
| 18 | Fugir do "é" e do "tem" | "serve como", "conta com", "ostenta" |
| 19 | Negrito de enfeite | "**Desempenho:** O desempenho foi aprimorado" |
| 20 | Títulos de enfeite | "🚀 Fase De Lançamento:" |
| 21 | Aspas curvas (*fraco sozinho*) | “assim” no lugar de "assim" |
| 22 | Resto de chatbot | "Ótima pergunta! ... Espero que ajude!" |
| 23 | Avisos de limite de conhecimento e chutes | "até a minha última atualização" |
| 24 | Título repetido na primeira frase | "## Desempenho" e, embaixo, "Velocidade importa." |
| 25 | Falar do documento em vez do assunto | "a tabela abaixo compara" |
| 26 | Explicar de novo o que o leitor já sabe | a resposta que refaz o diagnóstico antes da decisão |

## O que muda em relação ao original

A base é o Humanizer 4.0.0. A ordem dos padrões, os fortes e os fracos, os quatro passos de trabalho e os três modos de resposta são os mesmos. O que foi adaptado:

- As listas de expressões estão em português. Elas partem da tradução que a Wikipédia em português fez da página "Signs of AI writing" e somam o que os modelos repetem ao escrever na língua. As pesquisas que mediram palavras gastas de IA foram feitas com textos em inglês, e a skill avisa isso no padrão 12.
- O padrão 10 do original trata do hífen dos adjetivos compostos do inglês ("high-quality"), que não existe em português. Aqui ele cobre as convenções do inglês que vazam para o texto: vírgula antes do "e" final, mês e dia da semana com maiúscula, ponto decimal e expressões traduzidas ao pé da letra.
- No padrão 8, os travessões de diálogo e o hífen das palavras compostas ficam.
- O sujeito oculto ("Cheguei cedo") e o gerúndio comum ("estou escrevendo") não contam como sinal.
- A variedade do português, o registro informal e a gíria não são sinais. Ela não corrige "pra" nem "a gente".
- Os exemplos de antes e depois são os do original, traduzidos.

Este repositório tem só a skill. Os pacotes de plugin do original não vieram.

## Fontes

- [Humanizer](https://github.com/blader/humanizer), de Siqi Chen: a skill original.
- [Wikipedia: Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing), mantida pelo WikiProject AI Cleanup: a origem dos padrões.
- [Wikipédia: Sinais de texto gerado por inteligência artificial](https://pt.wikipedia.org/wiki/Wikip%C3%A9dia:Sinais_de_texto_gerado_por_intelig%C3%AAncia_artificial): a tradução da página, de onde vêm as expressões em português.

## Licença

MIT, a mesma do original. Veja o arquivo [LICENSE](LICENSE). A adaptação é do Felipe, [@ofelipemart](https://www.instagram.com/ofelipemart/) no Instagram.

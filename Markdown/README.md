![banner manual](./assets/coverMarkdown.png)

Markdown Syntax é uma sintaxe usada para padronizar e facilitar formatação de texto na web, utilizada em aplicativos como [Slack](https://slack.com/intl/pt-br/) e [GitHub](https://github.com/). Textos estilizados com **Markdown** são, na maioria dos casos, apenas texto com caracteres não-alfabéticos, como `#`, `\*` e `![]()`, usados para a configuração de títulos, listas, itálico, negrito e inserção de imagens.

O Markdown funciona como um conversor de texto para HTML: os caracteres não-alfabéticos são traduzidos como `<b>`, `<i>` e `<a href>`, etc. Já os textos sem formatação entram como parágrafo simples `<p>`.

# Lista de comandos em Markdown

## Títulos

Os títulos podem ser escritos com diversos tamanhos.

```md
# Título 1
## Título 2
### Título 3
#### Título 4
##### Título 5
###### Título 6
```

# Título 1
## Título 2
### Título 3
#### Título 4
##### Título 5
###### Título 6

---

## Formatação de texto - Ênfase

Para adicionar ênfase ao conteúdo que será escrito, usa-se o asterisco `*` ou traço-baixo (underline) `_`:



- **Negrito:** adicione dois asteriscos \*\*texto\*\* ou dois traços-baixos \_\_texto\_\_ no início e no fim do conteúdo.

- **Itálico:** adicione apenas um asterisco \*texto\* ou um traço-baixo \_texto\_ no início e no fim do conteúdo.


```md
**Texto em negrito**

_Texto em itálico_
```

**Texto em Negrito**

__Texto em Itálico__

> Se colocar crase antes e depois de uma palavra ou frase, a mesma é transformada de forma a dar ênfase, ótimo para marcar palavras reservadas.

> exemplo:
```md
Exemplo de frase com palavra reservada `function()` marcada.
```

Exemplo de frase com palavra reservada `function()` marcada.

---

## Lista não ordenada

```md
- Item 1
- Item 2
- Item 3
```
- Item 1
- Item 2
- Item 3

---

## Lista ordenada

```md
1. Item 1
2. Item 2
3. Item 3
```
1. Item 1
1. Item 2
1. Item 3

---

## Sub-Lista

```md
1. Primeiro item.   
	- Item 1  
	- Item 2  
	- Item 3
1. Segundo item.
	- Item 1  
	- Item 2  
	- Item 3 
```
1. Primeiro item.   
	- Item 1  
	- Item 2  
	- Item 3
1. Segundo item.
	- Item 1  
	- Item 2  
	- Item 3  

---

## Citação (Quote)

Para transformar um texto em uma citação ou comentário, semelhante ao código HTML `<blockquote>`, utilize o sinal `>` no início da linha que será formatada:


```md
> Texto aqui

>> Texto aqui

>>> Texto aqui
```

> Texto aqui

>> Texto aqui

>>> Texto aqui

---

## Códigos

Há dois modos de adicionar trechos de código ao Markdown:

- **Código em linha** _(inline)_: adicione um acento grave `ˋ` no início e no final do código.

- **Múltiplas linhas de código**: envolva as linhas de código com três acentos graves `ˋˋˋ` ou três tils `~~~`.

	- Em Alguns casos é permitido colocar o nome ou a sigla da linguagem que esta sendo usada, isso para mostrar um código com cores, como é o caso do discord.

> exemplo com javascript

```md
	```js
	const soma = function(x, y){
		return x + y;
	}

	soma (2, 3);
	soma(5, 4);
	```
```

```js
	const soma = function(x, y){
		return x + y;
	}

	soma (2, 3);
	soma(5, 4);
```

---

# Tasklists

```md
- [x] Atividade 1
- [ ] Atividade 2
- [ ] Atividade 3
```
- [x] Atividade 1
- [ ] Atividade 2
- [ ] Atividade 3

---

## Tabelas

Escolha os títulos das colunas e use `|` para delimitar as colunas. Depois, utilize hífen `-` na segunda linha para indicar que acima estão os títulos das colunas, usando novamente o `|` para delimitar colunas. Veja um exemplo abaixo:

```md
| Título 1 | Título 2 | Título 3 |
| --- | --- | --- |
| item | item | item |
| item | item | item |
```

| Título 1 | Título 2 | Título 3 |
| --- | --- | --- |
| item | item | item |
| item | item | item |

Para especificar o tipo de alinhamento que deseja ter nas tabelas, utilize `:` ao lado do campo horizontal de hífens `---`, na segunda linha da sua tabela.

**Alinhado a esquerda**: usar `:` no lado esquerdo (alinhamento padrão);
**Alinhado a direita**: usar `:` no lado direito;
**Centralizado**: usar `:` dos dois lados.

```md
| Título 1 | Título 2 | Título 3 |
|:- |:-:| -:|
| esquerda | Centro | Direita |
| esquerda | Centro | Direita |
```

| Título 1 | Título 2 | Título 3 |
|:- |:-:| -:|
| esquerda | Centro | Direita |
| esquerda | Centro | Direita |

Em markdown temos que basicamente desenhar a tabela, porém existe um gerador de tabelas que facilita a nossa vida: [link do gerador](https://www.tablesgenerator.com/markdown_tables)

Basta copiar o que o gerador criar e colar no README.md.

---

## Links

Existem duas formas de inserir link em Markdown, através de um **link direto** ou usando um **texto-âncora**:

- **Texto-âncora**: utilize os caracteres `[]()`, adicionando entre chaves o texto que você quer que apareça, e entre os parênteses, o endereço de destino, no formato `[exemplo](https://exemplo.com/)`.

- **Link direto**: envolva o endereço da web em chaves `<>`. O endereço ficará visível e será clicável pelo usuário. O endereço em forma de link direto tem o formato `<https://exemplo.com/>`.

	Este é um link em [formato de texto](), e este é um link direto https://google.com/.

- **Imagens & Gifs**

O código para inserir uma imagem no conteúdo é semelhante ao código de inserir links-âncora, adicionando um ponto de exclamação `!` no início do código, como no exemplo abaixo:

	![Alt ou título da imagem](URL da imagem)

> Esta é uma linha com uma imagem personalizada Eddie Feliz.![](./assets/eddie.png)
> 
> Imagens grandes podem estar em linhas individuais, para serem exibidas em maior tamanho.

---
[>> Voltar ao topo >>](#lista-de-comandos-em-markdown)
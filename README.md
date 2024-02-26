# Regex-MaterialDeEstudo
Material simples para quando quiser revisar conceitos ou comandos de Regex. 


# O que é e para que serve?

O RegEx serve para identificar padrões de caracteres em textos e ele está presente em quase todas as linguagens.


## Aplicações:
* Validar se um padrão de caractere existe.
* Extrair toda vez que encontrar o padrão.
* Achar um padrão e substituir por outro.

Essas aplicações podem ser feitas em um parágrado de texto, um texto estruturado como json e xml, ou em conteúdo de um código.


# Exemplo:
* Encontrar emails em um texto gigante.
* Achar um padrão de data e substituir por outro.
* Validar se CPF ou número telefonico estão no formato correto.


# Tabela

* . = qualquer caracter.
* \w \d \s = palavra, dígito e espaço em branco.
* [abc] = qualquer um entre 'a', 'b' ou 'c'.
* [^abc] = qualquer um que não seja 'a', 'b' ou 'c'.
* \t = tab.
* ^abc$ = início e fim da string.


## Quantificadores
* a* a+ a? = 0 ou mais, 1 ou mais, 0 ou 1.
* a{5} a{2,} = exatamente 5, 2 ou mais.
* a{1,3} = entre 1 e 3.
* ab|cd = encontrar 'ab'ou 'cd'.


# Exemplos práticos:

* Validação de telefone:
  
Para validar telefone no formato: 11-12345-6789
```
  \d\d[-]\d\d\d\d\d[-]\d\d\d\d
```

Como validar de maneira mais curta usando quantificadores:
```
  \d{2}[-]?\d{5}[-]?\d{4} ou \d{2}\-?\d{5}\-?\d{4}
```


* Validação de email:

Como validar email sem a possibilidade de algo após o '.com':
```
  \w+[@][a-zA-z]+[.][a-zA-Z]+
```

Como validar email com a possibilidade de algo após o '.com'(exemplo: .com.br ):
```
  \w+[@][a-zA-z]+[.][a-zA-Z]+([.][a-zA-z]+)?
```

Validando emails pré-definidos(gmail e outlook nesse exemplo):
```
  \w+[@](gmail|outlook)+[.][a-zA-Z]+([.][a-zA-z]+)?
```

* Validação de nome e sobrenome:

Encontrar nome e sobrenome no formato -> Xxxx Xxxx : 
```
  [A-Z][a-z]+ [A-Z][a-z]+
```

* Validação de CPF:

```
  [0-9]{3}[.][0-9]{3}[.][0-9]{3}[-][0-9]{2}
```

* Outro exemplos:

Se a string começa com o padrão escolhido, exemplo: telefone:
```
   ^\d{2}[-]?\d{5}[-]?\d{4} 
```

Se a string termina com o padrão escolhido, exemplo: telefone:
```
   \d{2}[-]?\d{5}[-]?\d{4}$ 
```

# Substituição de padrão

Irei usar como exemplo datas.
Para identificar uma data no formato YYYY-mm-dd:
```
  [0-9]{4}[-][0-9]{2}[-][0-9]{2}
```

Porém, para realizar uma substituição é necessário agrupar os blocos de código, dessa forma:
```
  ([0-9]{4})[-]([0-9]{2})[-]([0-9]{2})
```

Dessa maneira, serão criados "grupos", e para acessá-los, é só utilizar um '$' e em seguida o número referente a ordem do grupo.

Para alterar a ordem para o formato dd-mm-YYYY, seria feito assim:
```
  $3/$2/$1
```

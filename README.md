
# RegEx(Regular Expression)


### O que são expressões regulares?

É a definição de um padrão ou formato que um determinado texto deverá seguir.

### Como elas são definidas?

É utilizado os meta-caracteres para definir uma RegEx.

### Como "executar" expressões regulares?
O funcionamento das expressões regulares são dividido em 3 partes.  
A RegEx, a entrada de dados, e a engine.  
- A Regex é o padrão que você definiu.  
- A entrada de dados será onde vai ser aplicado o padrão definido na Regex.    
- A engine que faz tudo acontecer. Por padrão a maioria das linguagem suportam RegEx sem a necessidade de bibliotecas externas.

### O que são os meta-caracteres usados nas expressões regulares?
Os meta-caracteres são caracteres "comuns" que ganham um significado diferente dentro das expressões regulares. Os meta-caracteres formam uma estrutura que nos permite descrevermos o padrão que buscamos na entrada de dados.

### Formato de expressões regulares:
Uma expressão regular obrigatoriamente está delimitado entre barras, precisa conter ao menos 1 meta-caractere. As flags são opcionais.
``` javascript
/<meta-caracteres>/[flags]
```

### Flags:
Existem 3 principais flags que podem ser utilizadas:

Flag | Significado
-----|-----
   i |  "Ignore case". A expressão regular não levara em conta o uppercase ou lowercase, ou seja, A = a
   g | "Global search". Faz com que o RegExp procure todas as ocorrências do padrão na entrada de dados, e não apenas a primeira ocorrências.
   m | "Multiline". A expressão regular será aplicada para cada linha se a entrada possuir várias linhas.

### Matches:
Um match é quando uma parte da entrada de dados possui o formado definido pela RegEx. A expressão regular pode possuir varios matches.  
Este conceito de matches permite que expressões regulares sejam utilizadas para validar dados de entrada.

### Meta-caracteres:

###### Meta-caractere de inicio e fim de linha:
Para indicar que estamos lidando com o inicio ou fim da linha são utilizados o meta-caractere "^" para inicio da linha e "$" para final da linha.  
Sintaxe:
```javascript
  /^<...>/ - inicio da linhas
  /<...>$/ - fim da linha
```

###### Meta-caracteres de grupo de caracteres:
Pode ser necessário indicar um grupo de caracteres que podem ocorrer na entrada de dados. Os meta-caracteres utilizado é "[" para inicio do grupo e "]" para indicar o fim do grupo.  
Sintaxe:

```javascript
/[abc]/ - expressão regular que procura a primeira ocorrência de a ou b ou c
/[012]/ - expressão regular que procura a primeira ocorrência de 0 ou 1 ou 2
/[abc]/g - expressão regular que procura todas as ocorrências de a ou b ou c
/[012]/g - expressão regular que procura todas as ocorrências de 0 ou 1 ou 2
```

###### Meta-caractere ponto:
O meta-caractere ponto "." é o meta-caractere coringa que representa quaisquer caracteres, com exceção dos caracteres de quebra de linha e retorno da linha.  
Sintaxe:
```javascript
/./ - expressão regular que procurar um caractere qualquer
```

###### Meta-caracteres de quantificação:
As vezes precisamos repetir um determinado trecho de uma expressão regular. Os meta-caracteres utilizados são "{}" para determinar quantas vezes um determinado padrão de caracteres deve aparecer.  
Sintaxe:
```javascript
/.{5}/ - expressão regular que recupera quaisquer 5 caracteres
/.{1,5}/ - expressão regular que recupera de 1 a 5 quaisquer caracteres
/.{1,}/ - expressão regular que procura ao menos 1 caractere qualquer
```

Podemos também utilizar o meta-caractere "+" como quantificador, este meta-caractere indica que existe ao menos 1.  
Sintaxe:
```javascript
/<expressão>+/
/.+/ - expressão regular que faz match com uma entrada desde que ela possua ao menos 1 caractere. Equivale a “{1,}”;
```

Existe tambẽm o meta-caractere "?" que é um quantificador, ele é utilizado quando temos uma parte da expressão regular opcional, ou seja, 0 ou 1 ocorrência.  
Sintaxe:
```javascript
/<expressão>?/
/^9?/ - expressão regular que faz match com uma entrada; esta começando com o caractere “9” ou não;
```
E por fim o meta-caractere "\*" que também é um meta-caractere quantificador. É utilizado quando queremos zero ou mais ocorrências.
```javascript
/<expressão>*/
/^9*/ - expressão regular que faz match com uma entrada; esta começando com o caractere “9” ou não, e podendo conter qualquer quantidade de caracteres “9” no início do dado de entrada;
```

###### Meta-caracteres de AND:
Podemos precisar de condições logicas nas expressões regulares, podemos usar os meta-caracteres ".\*".  
Sintaxe:
```javascript
/<expressão1>.*<expressão2>/
 /^.{3}.*[0-9]{2}$/ - expressão regular que procura entradas que comecem com três caracteres quaisquer E terminem com dois números;
```

###### Meta-caracteres de OR:
Podemos precisar de condições logicas nas expressões regulares, podemos usar os meta-caracteres "|".  
Sintaxe:
```javascript
/(<expressão1>|<expressão2>)/
/^([Aa]|[Bb])/ - expressão regular que procura entradas cujo primeiro caractere seja a letra A OU a letra B. A busca será feita de maneira insensitiva;
```

###### Meta-caracteres de NOT:
Podemos precisar de condições logicas nas expressões regulares, podemos usar os meta-caracteres "^", este é o mesmo meta-caractere utilizado para inicio da linha porém quando utilizado dentro de um grupo ele funciona como o operador logico NOT.  
Sintaxe:
```javascript
/[^<grupo>]/
/^[^AaBb]/ - expressão regular que procura entradas cujo primeiro caractere NÃO seja a letra A, nem a letra B. A busca será feita de maneira insensitiva;
```

###### Meta-caractere de intervalo:
O meta-caractere "-" é utilizado para determinar um intervalo dentro do grupo de caracteres. Estes intervalos são referentes a tabela [ASCII](https://pt.wikipedia.org/wiki/ASCII) onde você pode consultar os possíveis intervalos.  
Sintaxe:
```javascript
/[start-end]/
/^[0-9]/ ou /^[a-z]/ - expressões que farão match com entradas que comecem com caracteres entre “0” e “9” (primeiro exemplo) ou entre “a” e “z” (segundo exemplo). Os caracteres especificados no intervalo também entram na verificação.
```
###### Meta-caractere de digito e não-digito:
Quando estamos buscado por dígitos(ou números) podemos usar o meta-caractere "\d" e quando esperamos por qualquer outro caractere diferente de números podemos usar o meta-caractere "\D".  
Sintaxe:
```javascript
/\d/ ou /\D/
/^\d{3}/ - expressão regular que busca entradas que comecem com três números ou dígitos;
/^\D{3}/ - expressão regular que busca entradas que comecem com três caracteres que não representem dígitos.
/[0-9]/ é equivalente a /\d/
/[^0-9]/ é equivalente a /\D/
```
###### Meta-caractere de alfanumérico e não-alfanumérico:
Quando precisamos procurar por caractere alfanumérico(números ou letras) usamos o meta-caractere "\w" e quando queremos pegar qualquer caractere não-alfanumérico usamos "\W". Caracteres não são considerados os que possuem acento, o "ç". o caractere "\_" é considerado alfanumérico.  
Sintaxe:
```javascript
/\w/ ou /\W/
/^\w{3}/ - expressão regular que busca entradas que comecem com três letras ou números;
/^\W{3}/ - expressão regular que busca entradas que comecem com três caracteres que não representem letras ou números.
\w equivale a [0-9a-zA-Z_];
\W equivale a [^0-9a-zA-Z_];
```
###### Meta-caracteres de caracteres de espaço e não-espaço:

Existe um meta-caractere para representa o espaço "\s", e para o não-espaço é usado o "\S". Caracteres como tabulação "\t", quebra de linha "\n" e retorno de linha "\r" também são considerados espaço.  
Sintaxe:
```javascript
/\s/ ou /\S/
/^\s{3}/ - expressão regular que busca entradas que comecem com três espaços;
/^\S{3}/ - expressão regular que busca entradas que comecem com três caracteres que não representem espaços.
```

###### Meta-caracteres de bordas:
As bordas são o inicio e o final das palavras. As engines de RegEx separam as palavras por espaço. O meta-caractere utilizado para definir borda "\b", e o meta-caractere "\B" é para localizar palavras cujos as bordas não possuam um determinado caractere.  
Sintaxe:
```javascript
/\b/ ou /\B/
/\ba/ - expressão regular que procura entradas cujo primeiro caractere seja a letra “a”;.
/a\b/: expressão regular que procura entradas cujo último caractere seja a letra “a”;
/\Ba/: expressão regular que procura entradas cujo primeiro caractere não seja a letra “a”;
/a\B/: expressão regular que procura entradas cujo último caractere não seja a letra “a”;
```

###### Meta-caracteres de grupos de captura e não-captura:
É utilizado o meta-caractere "()" para criar um grupo de captura ou "(?:)" para criar um grupo de não-captura. Grupo de captura é utilizado quando querermos que algo seja aplicado a um grupo de expressão regular.  
Exemplo:
Deve ser buscado palavras uma ou mais sequencias de ab.  
`/ab+/` - dessa forma não vai ocorrer da forma esperada o meta-caractere "+" só será aplicado ao b.  
`/(ab)+/` - está é a forma correta, o meta-caractere "+" sera aplicado ao grupo ab.  
Por ser um grupo de captura os resultados de ab serão guardados para um futuro processamento independente do resto da expressão regular. Isso gera um processamento mais lento, se não for necessário o processamento desse grupo separadamente deve ser utilizado o grupo de não-captura.  
`/(:?ab)+/` - dessa forma este grupo fará apenas parte da expressão regular, não será guardado os resultados de ab para um futuro processamento, só será levando em consideração os resultados completo da expressão regular, há não ser que exista grupos de captura em outras partes da expressão regular.



###### Meta-caracteres de sucessão e não-sucessão:
As vezes precisamos capturar determinados caracteres só se vir um outro caractere após ele. o meta-caractere utilizado é o "(?=)", e o meta-caractere "(?!)" é utilizado quando queremos que algo não seja precedido por esse caractere Por exemplo:  

Suponhamos que você queira pegar apenas os valores de metros então seria a seguinte expressão `/\d+(?=m)/gm`, se utilizamos `/\d+(?!m)/` agora não vai pegar nenhuma medida de metros, sera pego qualquer outra digito precedido por qualquer outro caractere diferente do "m", neste caso 90cm.

90cm  
2m  
15m

Sintaxe:
```javascript
/(?=)/ ou /(?!)/
/ <caractere>(?=<caractere>)/ ou /<caractere>(?!<caractere>)/
/a(?=b)/ - expressão regular que procura capturará o caractere “a” somente se ele for seguido pelo caractere “b”;
/a(!=b)/ - expressão regular que procura capturará o caractere “a” somente se ele NÃO for seguido pelo caractere “b”;
```

# logica-modulo02-senac


![javascript](https://engineering.fb.com/wp-content/uploads/2012/12/javascript-illustration.png)


1. [Estruturas Condicionais](#estruturas-condicionais)
2. [Function and Arrow function](#function-and-arrow-function)
3. [Função Callback](#função-callback)
4. [Arrays](#arrays)
5. [Objetos](#objetos)
6. [Classes](#classes)


---


### Estruturas Condicionais

> Na programação utilizamos estruturas condicionais para decidir se algo deve ou não acontecer. Ou seja, para tomada de decisão.

- if/ else if/ else


```
if (condição) {
  // se a condição for verdadeira, o código aqui dentro será executado
} else {
  // se a primeira condição não for verdadeira, o código aqui dentro será executado
}
```

````
if (condição) {
  // se a condição for verdadeira, o código aqui dentro será executado
} else if (condição) {
  // se a condição anterior não for verdadeira e a condição atual for, o código aqui dentro será executado
} else {
  // se as condições anteriores não forem verdadeiras, o código aqui dentro será executado
}
````

Exemplo:

Se for maior de idade pode entrar:
```
if (idade >= 18) {
  console.log('pode entrar')
}
```

Agora queremos também mandar mensagem caso não seja maior de idade:

```
if (idade >= 18) {
  console.log('pode entrar')
} else {
  console.log('entrada permitida apenas para maiores de idade.')
}
```

Agora mudamos um pouco a regra e complicamos um poco:
- se for maior de 18 entra
- se for mais de 18 e menor de 21 entra, mas nao pode consome bebida alcolica
- se for maior de 21 entra e pode consome bebida alcolica.

````
if (idade >= 18 && idade < 21) {
  console.log('pode entrar, mas não pode consumir bebidas alcolicas')
} else if (idade >= 21) {
  console.log('pode entrar e consumir bebidas alcolicas')
} else {
  console.log('entrada permitida apenas para maiores de idade.')
}
````
O else if pode ser repetido quantas vezes for necessário.

__Exemplo de condicional usando ternário:__

```js
const nota = 3

(nota >= 7) ? 'aprovado' : 'reprovado'
```

- Switch Case

> A estrutura condicional switch permite executar um bloco de código diferente de acordo com cada opção (cada case) especificada. Seu uso é indicado quando os valores a serem analisados nessas condições são pré-definidos.

A sintaxe da SC é:

```
switch(expression) {
  case x:
    // code block
    break;
  case y:
    // code block
    break;
  default:
    // code block
}
```

Observe na prática:
````
const produto = 'mamão'

switch (produto) {
  case 'laranja':
    console.log('laranja custa 30 centavos');
    break;
  case 'manga':
  case 'mamão':
    console.log('manga e mamão custam 2.79 reais.');
    break;
  default:
    console.log('desculpe, nao temos o produto desejado');
}
````

---
### Function and Arrow function

Declarando funções:

```js
function falar() {### Switch Case

A função switch case é uma ferramenta essencial na caixa de ferramentas de qualquer programador JavaScript. Ela oferece uma maneira eficiente de lidar com múltiplas condições, evitando o uso excessivo de estruturas condicionais aninhadas. A estrutura switch case é especialmente útil quando se precisa executar diferentes blocos de código com base no valor de uma expressão.

A sintaxe do Switch Case é:
```js
switch (expressão) {
case valor1:
  // bloco de código a ser executado
  break;
case valor2:
  // bloco de código a ser executado
  break;
// mais cases...
default:
  // bloco de código a ser executado se nenhum case combinar
} 
```
Agora observe o exemplo:

```js
const produto = 'mamão'

switch (produto) {
  case 'laranja':
    console.log('laranja custa 30 centavos');
    break;
  case 'manga':
  case 'mamão':
    console.log('manga e mamão custam 2.79 reais.');
    break;
  default:
    console.log('desculpe, nao temos o produto desejado');
}
```
```js

  return 'Pipipi popopo'
}

function dobro(num) {
  return num * 2
}

function calcularMedia(nota1, nota2, nota3) {
  const soma = (nota1 + nota2 + nota3)
  const media = soma / 3
  return media
}
```

Ou, podemos declarar as mesmas funções da seguinte forma:

```js
const falar = function() {
  return 'Pipipi popopo'
}

const dobro = function(num) {
  return num * 2
}

const calcularMedia = function(nota1, nota2, nota3) {
  const soma = (nota1 + nota2 + nota3)
  const media = soma / 3
  return media
}
```

Arrow function possui uma sintaxe mais curta, e sabemos que é uma função pelo símbolo `=>`

```js
const falar = () => {
  return 'Pipipi popopo'
}

const dobro = (num) => {
  return num * 2
}

const calcularMedia = (nota1, nota2, nota3) => {
  const soma = (nota1 + nota2 + nota3)
  const media = soma / 3
  return media
}
```

Conseguimos deixar a função ainda mais concisa, pois:
- caso a função só tenha uma linha de instrução, as chaves `{}` são opcionais
- e ao remover as chaves `{}`, o `return` é implícito e, portanto, também removemos:

  ```js
  const falar = () => 'Pipipi popopo'

  const dobro = num => num * 2
  ```

- caso a função só tenha 1 parâmetro, os parênteses em volta do parâmetro `(param)` também são opcionais:

  ```js
  const dobro = num => num * 2
  ```

MDN: [Arrow function](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Functions/Arrow_functions)

---
### Função Callback

> Uma função callback é uma função passada a outra função como parâmetro, que é então invocada dentro da função externa para completar algum tipo de rotina ou ação. *Fonte MDN: [callback](https://developer.mozilla.org/pt-BR/docs/Glossario/Callback_function)*

```js
function somar(a, b) {
  return a + b
}

function subtrair(a, b) {
  return a - b
}

function multiplicar(a, b) {
  return a * b
}

function dividir(a, b) {
  return a / b
}

function ordenar(a, b) {
  if (a <= b) {
    return [a, b]
  } else {
    return [b, a]
  }
}

function calcular(a, b, callback) {
  return callback(a, b)
}

const num1 = 7
const num2 = 2

const somaDoisNumeros = calcular(num1, num2, somar)
console.log(somaDoisNumeros) // 9

const subtracaoDoisNumeros = calcular(num1, num2, subtrair)
console.log(subtracaoDoisNumeros) // 5

const multiplicacaoDoisNumeros = calcular(num1, num2, multiplicar)
console.log(multiplicacaoDoisNumeros) // 14

const divisaoDoisNumeros = calcular(num1, num2, dividir)
console.log(divisaoDoisNumeros) // 3.5

const ordenarDoisNumeros = calcular(num1, num2, ordenar)
console.log(ordenarDoisNumeros) // [2, 7]
```

Deixando a sintaxe reduzida:

```js
const somar = (a, b) => a + b

const subtrair = (a, b) => a - b

const multiplicar = (a, b) => a * b

const dividir = (a, b) => a / b

const ordenar = (a, b) => (a <= b) ? [a, b] : [b, a]

const calcular = (a, b, callback) => callback(a, b)
```

---

### Arrays

Declaração de arrays

```js
const lista = new Array('pera', 'uva', 'maçã')

const numeros = [9, 2, 5]
```

Acessando elementos pela posição do array:

```js
const primeiroItem = lista[0]

console.log(primeiroItem) // pera
```

Tamanho de array:

```js
const tamanho = numeros.length

console.log(tamanho) // 3
```

Atribuição via desestruturação

```js
const [primeiro, segundo, terceiro] = lista

console.log(primeiro) // pera
console.log(segundo) // uva
console.log(terceiro) // maçã
```

---

### Objetos

> Objetos em JavaScript, assim como em muitas outras linguagens de programação, podem ser comparados com objetos na vida real. O conceito de objetos em JavaScript pode ser entendido com objetos tangíveis da vida real.

Declaração de objetos

```js
const objeto = new Object()
objeto.nome = 'cadeira'
objeto.tipo = 'madeira'
objeto.peso = 7

const pokemon = {
  nome: 'Pikachu',
  tipo: 'elétrico',
  altura: 40.6,
}
```

Acessando o valor de uma propriedade do objeto.

```js
console.log(pokemon.nome) // Pikachu
```

Declarando uma variável de mesmo nome que a propriedade.

```js
const nome = pokemon.nome
const tipo = pokemon.tipo
const altura = pokemon.altura

console.log(nome) // Pikachu
console.log(tipo) // elétrico
console.log(altura) // 40.6
```

Atribuição via desestruturação

```js
const { nome, tipo, altura } = pokemon

console.log(nome) // Pikachu
console.log(tipo) // elétrico
console.log(altura) // 40.6
```

MDN: [destructuring assignment](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Operators/Atribuicao_via_desestruturacao)

---


### Date

> Cria uma instância JavaScript de Date que representa um único momento no tempo. Objetos Date são baseados no valor de tempo que é o número de milisegundos desde 1º de Janeiro de 1970 (UTC).


```js
const hoje = new Date()

console.log(hoje) // 2020-09-05T10:56:49.693Z

const dia = hoje.getDate()
const mes = hoje.getMonth()
const ano = hoje.getFullYear()

console.log(dia, mes, ano) // 5 8 2020 🤔

const dataFormatada = hoje.toLocaleDateString('pt-BR')
console.log(dataFormatada) // 05/09/2020

const options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' }
const dataLonga = hoje.toLocaleDateString('pt-BR', options)
console.log(dataLonga) // sábado, 5 de setembro de 2020
```
MDN: [date](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Date),
[toLocaleDateString](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Date/toLocaleDateString)

---

### Classes

> Uma classe em JavaScript funciona como um molde para criar objetos. Podemos definir as propriedades e os métodos que os objetos criados terão a partir dela. É como se fosse uma “planta” de construção para o objeto.


```js
class Pessoa {
  constructor(nome, idade, andando = false, caminhada = 0) {
    this.nome = nome
    this.idade = idade
    this.andando = andando
    this.caminhada = caminhada
  }

  andar(metros) {
    this.andando = true
    this.caminhada += metros
  }
}

const professora = new Pessoa('Cintia', 35)
console.log(professora) // Pessoa { nome: 'Cintia', idade: 35, andando = false, caminhada: 0 }

professora.andar(200)
console.log(professora) // Pessoa { nome: 'Cintia', idade: 35, andando = true, caminhada: 200 }

```

MDN: [class](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Classes)

---

### Bora estudar mais?

- [if...else](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/if...else), [ternary](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Operators/Operador_Condicional)
- [Switch Case](https://www.devmedia.com.br/javascript-switch/39761)
- [Date](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Date)
- [Classes](https://www.hashtagtreinamentos.com/classes-em-javascript?gad_source=1&gclid=Cj0KCQjwwuG1BhCnARIsAFWBUC2wVXI52-Z_xaWKri56krGJmR4kER5O63J4E71byHJMdbtiClqqVjEaAh8qEALw_wcB)
- [Objetos](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Working_with_objects)

# logica-modulo02-senac

1. [Conditional if and else](#conditional-if-and-else)
2. [Function and Arrow function](#function-and-arrow-function)
3. [Função Callback](#função-callback)
4. [Arrays](#arrays)
5. [Objetos](#objetos)
6. [Classes](#classes)


---

### Conditional if and else

Exemplo de condicional usando `if...else`:

```js
const nota = 3

if (nota >= 7) {
  return 'aprovado'
} else {
  return 'reprovado'
}
```

Exemplo de condicional usando ternário:

```js
const nota = 3

(nota >= 7) ? 'aprovado' : 'reprovado'
```

MDN: [if...else](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/if...else), [ternary](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Operators/Operador_Condicional)

---

### Function and Arrow function

Declarando funções:

```js
function falar() {
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
---

### Objetos

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

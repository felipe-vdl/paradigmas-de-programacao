# Fundamentos de Paradigmas de Programação

### O que é um paradigma de programação?
Podemos definir um paradigma de programação como uma abordagem/modo de construção de um algoritmo.

Um paradigma de programação determina como os problemas são abordados e resolvidos em uma linguagem de programação, influenciando na sintaxe, estrutura, e nas práticas utilizadas no desenvolvimento de um software.

Existem diferentes paradigmas, e cada um deles oferece uma forma diferente de pensar sobre a solução de problemas. Entretanto, dependendo da linguagem de programação, múltiplos paradigmas podem ser utilizados em conjunto (por exemplo, a linguagem JavaScript suporta os paradigmas: Procedural, Orientado a Objetos, Funcional, e Orientado a Eventos).

# Categorias dos Paradigmas de Programação:
Antes de elaborarmos cada paradigma em específico, é importante citar que podemos classificar os paradigmas em três grandes categorias (imperativo, declarativo e reativo):

## Paradigmas Imperativos:
Os paradigmas imperativos são aqueles onde descrevemos diretamente **COMO** um programa deve ser executado, especificando passo a passo as operações que serão realizadas. Geralmente, são focados em modificações de estado por meio de instruções sequenciais (podemos definir o "estado" de um programa como o conjunto de dados que define a condição atual do programa, incluindo suas variáveis, estruturas de dados, objetos, entre outros elementos que influenciam o comportamento do programa).

As principais características dos paradigmas imperativos são:
- Enfatiza a execução sequencial
- Uso de controles de fluxo (condicionais) e estruturas de repetição (for, while)
- Utiliza variáveis mutáveis
- O estado do programa pode ser alterado diretamente

Podemos citar alguns paradigmas imperativos, como: 
- Procedural
- Orientado a Objetos

#### Exemplo de código JavaScript:
```js
function somar(a, b) {
  let resultado = 0;

  resultado = a + b;

  return resultado;
}

console.log(somar(5, 3)); // Saída: 8
```

No exemplo acima definimos como a soma deve ser realizada, atribuindo valores e manipulando variáveis. O passo a passo do programa é diretamente especificado, e o estado do programa é alterado, desta forma podemos dizer que é um trecho de código imperativo.

#### Exemplo 2 em JavaScript:
```js
const numeros = [1, 2, 3, 4, 5, 6];
let resultado = [];

for (let i = 0; i < numeros.length; i++) {
  if (numeros[i] % 2 === 0) {
    resultado.push(numeros[i] * 2);
  }
}

console.log(resultado); // [4, 8, 12]
```

Aqui, estamos modificando diretamente o array **resultado**, utilizando uma estrutura de repetição **for**, e verificando cada número diretamente.

## Paradigmas Declarativos:
Os paradigmas declarativos focam em **O QUE** deve ser feito/alcançado, sem especificar quais serão os passos executados pelo programa internamente para chegar no resultado daquela instrução.

Em vez de alterar diretamente os dados do programa, usamos funções que criam novas versões dos dados sem modificar os originais (chamamos isto de imutabilidade).

#### As principais características dos paradigmas declarativos são:
- Foca no resultado, e não na sequência específica de instruções executadas
- Evita mudanças de estado do programa
- Utiliza funções high-order e composição de funções
  - Funções high-order são aquelas que aceitam funções como parâmetro, elas podem retornar uma outra função, ou o resultado em si.

  - A composição de funções é o encadeamento de múltiplas funções (cada função na cadeia recebe o resultado da função anterior na cadeia), o objetivo é transformar os dados com o uso de pequenas funções, ao invés de escrever uma única sequência maior de instruções.

#### Exemplo em JavaScript:
```js
const somar = (a, b) => a + b;

console.log(somar(5, 3)); // Saída: 8
```

O código apenas declara o que deve acontecer (retornar a soma), sem detalhar os passos intermediários.

#### Exemplo 2 em JavaScript:
```js
const numeros = [1, 2, 3, 4, 5, 6];

const resultado = numeros
  .filter(n => n % 2 === 0) // Filtra números pares
  .map(n => n * 2); // Dobra os valores filtrados

console.log(resultado); // Saída: [4, 8, 12]
```

Neste exemplo, não manipulamos diretamente o estado do programa (os métodos de array .filter() e .map() retornam novos arrays), também fizemos a utilização de composição de funções (.filter(), seguido de .map()).

Outros exemplos de linguagens focadas em programação declarativa são:
- CSS - "O botão deve ter a cor azul"
- SQL - "SELECIONE os dados onde a idade seja maior que 20"

### Diferenças Práticas: Imperativo vs. Declarativo
#### Imperativo:
- Como fazer (passo a passo)
- Explícito (for, if/else)
- Variáveis mutáveis
- Tende a ser mais verboso
- for, while, if/else

#### Declarativo:
- O que fazer (resultado esperado)
- Implícito (funções de alto nível)
- Evita mutações diretas
- Tende a ser mais conciso
- .map(), .filter(), .reduce(), SQL

## Paradigmas Reativos:
Os paradigmas reativos focam na propagação de eventos e mudanças, permitindo que o sistema reaja automaticamente a ocorrência de eventos. Ele é amplamente usado em interfaces gráficas e programação assíncrona.

As principais características dos paradigmas reativos são:
- Programação baseada em eventos e fluxos de dados assíncronos
- Usa "observers" que reagem a mudanças de estado
- Usa "listeners" que reagem a ocorrências de eventos
- Muito utilizado em interfaces gráficas e programas assíncronos

## Programas Assíncronos:
Na programação assíncrona, algumas tarefas podem ser executadas independentemente de outras (ou seja, o programa não precisa esperar por uma operação ser completa para continuar a execução de outras operações que não dependem dela).

Ao invés de bloquear o fluxo de execução com um processo demorado (por exemplo, uma requisição de rede, uma leitura de arquivo no disco, etc), o código pode continuar sua execução e, quando o processo assíncrono terminar, notificar o programa, para que as próximas etapas que dependem dele possam ser realizadas.

Esse tipo de comportamento é especialmente útil em situações onde a espera por uma operação externa pode bloquear o programa de fazer outras coisas (como leituras de disco, chamada de APIs externas, execuções baseadas em tempo ou eventos, e tarefas longas em geral).

### Exemplos comuns de processos que usam programação assíncrona são:
- Requisições de rede (ex.: chamada de APIs externas)
- Programas orientados a eventos (ex.: EventEmitter e Streams do JavaScript e Node.js)
- Apache Kafka e RabbitMQ (streaming de eventos em sistemas distribuídos)
- IoT (dispositivos que reagem a eventos)

#### Exemplo de programa reativo em JavaScript:
```js
document.getElementById("botaoExemplo").addEventListener("click", () => {
  console.log("O botão foi clicado!");
});
```

Neste caso, o programa não controla diretamente o fluxo, ele apenas reage quando o evento de clique no botão especificado ocorre.

## Resumo das Categorias de Paradigmas:
### Imperativo:
  Foca em como resolver o problema, com a definição de instruções passo a passo. Por exemplo:
  - JavaScript procedural, entre outras linguagens procedurais como C, Python, etc.

### Declarativo:
  Foca em o que precisa ser feito/alcançado, sem definir os passos específicos da execução. Por exemplo:
  - SQL
  - CSS
  - Programação Funcional

### Reativo:
  Baseado em eventos e reações a mudanças.
  - Eventos de interface, observers
  - JavaScript EventEmitter
  - Node.js Streams

# Paradigmas de Programação:
  Agora, vamos especificar alguns dos paradigmas de programação mais comuns, que são:
  1. Programação Procedural
  2. Programação Orientada a Objetos (OOP)
  3. Programação Funcional
  4. Programação Orientada a Eventos (EDP)

  Vamos explorar os conceitos básicos de cada um deles. Utilizaremos alguns exemplos de código em JavaScript, que é uma linguagem que suporta diversos paradigmas de programação.

## Programação Procedural:
Na programação procedural, organizamos o código como uma sequência de instruções e procedimentos. Esse paradigma segue a abordagem "passo a passo", onde especificamos diretamente as operações do programa.

As características principais da programação procedural incluem:
- Organização baseada em funções que podem ser declaradas
- Uso de variáveis globais e locais
- Estruturas de controle de fluxo e repetição (if, while, for)

#### Exemplo em JavaScript:
```js
let resultado = 0;

// Função que calcula a área de um retângulo
function calcularArea(largura, altura) {
  resultado = largura * altura
}

// Chamando a função
calcularArea(5, 3)

console.log(resultado); // 15
```

## Programação Orientada a Objetos (OOP):
Na programação orientada a objetos, organizamos o código em torno de objetos, que são instâncias de classes declaradas no programa. Objetos podem possuir atributos (dados) e métodos (funções abarcadas no objeto).

#### As características principais da programação orientada a objetos são:
- **Encapsulamento:** Os dados e métodos são guardados dentro objetos.

- **Abstração:** Os objetos escondem os detalhes internos e expõem apenas seus atributos (que podem ser lidos/modificados) e métodos (que podem ser executados).

- **Herança:** Podemos declarar uma classe com base em outra classe (a nova classe herda todas as características da classe base, pode ter seus próprios atributos e métodos, e também é possível alterar os atributos/métodos herdados).

- **Polimorfismo:** Permite tratar as classes de forma genérica, ou seja, quando uma certa classe é herdeira de uma classe base, pode-se dizer de forma genérica que esta classe pertence a classe que foi herdada. Por exemplo, considere que uma classe "Felino" e uma classe "Canino" herdam uma classe base "Animal". Neste caso, podemos dizer que objetos da classe "Felino" e "Canino" pertencem a classe "Animal".

### Exemplo em JavaScript:
```js
class Animal {
  // Atributos
  constructor(nome, cor) {
    this.nome = nome
    this.cor = cor
  }

  // Método de comunicação
  falar() {
    return "Hello World!";
  }
}

class Canino extends Animal {
  constructor(nome, cor, dono) {
    super(nome, cor);
    this.dono = dono;
  }

  falar() {
    return "Au! Au!"
  }
}

class Felino extends Animal {
  constructor(nome, cor) {
    super(nome, cor);
  }

  falar() {
    return "Miau!"
  }
}

const cachorroUm = new Canino("Magrelinho", "Caramelo", "Fulano");
cachorroUm.falar(); // "Au! Au!"

const gatoUm = new Canino("Mingau", "Branco");
gatoUm.falar(); // "Miau!"
```

## Programação Funcional (FP):
Na programação funcional, as funções são os elementos fundamentais do código, neste paradigma as funções são comumente passadas como parâmetros de outras funções, elas também podem ser os valores retornados por funções. A programação funcional foca no uso de **funções puras**, **imutabilidade**, e expressões sem **efeitos secundários**.

Vamos entender melhor cada um desses conceitos:
### Funções Puras:
Uma função pura é aquela que sempre retorna o mesmo resultado para os mesmos parâmetros, e não causa efeitos secundários.
#### Exemplo de função pura:
```js
function somar(a, b) {
  return a + b;
}

console.log(somar(2, 3)); // Sempre retorna 5
console.log(somar(2, 3)); // Sempre retorna 5
```

#### Exemplo de função impura:
```js
let total = 0;

function somarImpuro(a) {
  total += a;  // Modifica uma variável externa a função (efeito secundário)
  return total;
}

console.log(somarImpuro(2)); // Retorna 2
console.log(somarImpuro(2)); // Retorna 4
```

### Imutabilidade:
A imutabilidade significa que os dados não serão modificados diretamente. Em vez disso, criamos novos valores ao invés de alterar os existentes. O objetivo é evitar efeitos inesperados no código, quando um mesmo conjunto de dados é utilizado por diversos processos diferentes.

#### Exemplo de código imutável:
```js
const numeros = [1, 2, 3];

const novosNumeros = [...numeros, 4]; // Cria um novo array
console.log(numeros);       // [1, 2, 3] (original não foi alterado)
console.log(novosNumeros);  // [1, 2, 3, 4] (novo array)
```

#### Exemplo de código mutável:
```js
const numeros = [1, 2, 3];

numeros.push(4); // Modifica diretamente o array original (efeito secundário)
console.log(numeros); // [1, 2, 3, 4]
```

### Efeitos Secundários:
Um efeito secundário (também chamado de side effect) ocorre quando uma função modifica ou afeta algo fora do escopo local dela, como:
- Alterar variáveis globais, ou fora do escopo local da função
- Fazer requisições HTTP
- Fazer operações de escrita em um banco de dados ou disco

Em geral, efeitos secundários podem causar comportamentos inesperados, o paradigma da programação funcional tenta minimizá-los.

### As características principais da programação funcional são:
- Uso de funções puras
- Imutabilidade
- Uso de funções high-order
- Uso de composição de funções
- Substituição de estruturas de repetição por funções recursivas

### Exemplo de programação funcional em JavaScript (função pura e high-order):
```js
// Função pura (não modifica nada fora dela)
const calcularArea = (largura, altura) => largura * altura;

console.log(calcularArea(5, 3)); // 15

// Função high-order (recebe outra função como argumento)
const aplicarOperacao = (a, b, operacao) => operacao(a, b);

// Chamando com uma função anônima
console.log(aplicarOperacao(5, 3, (x, y) => x * y)); // 15

// Chamando com uma função declarada
const somar = (x, y) => x + y;

console.log(aplicarOperacao(5, 3, somar)); // 8
```
### Exemplo de programação funcional em JavaScript (função pura e recursiva):
```js
// Função recursiva para calcular o fatorial
const fatorial = (n) => {
  if (n === 0) return 1; // Caso base
  return n * fatorial(n - 1); // Chamada recursiva
};

console.log(fatorial(5)); // Saída: 120
```

## Paradigma Orientado a Eventos (EDP):
Também conhecido como Event-Driven Programming, ou EDP, é um paradigma onde as operações do programa são impulsionadas por eventos. Os eventos podem ter diversas naturezas, como ações do usuário, notificações de um processo, ou mudanças de estado observadas. Esse paradigma é amplamente utilizado em interfaces gráficas e sistemas assíncronos.

### As principais características da programação orientada a eventos são:
- Operações baseadas em eventos (o código reage a eventos notificados e mudanças observadas)

- Uso de listeners, observers e handlers (os listeners são responsáveis por "ouvir" eventos, observers são responsáveis por observar modificações, e os handlers definem o que fazer quando o evento/modificação ocorre)

- Assincronismo (as aplicações baseadas em eventos tendem a utilizar programação assíncrona, para reagir a múltiplos eventos sem bloquear a execução do programa)

- Desacoplamento (os componentes podem funcionar de forma independente, apenas reagindo a eventos quando necessário)

### Exemplo de programação orientada a objetos em JavaScript:
Na programação web, os eventos são muito utilizados para criar interfaces reativas e manipuláveis.
```js
// Seleciona um botão pelo ID
const botao = document.getElementById("meuBotao");

// Adiciona um evento de clique
botao.addEventListener("click", () => {
  alert("Botão clicado!");
});
```

No código acima, quando o botão é clicado, um evento de "click" é disparado e a função passada como parâmetro é executada.

### Exemplo em Node.js com o módulo EventEmitter:
Nas aplicações backend com Node.js, os eventos também podem ser muito úteis.
```js
import EventEmitter from "events";
const emissor = new EventEmitter();

// Definindo um evento personalizado
emissor.on("mensagem", (texto) => {
  console.log(`Mensagem recebida: ${texto}`);
});

// Disparando o evento
emissor.emit("mensagem", "Olá, mundo!");
```

Aqui, o EventEmitter permite criar eventos personalizados, que podem ser emitidos em outros trechos do código de forma assíncrona.

## Paradigma Lógico:
Para finalizarmos nossa apresentação dos paradigmas de programação, podemos citar um paradigma que é menos comum na programação web e em linguagens populares como JavaScript. Entretanto, ele é amplamente utilizado em áreas como inteligência artificial, linguística computacional e sistemas especialistas. O paradigma lógico se baseia na lógica matemática para descrever problemas e encontrar soluções automaticamente.

### As principais características do paradigma lógico são:
- **Baseado em regras e fatos declarados:**
  Em vez de definir como um problema deve ser resolvido, nós definimos o que é verdadeiro e quais regras/propriedades se aplicam.

- **Inferência automática:**
  O sistema usa um motor lógico (ou motor de inferência), que deduz conclusões a partir dos fatos e regras fornecidas.

- **Sem controle de fluxo:**
  O próprio motor de inferência é responsável pela ordem das operações efetuadas.

- **Programação declarativa:**
  O foco está na declaração de conhecimento, e não na sequência de instruções.

### Alguns exemplos de linguagens e usos do paradigma lógico são:
- **Prolog** (Programming in Logic): é a linguagem mais conhecida desse paradigma.
- **Sistemas de IA** (chatbots inteligentes, assistentes virtuais)
- **Processamento de Linguagem Natural** (análise sintática de textos)
- **Engines de Regras** (sistemas de recomendação baseados em lógica)

Embora o JavaScript não suporte diretamente o paradigma lógico, existem bibliotecas que imitam esse comportamento, como json-logic-js para criação de regras declarativas. Se tiver interesse em explorar mais a fundo esse paradigma, pesquise sobre Prolog e Datalog.

# Qual paradigma usar?
Para concluir nosso estudo, podemos nos perguntar: qual paradigma usar? A resposta depende muito do problema que queremos resolver. Não existe um paradigma melhor ou pior de forma absoluta, cada um possui vantagens e desvantagens, e podem se adaptar melhor ou pior, dependendo do contexto e do problema a ser resolvido.

## Paradigmas Imperativos (Ex.: Programação Procedural, OOP):
Útil quando precisamos de controle explícito sobre o fluxo de execução, e modificações diretas no estado do programa.

### Casos de uso comuns:
- Backend tradicional (Node.js + Express, ou Php + Laravel), onde controlamos o fluxo das requisições e respostas.

- Estruturas baseadas em classes e objetos, como no uso de ORMs para manipulação de bancos de dados.

## Paradigmas Declarativos:
Útil quando queremos um código mais previsível e modular, focando no resultado e não no passo a passo em específico.

### Casos de uso comuns:
- Frontend com componentes funcionais e estado imutável (React, Vue).
- Manipulação de dados com map, filter, reduce, etc.
- Queries em banco de dados SQL, onde descrevemos o que queremos consultar, sem definir como buscar/manipular os dados.

## Paradigmas Reativos:
Útil quando o software precisa responder dinamicamente a eventos, mudanças de estado, e operações assíncronas.

### Casos de uso comuns:
- Interfaces interativas na web.
- Aplicações que usam WebSockets (ex.: chats, ações/notificações em tempo real).
- Sistemas de IoT (dispositivos que reagem a eventos captados).

## Conclusão:
A escolha de qual paradigma utilizar depende do problema que será solucionado, entretanto, lembre-se que muitos sistemas modernos combinam diferentes paradigmas ao mesmo tempo, para aproveitar o melhor de cada abordagem.

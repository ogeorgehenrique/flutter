# O que é o Dart?

Dart é uma linguagem de programação moderna, criada pelo Google em 2011, com o objetivo de ser uma opção ao TypeScript para desenvolvimento
Web.
Começou a ser mais difundida com o advento do Flutter que trouxe o Dart como linguagem para seu SDK. 

Ela foi projetada para ser:
1. Simples de aprender
2. Rápida (pode compilar para código nativo ou JavaScript)
3. Orientada a objetos
4. Segura (com tipagem estática)
5. Otimizada para interfaces de usuário (UIs) responsivas e reativas

**É a linguagem oficial para criar apps Flutter.**

# Breve História do Dart

| Ano     | Evento                                                                                          |
|---------|-------------------------------------------------------------------------------------------------|
| 2011    | Google lança o Dart como alternativa ao JavaScript                                              |
| 2013    | Dart começa a ser usado em projetos web                                                         |
| 2017    | Google lança o Flutter (beta) com Dart                                                          |
| 2021+   | Dart entra no TOP 20 do ranking TIOBE                                                           |
| Hoje    | Dart é usada em milhares de apps, inclusive produtos do próprio Google (GPay, Ads, Nest, etc.) |


---

# Por que o Dart é ótimo para o Flutter?
	•	Compila para código nativo (performance real de app)
	•	Hot reload por causa do JIT
	•	Código compacto e legível
	•	Ótimo suporte para UI declarativa (base do Flutter)


📘 Resumo da Filosofia do Dart
| Característica      | Dart                                     |
|---------------------|------------------------------------------|
| Paradigma           | Orientado a Objetos + Funcional          |
| Tipagem             | Estática com inferência                  |
| Segurança de null   | Sim (null safety)                        |
| Assíncrono          | Sim, com Future, Stream                  |
| Suporte a UI        | Excelente (via Flutter)                  |
| Compilação          | JIT (dev) e AOT (produção)               |


# Fundamentos da Linguagem Dart

Vamos agora montar o alicerce que sustenta qualquer app Flutter:


# Tipos de Dados

Dart é uma linguagem orientada a objetos, e todos os tipos são objetos, inclusive números, booleanos e strings. Alem disso, o Dart é tipada (como Java/C#), mas pode ser inferida (como Python/JS).

```
TIPOS DE DADOS
int idade = 25;
double altura = 1.70;
bool lindo = true;
String nome = "George";
var cidade = "Cuiabá"; // inferência automática
```

# 1. Hierarquia de Tipos em Dart

```
Object
 ├─ Null
 ├─ num
 │   ├─ int
 │   └─ double
 ├─ bool
 ├─ String
 ├─ List, Set, Map (coleções)
 └─ dynamic
```
# 2. Tipo Object (supertipo universal)

Tudo em Dart herda ou implementa Object.
```
Object x = 42;  // pode ser int, String, bool, qualquer objeto
```
Métodos definidos em Object:
- toString()
- hashCode
- == (igualdade)
- runtimeType

Prática:
 ```
void main() {
  Object dado = "George";
  print(dado.toString()); // String
  print(dado.runtimeType); 
}
```
# 3. Tipo dynamic (sem verificação estática)

dynamic ignora a verificação de tipo em tempo de compilação.

```
dynamic x = 10;
x = "texto";
x = true;
```

contudo, **usar esse tipo é perigoso se mal utilizado**, pois os erros só aparecem em tempo de execução.

Útil para JSONs não tipados e APIs onde os tipos são incertos.

# 4. Tipo Null (representa ausência de valor)

```
String? nome = null; // o "?" torna o tipo anulável
```

Desde o Dart 2.12, o sistema de `Null Safety` obriga você a tratar variáveis que podem ou não ter valor.

Exemplo de erro evitado:
```
String? nome;
print(nome.length); // Erro! Pode ser null.
```
Correção:
```
if (nome != null) {
  print(nome.length);
}
```
# 5. Números: int, double, num

##  int
Representa números inteiros (positivos ou negativos), armazena com precisão total até 64 bits.

Exemplo de uso:
```
int numero1 = -3;
int numero2 = 0;
int numero3 = 99;
```

## Métodos comuns do tipo INTEIRO:

- .isEven

Realiza o teste se e somente se esse inteiro for PAR, caso seja é retornado um True
```
int numero1 = 10;
int numero2 = 11;

print("Retorna verdadeiro se e somente se esse inteiro for par");
print(numero1.isEven); //True
print(numero2.isEven); //False
```

- .isOdd

Realiza o teste se e somente se esse inteiro for IMPAR, caso seja é retornado um True
```
int numero1 = 10;
int numero2 = 11;

print("Retorna verdadeiro se e somente se este inteiro for ímpar");
print(numero1.isOdd); //False
print(numero2.isOdd); //True
```

- .isFinite

Realiza o teste se o número é **finito**, caso seja é retornado um True

```
int numero1 = 10;
print("Retorna se o número é finito");
print(numero1.isFinite);
```

- .infinity

Realiza o teste se o número é **ifinito**, caso seja é retornado um True
```
print("Retorna se o número é infinito");
print(double.infinity);
```

- .isNaN

Testa se o número é valido caso seja retorna um True
```
int numero1 = 10;
print("Retorna True caso o número seja válido");
print(numero1.isNaN);
```

- .isNegative

Testa se o numero é negativo, caso seja retorna um True
```
int numero1 = 10;
print("Retorna True caso o número seja negativo");
print(numero1.isNaN);
```

- .parse e .tryParse

Realiza a conversão de uma String para um Inteiro

```
print("Converte String para inteiro");
print(int.parse("10"));
```
Contudo, caso não seja possivél transformar em inteiro ele acusará um erro:
` print(int.parse("teste"));`, nesse caso use o 'tryParse', pois ele tenta converter a String em Inteiro caso ñ seja possivel ele retorna um NULL

```
print(int.tryParse("teste")); //null
```

## double
Ponto flutuante de precisão dupla (IEEE 754).

Exemplo de uso:
```
int numero1 = -3.14;
int numero2 = 0;
int numero3 = 0.1;
```

## Métodos comuns do tipo DOUBLE:

POSSUI OS MESMOS METODOS DO INTEIRO 

## num

**Supertipo de int e double**, aceita ambos, útil para variáveis que podem ser qualquer número.

Exemplo de uso:
```
num a = 10;   // int
a = 3.14;     // double
```

# 6. Booleanos: bool

Em Dart, o tipo booleano, representado pela palavra-chave `bool`, possui dois valores possíveis: `true (verdadeiro)` e `false (falso)`. Ele é usado para representar valores lógicos em expressões condicionais e operações lógicas. 

```
bool ativo = true;
bool vazio = false;
```

Somente true ou false são válidos.
**0 ou null não são considerados falsos, como em JavaScript ou C.**


# 7. Texto: String

Em Dart, uma `String` é uma sequência de caracteres UTF-16 imutável (não pode ser modificada após a criação). Ou seja, sempre que você altera uma string, na verdade você está criando uma nova string na memória.

Dart é otimizado para lidar com strings de forma eficiente, inclusive para aplicações gráficas (como no Flutter).

Formas de declarar strings:

## - Aspas simples ou duplas

Ambas são equivalentes:

```
String nome = 'George';
String cidade = "Cuiabá";
```
## - Strings multilinha ou Dicionário

Usa-se três aspas:
```
String bio = '''
Sou desenvolvedor Flutter,
apaixonado por tecnologia
e café!
''';
```

## - Interpolação de Strings

Você pode inserir variáveis ou expressões diretamente na string com $:

```
String nome = 'George';
int idade = 25;

String mensagem = 'Olá, meu nome é $nome e tenho $idade anos.';
String calc = '5 + 3 = ${5 + 3}';
```
Se for uma expressão ou método, use ${}.

## Métodos comuns do tipo STRING:

- .length

Obtem o tamanho da String e o retorna como um número de caracteres
```
nome = "george"
print(texto2.length); //6
```

- .isEmpty

Confere se a String está vazia

```
nome = "george"
print(nome.isEmpty); //false
print("".isEmpty); //true
print(" ".isEmpty); //true
```

- .toUpperCase()

Transforma toda a String em maiúsculas
```
nome = "george"
nome.toUpperCase() //GEORGE
```

- .toLowerCase()

Transforma em minúsculas
```
nome = "george"
nome.toLowerCase() //george
```


- .contains()

Verifica se contém um trecho de uma String dentro de outra

```
nome = "george"
print(nome.contains("ge")); //true
```

- .replaceAll()

Substitui todos os trechos de uma String em outra

```
nome = "george"
nome.replaceAll('e', '3') //g3org3
```

- .substring(startIndex, endIndex)

Recorta parte da String, sendo a posição 0 o inicio de qualquer String, o método `.substring` pode receber dois parametros (startIndex, endIndex), o primeiro indicando onde iniciar a coleta da String e o segundo indicando quantos carateres deve ser lidos, caso haja apenas um paremetro o método retorna toda a String iniciando pela posição informada.

```
nome = "george"
nome.substring(3) //rge
nome.substring(0, 3) //geo
```

- .split()

Quebra uma String por um caracter especifico passado como parametro

```
print("NOME;ENDERECO;CEP".split(";"));
```

- .trim(), .trimLeft, .trimRight

Remove espaços das pontas, ou da esquerda ou da direita

```
print(" george ".trim());
print(" george ".trimLeft());
print(" george ".trimRight());
```

# String imutável e segurança!

Por ser imutável, String é segura para ser usada como chave de Map, em manipulações concorrentes, e mais resistente a bugs relacionados a mutabilidade de estado.

# 8. Coleções: List, Set, Map

As coleções são fundamentais na programação em Dart (e em Flutter), pois ajudam a armazenar, organizar e manipular dados em grupo.

Dart oferece três coleções principais:
- List → Lista ordenada de elementos.
- Set → Conjunto de elementos únicos.
- Map → Conjunto de pares chave/valor.

## 1. List: Lista Ordenada de Elementos

Em Dart, uma lista é uma estrutura de dados que armazena uma coleção ordenada de itens. É como um array em outras linguagens, mas com algumas diferenças e recursos adicionais. As listas em Dart podem armazenar itens de diferentes tipos e podem ser manipuladas usando vários métodos e operadores. 

Uma lista pode:
- Armazena elementos em ordem.
- Permite duplicatas.
- Pode ser mutável ou imutável.

Como criar uma lista em Dart:

1. Listas literais:
Usando colchetes [  ] para envolver os elementos da lista, separados por vírgulas.

Exemplo:
```
List<int> numeros = [1, 2, 3, 4, 5];

List<String> frutas = ['Maçã', 'Banana', 'Laranja'];

// Lista com tipo dinâmico (não recomendado em produção)
var numeros = [1, 2, 3, 4];
```

2. Usando o construtor List():

```
Exemplo: List<String> frutas = List();
```


## Métodos comuns do tipo LIST:

- .add(element)

Adiciona um elemento ao final da lista.

```
frutas.add('Uva');
```

- .insertelement)

Adiciona um elemento na lista na posição informada no parametro

```
frutas.insert(1, 'Manga');   // Adiciona na posição 1
```

- .remove(element)

Remove a primeira ocorrência do elemento da lista.

```
frutas.remove('Banana');     // Remove por valor
```

- .removeAt(index):

Remove o elemento no índice especificado passado por parametro.

```
frutas.removeAt(0);          // Remove por índice
```

- .contains(element)

Verifica se a lista contém o elemento especificado, caso haja ele retorna true

```
frutas.contains('Uva');      // true
```

- .length

Retorna o número de elementos na lista.

```
frutas.length;               // Tamanho da lista
```

- Acesso direto aos elementos da lista.

```
frutas[0];                   // Acessa o primeiro elemento
```

- .isEmpty e .isNotEmpty

Verifica se a lista está vazia ou não.

```
print(frutas.isEmpty); //false
print(lstInt.isNotEmpty); //true
```

- .indexOf(element):

Retorna o índice da primeira ocorrência do elemento.

```
frutas.indexOf("banana");
```

- .sort()

Ordena a lista. Para listas de objetos, é necessário fornecer uma função de comparação.

- .shuffle()

Embaralha os elementos da lista.


- .sublist(startIndex, endIndex)

Cria uma nova lista com uma parte da lista original.


- .clear()

Remove todos os elementos da lista. 


# 2. Set: Conjunto Não Ordenado de Valores Únicos

Em Dart, um `Set` é um tipo de coleção que armazena um conjunto não ordenado de valores únicos. Isso significa que cada elemento em um `Set` **deve ser diferente dos demais**, e a ordem em que os elementos são adicionados ou iterados não é garantida. 

Características principais:

- Não ordenado:
A ordem dos elementos em um `Set` não é significativa. Quando você itera sobre um `Set`, a ordem dos elementos pode variar entre diferentes execuções ou em diferentes implementações.

- Valores únicos:
Um `Set` não permite elementos duplicados. Se você tentar adicionar um valor que já existe no `Set`, a operação será ignorada.

- Uso comum:
Sets são úteis quando você precisa garantir que uma coleção contenha apenas valores distintos e não se importa com a ordem. 

Exemplo de uso: 

```
void main() {
  Set<String> meuSet = {'apple', 'banana', 'cherry'};
  print(meuSet); // Saída: {apple, banana, cherry} (a ordem pode variar)

  meuSet.add('apple'); // Tentar adicionar 'apple' novamente (duplicado) Ñ SERÁ ADD
  print(meuSet); // Saída: {apple, banana, cherry} (continua com os mesmos elementos)

  meuSet.add('date');
  print(meuSet); // Saída: {apple, banana, cherry, date} (novo elemento adicionado)
}
```

## Métodos comuns do tipo SET:

Possui os mesmos metodos de LIST

# 3. Map: Estrutura Chave → Valor

Em Dart, um Map é uma estrutura de dados que armazena pares chave-valor. Cada chave no mapa é única e usada para acessar o valor associado a ela. 

Estrutura:
Um mapa em Dart é declarado usando a sintaxe `Map<Chave, Valor>`, onde Chave e Valor são os tipos de dados das chaves e valores, respectivamente.

Por exemplo: 
```
Map<String, int> frutas = {
  'banana': 3,
  'maçã': 5,
  'laranja': 2,
};
```
Neste exemplo, frutas é um mapa onde as chaves são strings (nomes das frutas) e os valores são inteiros (quantidades). 

As chaves devem ser únicas, valores podem se repetir. O map é muito útil para representar objetos com propriedades.

## Métodos comuns do tipo MAP:

- Acessar um valor

Use a chave entre colchetes para obter o valor correspondente

```
int quantidadeBanana = frutas['banana']; // quantidadeBanana terá o valor 3
```

- Adiciona um par chave-valor dentro de um Map

```
frutas['morango'] = 7;
```

- Remove um par chave-valor dentro de um Map

```
frutas.remove('maçã');
```

- Verifica se uma chave existe dentro de um Map

```
bool temLaranja;
temLaranja = frutas.containsKey('laranja'); // temLaranja será true
```
- .length

Retorna o número de pares chave-valor no mapa.

```
print(frutas.length);
```

- .isEmpty e .isNotEmpty

Verifica se o map mapa estiver vazio retornando true caso seja verdade, ja isNotEmpty faz o a verificação se o mapa NÃO está vazio.

```
print(frutas.isNotEmpty);
print(frutas.isEmpty);
```

- .keys

Retorna um Iterable com todas as chaves do mapa.


- .values

Retorna um Iterable com todos os valores do mapa.


- clear()

Remove todos os pares chave-valor do mapa.


 # 9. Const vs Final vs Var

Em Dart, `const`, `final` e `var` são usados para declarar variáveis, mas com diferenças importantes. `const` é usado para constantes de tempo de compilação, cujos valores devem ser **conhecidos no momento da compilação e nunca mudam**. 

`final` é usado para **variáveis que são atribuídas apenas uma vez**, seja no momento da declaração ou em tempo de execução, mas depois disso, seu valor não pode ser alterado. 

`var` é usado quando o tipo da variável não é conhecido ou é inferido pelo compilador, permitindo que a variável seja reatribuída com valores de tipos diferentes. 

## `const` (Constante de Tempo de Compilação):

1. Define uma variável cujo valor é conhecido e imutável durante a compilação.
2. Usado para valores que são constantes em tempo de execução e não podem mudar.
3. Ideal para valores que são conhecidos antes mesmo da execução do programa. 

Exemplo: `const pi = 3.14159;`

## `final` (Variável de Atribuição Única):

1. Define uma variável cujo valor é atribuído apenas uma vez, seja em tempo de compilação ou execução.
2. Depois de atribuído, o valor não pode ser alterado, mas o objeto referenciado pode ser mutável.
3. Útil para variáveis que podem ter valores diferentes em diferentes execuções, mas não devem ser alteradas dentro da mesma execução.

Exemplo: `final name = "João";` ou `final List<int> numbers = [1, 2, 3];` 

## `var` (Variável Genérica):

1. Declara uma variável cujo tipo é inferido pelo compilador ou explicitamente declarado.
2. Permite que a variável seja reatribuída com valores de tipos diferentes.
3. Útil quando o tipo da variável não é conhecido ou é indiferente.

Exemplo: `var message = "Olá";` ou `var number = 10;` 

## Diferenças entre as Chaves:

- Tempo de Avaliação:

`const` é avaliado em tempo de compilação, enquanto `final` é avaliado em tempo de execução (na primeira atribuição).

- Imutabilidade:

`const` garante imutabilidade tanto do valor quanto do objeto, enquanto `final` garante apenas que o valor não seja alterado após a atribuição, mas o objeto pode ser mutável.

- Reatribuição:
`var` permite reatribuição, enquanto `const` e `final` não permitem.

- Uso:

Use `const` para constantes que são conhecidas no momento da compilação e `final` para variáveis que são atribuídas uma vez em tempo de execução. 

----

# 10. Estruturas Condicionais e de Repetição

Em Dart, estruturas condicionais e de repetição são usadas para controlar o fluxo de execução do código. As estruturas condicionais (`if`, `else`, `switch`) permitem que o programa execute diferentes blocos de código com base em condições. 

As estruturas de repetição (`for`, `while`, `do-while`) executam um bloco de código várias vezes, seja com um número definido de iterações ou enquanto uma condição for verdadeira. 

# Estruturas Condicionais:

## if

Executa um bloco de código se a condição for verdadeira. 

Sintaxe:
```
if (condição) {
  // código executado se for verdadeiro
```

## else

Executa um bloco de código se a condição do if for falsa. 

Sintaxe:
```
if (condição) {
  // código executado se for verdadeiro
} else {
  // executado se nenhuma das anteriores for verdadeira
}
```

## else if

Permite verificar várias condições consecutivas. Se a condição anterior for falsa, a próxima condição é avaliada. 

Sintaxe:
```
if (condição) {
  // código executado se for verdadeiro
} else if (outraCondição) {
  // executado se a outraCondição for verdadeira
} else {
  // executado se nenhuma das anteriores for verdadeira
}
```

## if com operador ternário (condição em uma linha)

Em Dart, o operador ternário é uma forma concisa de escrever expressões condicionais, similar ao uso de if/else. Ele permite escolher entre dois valores com base em uma condição booleana.

 Sintaxe:
```
condição ? valorSeVerdadeiro : valorSeFalso;
```

Exemplo:
```
void main() {
  int idade = 20;
  String mensagem = idade >= 18 ? "Maior de idade" : "Menor de idade";
  print(mensagem); // Saída: Maior de idade
}
```
**Explicação:**
1. `condição`: Uma expressão booleana que é avaliada. No exemplo, `idade >= 18` é a condição.
2. `?`: Se a condição for verdadeira, o valor após o `?` é retornado.
3. `valorSeVerdadeiro`: O valor a ser retornado se a condição for verdadeira. No exemplo, "Maior de idade".
4. `::` Se a condição for falsa, o valor após o `:` é retornado.
5. `valorSeFalso`: O valor a ser retornado se a condição for falsa. No exemplo, "Menor de idade". 

O operador ternário é útil para simplificar o código quando você precisa escolher entre duas opções com base em uma condição simples. Ele é frequentemente usado em expressões mais curtas e limpas, especialmente em situações onde você precisa atribuir um valor a uma variável com base em uma condição, como no exemplo acima. 


## switch

Em Dart, a estrutura switch com case é usada para executar diferentes blocos de código com base no valor de uma expressão. É uma alternativa mais elegante e legível para várias estruturas if-else aninhadas, especialmente quando se lida com múltiplas opções baseadas em um valor. 

Sintaxe:
```
Código

switch (expressao) {
  case valor1:
    // Código a ser executado se expressao == valor1
    break;
  case valor2:
    // Código a ser executado se expressao == valor2
    break;
  default:
    // Código a ser executado se nenhum dos casos corresponder
}
```
Explicação:
1. `switch (expressao)`: A palavra-chave switch seguida pela expressão a ser avaliada.
2. `case valor1:`: Cada case verifica se a expressão corresponde a um valor específico.
3. `break;`: O break é crucial para sair do bloco switch após a execução do caso correspondente. Sem o break, a execução "cai" para o próximo case.
4. `default:`: O bloco default é opcional e executado se nenhum dos casos corresponder à expressão.
5. Os tipos de dados da expressão e dos valores dos cases devem ser compatíveis.
6. As cláusulas case devem ser constantes ou expressões constantes. 

Exemplo:
```
void main() {
  int diaDaSemana = 3;

  switch (diaDaSemana) {
    case 1:
      print("Domingo");
      break;
    case 2:
      print("Segunda-feira");
      break;
    case 3:
      print("Terça-feira");
      break;
    case 4:
      print("Quarta-feira");
      break;
    case 5:
      print("Quinta-feira");
      break;
    case 6:
      print("Sexta-feira");
      break;
    case 7:
      print("Sábado");
      break;
    default:
      print("Dia inválido");
  }
}
```
O Dart 3 introduziu o recurso de expressões de switch, que oferecem uma forma mais concisa e funcional de lidar com casos. 

## Switch Expressions (Dart 3):
As expressões de switch permitem retornar um valor diretamente do switch, tornando o código mais compacto e legível. 

```
String getDiaDaSemana(int dia) {
  return switch (dia) {
    1 => "Domingo",
    2 => "Segunda-feira",
    3 => "Terça-feira",
    4 => "Quarta-feira",
    5 => "Quinta-feira",
    6 => "Sexta-feira",
    7 => "Sábado",
    _ => "Dia inválido",
  };
}
```


Neste exemplo, a função `getDiaDaSemana` retorna o nome do dia correspondente ao número fornecido, utilizando a expressão de switch. O `_` substitui o default na sintaxe anterior. 


# Estruturas de Repetição:

## for
  
Em Dart, a estrutura de repetição for é usada para executar um bloco de código repetidamente, com base em uma condição. Ela é particularmente útil quando se sabe quantas vezes o loop precisa ser executado. 
Estrutura básica do for:

```
for (inicialização; condição; incremento/decremento) {
  // Bloco de código a ser executado repetidamente
}
```

Exemplo:
```
void main() {
  for (int i = 1; i <= 5; i++) {
    print(i);
  }
}
```

Explicação:
1. `int i = 1;`: Inicializa a variável de controle i com o valor 1.
2. `i <= 5;`: Define a condição para que o loop continue. O loop irá rodar enquanto i for menor ou igual a 5.
3. `i++`: Incrementa o valor de i em 1 a cada iteração.
4. `print(i);`: O bloco de código dentro do loop, que imprime o valor atual de i em cada iteração.


## for in

Em Dart, o `for...in` é uma estrutura de iteração usada para percorrer elementos em coleções, como listas ou conjuntos. Ele simplifica a iteração, permitindo que você acesse cada elemento diretamente, sem a necessidade de gerenciar índices ou contadores. 

Sintaxe:

```
for (var item in collection) {
  // Código a ser executado para cada 'item' na 'collection'
}
```

Exemplo:
```
void main() {
  var frutas = ['maçã', 'banana', 'laranja'];

  for (var fruta in frutas) {
    print(fruta);
  }
}
```
Saída:
```
maçã
banana
laranja
```

**Explicação:**
1. `for (var fruta in frutas)`: Este laço "for...in" itera sobre a lista frutas.
2. `var fruta`: Em cada iteração, o valor atual da lista é atribuído à variável fruta.
3. `print(fruta)`: Imprime o valor atual da variável fruta em cada iteração, mostrando cada fruta da lista.

## Outras coleções:

O "for...in" também pode ser usado com outros tipos de coleções em Dart, como:
1. Sets: Para iterar sobre elementos únicos em um conjunto.
2. Maps: Para iterar sobre as chaves de um mapa, ou sobre pares chave-valor (com chaves e valores separados).

Exemplo com mapa:

```
void main() {
  var mapa = {'nome': 'João', 'idade': 30, 'cidade': 'São Paulo'};

  for (var chave in mapa.keys) {
    print('Chave: $chave, Valor: ${mapa[chave]}');
  }
}
```
Saída:
```
Chave: nome, Valor: João
Chave: idade, Valor: 30
Chave: cidade, Valor: São Paulo
```


## Vantagens do "for...in":

- Legibilidade: Torna o código mais limpo e fácil de entender, especialmente quando se trabalha com coleções.
- Concisão: Elimina a necessidade de criar e gerenciar contadores, tornando o código mais curto.
- Segurança: Evita erros comuns de índice que podem ocorrer com loops for tradicionais.


## while 

Em Dart, a estrutura `while` é usada para criar um loop que executa um bloco de código repetidamente enquanto uma condição booleana for verdadeira. A condição é verificada antes de cada iteração do loop. Se a condição for falsa, o loop não será executado nenhuma vez. O `while` é uma estrutura fundamental para controlar o fluxo de execução em programas Dart, permitindo a repetição de tarefas com base em critérios específicos. 

Sintaxe:

```
while (condicao) {
  // Código a ser executado enquanto a condição for verdadeira
}
```

**Funcionamento:**
1. Avaliação da Condição:
Antes de cada iteração do loop, a expressão condicao é avaliada.
2. Execução do Bloco: Se a condição for verdadeira, o bloco de código dentro do while é executado.
3. Repetição: O processo de avaliação da condição e execução do bloco se repete enquanto a condição permanecer verdadeira.
4. Saída do Loop: Quando a condição se torna falsa, o loop é interrompido, e o programa continua a execução após o bloco `while`. 

Exemplo:

```
void main() {
  int numero = 1;
  while (numero <= 5) {
    print(numero);
    numero++; // Incrementa o valor de 'numero' para evitar um loop infinito
  }
}
```

Neste exemplo: 
1. A variável numero é inicializada com o valor 1.
2. O loop while continua enquanto numero for menor ou igual a 5.
3. Dentro do loop, o valor atual de numero é impresso e, em seguida, numero é incrementado.
4. O resultado será a impressão dos números de 1 a 5, cada um em uma linha separada.

**Importante:**
É crucial garantir que a condição do while eventualmente se torne falsa para evitar loops infinitos.

A estrutura break pode ser usada para sair do loop while prematuramente, mesmo que a condição ainda seja verdadeira, como descreve um tutorial do Dart. 

Em situações onde é necessário garantir que o bloco de código seja executado pelo menos uma vez, a estrutura do-while pode ser mais adequada. 

## do-while

Em Dart, a estrutura `do-while` executa um bloco de código pelo menos uma vez e depois repete a execução enquanto uma determinada condição for verdadeira. A diferença chave em relação ao loop `while` é que a condição é avaliada após a execução do bloco de código, garantindo que o bloco seja sempre executado pelo menos uma vez. 

Sintaxe:

```
do {
  // Bloco de código a ser repetido
} while (condicao);
```

**Funcionamento:**

1. Execução inicial: O bloco de código dentro do `do` é executado pela primeira vez, independentemente da condição.
2. Avaliação da condição: Após a execução do bloco, a condicao é avaliada. Se a condição for verdadeira, o bloco de código é executado novamente.
3. Repetição: O processo de execução do bloco e avaliação da condição continua até que a condicao se torne falsa.
4. Finalização: Quando a condicao é falsa, o loop `do-while` é interrompido, e a execução do programa continua na próxima linha após o loop. 

Exemplo:

```
void main() {
  int i = 1;
  do {
    print(i);
    i++;
  } while (i <= 5);
}
```


1. Neste exemplo, o código dentro do `do` (que imprime o valor de i e o incrementa) será executado pelo menos uma vez.
2. Na primeira execução, i é 1, então "1" será impresso. Em seguida, i é incrementado para 2.
3. A condição `i <= 5` é então avaliada como verdadeira, então o loop continua. Este processo se repete até que i se torne 6, momento em que a condição se torna falsa e o loop é interrompido.

## Diferença entre while e do-while:
- `while`: A condição é avaliada antes da execução do bloco de código. Se a condição for falsa inicialmente, o bloco nunca será executado.
  
- `do-while`: A condição é avaliada após a execução do bloco de código. O bloco será executado pelo menos uma vez, mesmo que a condição seja falsa inicialmente. 

---

# 11. Funções em Dart

Em Dart, funções são objetos de primeira classe, o que significa que podem ser passadas como argumentos para outras funções, retornadas de outras funções e atribuídas a variáveis. Funções em Dart podem ser nomeadas ou anônimas ( funções lambda ) e podem ter zero ou mais parâmetros. Elas podem retornar valores ou não (funções com tipo de retorno void). 

Estrutura básica de uma função em Dart:

```
tipo_de_retorno nome_da_funcao(parametros) {
  // Corpo da função (código a ser executado)
  // ...
  return valor_de_retorno; // Opcional, dependendo do tipo_de_retorno
}
```

Exemplos:
Função sem parâmetros e sem retorno. 
```
void imprimirMensagem() {
  print('Olá, mundo!');
}
```
Função com parâmetros e com retorno. 

```
int somar(int a, int b) {
  return a + b;
}
```

Função com parâmetros opcionais. 

```
String saudar(String nome, {String? titulo}) {
  if (titulo != null) {
    return 'Olá, $titulo $nome!';
  } else {
    return 'Olá, $nome!';
  }
}
```

Função anônima (lambda). 

```
var dobrar = (int numero) => numero * 2;
```
Função que recebe uma função como paremtro:

```
int executar( int numero, Funcion funf){
	return func(numero);
}
```

**Principais características das funções em Dart:**
1. Objetos de primeira classe: Funções podem ser tratadas como qualquer outro tipo de dado.
2. Tipagem estática: Dart é uma linguagem com tipagem estática, o que significa que o tipo de retorno e os tipos de parâmetros devem ser especificados.
3. Parâmetros opcionais: Dart permite definir parâmetros opcionais nomeados e posionais, facilitando a criação de funções mais flexíveis.
4. Funções assíncronas: Dart suporta funções assíncronas, que podem retornar um valor no futuro, permitindo a execução de operações de longa duração sem bloquear a thread principal.
5. Funções com efeitos colaterais: Funções podem ter efeitos colaterais, como modificar o estado de variáveis globais ou realizar operações de entrada/saída.
6. Escopo: Variáveis definidas dentro de uma função são locais e só podem ser acessadas dentro dela. Variáveis globais são acessíveis em qualquer lugar do código, mas seu uso excessivo pode levar a problemas de manutenção. 

Exemplo completo:

```
void main() {
  imprimirMensagem();
  int resultado = somar(5, 3);
  print('A soma é: $resultado');
  String saudacao = saudar('João', titulo: 'Sr.');
  print(saudacao);
  int resultadoDobro = dobrar(4);
  print('O dobro de 4 é: $resultadoDobro');
}

void imprimirMensagem() {
  print('Olá, mundo!');
}

int somar(int a, int b) {
  return a + b;
}

String saudar(String nome, {String? titulo}) {
  if (titulo != null) {
    return 'Olá, $titulo $nome!';
  } else {
    return 'Olá, $nome!';
  }
}

var dobrar = (int numero) => numero * 2;
```


# 12. ENTRADA E SAIDA DE DADOS

falta

# 13. Orientação a Objetos

A Orientação a Objetos (OO) em Dart é um paradigma de programação que permite organizar o código em torno de objetos, que são instâncias de classes. As classes definem os atributos (dados) e métodos (ações) que os objetos terão. Em Dart, a OO facilita a reutilização de código, a organização e a manutenção de projetos. 

## Conceitos Fundamentais:

- Classes: Modelos ou blueprints para criar objetos. Definem as características (atributos) e comportamentos (métodos) comuns a um grupo de objetos. 

- Objetos: Instâncias de classes. Cada objeto possui seus próprios valores para os atributos definidos na classe. 

- Atributos: Variáveis que armazenam os dados de um objeto. 

- Métodos: Funções que definem o comportamento de um objeto. 

- Encapsulamento: Ocultação dos detalhes internos de um objeto, expondo apenas uma interface para interação.

- Herança: Mecanismo que permite que uma classe (subclasse) herde características e comportamentos de outra classe (superclasse), reutilizando código e estabelecendo relações entre classes.

-  Polimorfismo: Capacidade de objetos de diferentes classes serem tratados de forma semelhante, através de uma interface comum. 

**Benefícios da OO em Dart:**

1. Reutilização de código: Através da herança e composição, evita-se a duplicação de código.
2. Organização: O código fica mais estruturado e fácil de entender, com classes e objetos representando elementos do mundo real.
3. Manutenibilidade: Modificações em uma classe não afetam outras classes, facilitando a manutenção e evolução do projeto.
4. Legibilidade: O código se torna mais claro e intuitivo.
5. Modularidade: Permite dividir o código em módulos independentes, facilitando o desenvolvimento e a colaboração. 

# 14. Classes

Em Dart, classes são modelos para a criação de objetos, encapsulando dados (variáveis de instância) e comportamentos (métodos). Uma classe define a estrutura e o comportamento de um objeto, enquanto um objeto é uma instância específica dessa classe. 

## Conceitos:
- Classe: Define um conjunto de propriedades (variáveis de instância) e métodos que um objeto terá.
- Objeto: Uma instância específica de uma classe.
- Variáveis de instância: Representam os dados de um objeto.
- Métodos: Representam as funções ou ações que um objeto pode realizar.
- Construtor: Um método especial usado para criar e inicializar objetos de uma classe.

**Como definir uma classe em Dart:**
1. Palavra-chave `class`: Use a palavra-chave class seguida do nome da classe (em maiúsculas, por convenção).
2. Chaves `{}`: Delimite o corpo da classe com chaves, onde você definirá as propriedades e métodos. 

Exemplo:

```
class Carro {
  String cor;
  String modelo;

  Carro(this.cor, this.modelo); // Construtor

  void dirigir() {
    print('O carro $cor está dirigindo!');
  }
}
```

**Explicando o exemplo:**
- Carro é o nome da classe.
- cor e modelo são propriedades (variáveis de instância) da classe.
- dirigir() é um método que define um comportamento da classe. 

## Instanciando um objeto:

Para criar um objeto (instância) da classe, use o operador new (opcional em Dart) seguido do nome da classe e parênteses: 

```
var meuCarro = new Carro(); // Cria uma instância da classe Carro
```

## Acessando propriedades e métodos:

```
meuCarro.cor = 'vermelho';
meuCarro.modelo = 'Fusca';
meuCarro.dirigir(); // Chama o método dirigir
```

# Encapsulamento

Em Dart, encapsulamento é o princípio de OOP que permite agrupar dados e métodos que operam sobre esses dados em uma única unidade, protegendo a implementação interna de um objeto e expondo apenas uma interface controlada para interação externa. Isso é feito principalmente através do uso de modificadores de acesso (público e privado) e, em muitos casos, de getters e setters. 

## Como funciona o encapsulamento em Dart:

**Modificadores de Acesso:**
- Público: Variáveis e métodos com modificador público (não há modificador explícito, por padrão são públicos) são acessíveis de qualquer lugar no código.
- Privado: Variáveis e métodos com modificador privado `(prefixados com um sublinhado _)` são acessíveis apenas dentro da própria biblioteca onde são definidos.

Exemplo:
```
class ContaBancaria {
	double _saldo; //atributo privado
	int conta; //atributo publico
...
}
```

## Getters e Setters

São métodos especiais que permitem o acesso controlado a atributos privados. O getter permite a leitura do valor, enquanto o setter permite a modificação, potencialmente com validações. 

Exemplo:

```
Exemplo:

class ContaBancaria {
  double _saldo;

  ContaBancaria(this._saldo);

  // Getter para o saldo
  double getSaldo => _saldo;

  // Setter para o saldo com validação
  void setSaldo(double novoSaldo) {
    if (novoSaldo >= 0) {
      _saldo = novoSaldo;
    } else {
      print("Erro: Saldo não pode ser negativo.");
    }
  }

  // Método para depósito
  void depositar(double valor) {
    if (valor > 0) {
      saldo = saldo + valor;
    } else {
      print("Valor de depósito inválido.");
    }
  }
}

void main() {
  var minhaConta = ContaBancaria(1000.0);
  print("Saldo inicial: ${minhaConta.saldo}"); // Acessando o saldo via getter

  minhaConta.depositar(500.0);
  print("Saldo após depósito: ${minhaConta.saldo}");

  minhaConta.saldo = -200.0; // Tentativa de definir um saldo negativo (será ignorada)
  print("Saldo após tentativa de saldo negativo: ${minhaConta.saldo}");

  //minhaConta._saldo = 500.0;  // Erro! Não é possível acessar diretamente o atributo privado
}
```
## Construtor

Em Dart, um construtor é um método especial usado para criar e inicializar objetos de uma classe. Ele é chamado automaticamente quando um novo objeto é instanciado. Construtores em Dart podem ter parâmetros e podem ser padrão, nomeados ou de fábrica. 

**Tipos de Construtores em Dart:**
- Construtor Padrão (Default Constructor): É o construtor padrão de uma classe, que é chamado quando nenhum outro construtor é explicitamente definido. 

- Construtor Nomeado: Permite definir múltiplos construtores para uma mesma classe, usando nomes diferentes para cada um, o que facilita a criação de objetos com diferentes conjuntos de parâmetros. 

- Construtor de Fábrica: Permite um controle mais flexível sobre a criação de objetos. Pode retornar uma instância existente ou de uma subclasse, em vez de criar sempre uma nova instância. 

Exemplos:

```

class Pessoa {
  String _nome;
  int _idade;

  // Construtor padrão
	Pessoa(this.nome, this.idade);

  // Construtor nomeado
	Pessoa.semNome(int idade){
		_idade = idade;
	}


  // Construtor de fábrica
  factory Pessoa.fromJson(Map<String, dynamic> json) {
    return Pessoa(json['nome'], json['idade']);
  }
}

```
**Casos de uso:**
1. Inicialização de atributos: Construtores são usados para definir os valores iniciais dos atributos de um objeto.
2. Controle de acesso: Construtores podem ser privados (usando _ antes do nome) para restringir a criação de objetos a partir de outras classes.
3. Implementação de padrões de projeto: Construtores de fábrica são úteis em padrões como Singleton, onde se deseja controlar a criação de instâncias únicas.
4. Lógica complexa de inicialização: Construtores de fábrica podem ser usados para realizar operações complexas ou acessar dados externos antes de criar o objeto. 

**Observações:**
- Construtores não possuem tipo de retorno (nem mesmo void).
- O uso de this dentro do construtor se refere ao atributo da instância da classe.
- Em Dart, construtores podem ser chamados com a palavra-chave new (opcional) ou sem ela. 



# Sobrescrita (overriding)

Em Dart, sobrescrita (overriding) de métodos ocorre quando uma classe filha fornece sua própria implementação de um método que já existe na classe pai (superclasse). Isso permite que a classe filha personalize o comportamento do método herdado, adaptando-o às suas necessidades específicas. A sobrescrita é um exemplo de polimorfismo, permitindo que objetos de classes diferentes respondam de maneiras diferentes a um mesmo método. 

**Como funciona a sobrescrita em Dart:**

1. Herança: A sobrescrita pressupõe que a classe filha herda de uma classe pai.
2. Assinatura do método: O método na classe filha deve ter a mesma assinatura do método na classe pai (mesmo nome, tipo de retorno e parâmetros).
3. `@override`: O uso da anotação `@override` antes da declaração do método na classe filha é opcional, mas altamente recomendado para indicar que você está intencionalmente sobrescrevendo um método, facilitando a detecção de erros.
4. Execução: Quando um método sobrescrito é chamado em um objeto da classe filha, a implementação da classe filha é executada, não a da classe pai. 

Exemplo:

```
class Animal {
  void fazerSom() {
    print('Som genérico de animal');
  }
}

class Cachorro extends Animal {
  @override
  void fazerSom() {
    print('Au au');
  }
}

void main() {
  Animal animal = Animal();
  animal.fazerSom(); // Saída: Som genérico de animal

  Cachorro cachorro = Cachorro();
  cachorro.fazerSom(); // Saída: Au au

  Animal animalCachorro = Cachorro();
  animalCachorro.fazerSom(); // Saída: Au au (polimorfismo)
}
```

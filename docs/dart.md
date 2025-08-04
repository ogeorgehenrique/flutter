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


# Fundamentos da Linguagem Dart

Vamos agora montar o alicerce que sustenta qualquer app Flutter:


# Tipos de Dados

Dart é uma linguagem orientada a objetos, e todos os tipos são objetos, inclusive números, booleanos e strings. Alem disso, o Dart é tipada (como Java/C#), mas pode ser inferida (como Python/JS).

```
TIPOS DE DADOS
int idade = 25;
double altura = 1.70;
bool ativo = true;
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
  print(dado.toString());
  print(dado.runtimeType); // String
}
```
# 3. Tipo dynamic (sem verificação estática)

dynamic ignora a verificação de tipo em tempo de compilação.

```
dynamic x = 10;
x = "texto";
x = true;
```

contudo, usar esse tipo é perigoso se mal utilizado: erros só aparecem em tempo de execução. Útil para JSONs não tipados e APIs onde os tipos são incertos.

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

# - int
Representa números inteiros (positivos ou negativos), armazena com precisão total até 64 bits.
Exemplo de uso:
```
int numero1 = -3;
int numero2 = 0;
int numero3 = 99;
```

# Métodos comuns do tipo INTEIRO:

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
print("Retorna se o número não é um núemro válido");
print(numero1.isNaN);
```

- .isNegative

Testa se o núemro é negativo, caso seja retorna um True
```
int numero1 = 10;
print("Retorna se o número não é um núemro válido");
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

# - double
Ponto flutuante de precisão dupla (IEEE 754).

Exemplo de uso:
```
int numero1 = -3.14;
int numero2 = 0;
int numero3 = 0.1;
```

# Métodos comuns do tipo DOUBLE:

POSSUI OS MESMOS METODOS DO INTEIRO 

- num
**Supertipo de int e double**, aceita ambos, útil para variáveis que podem ser qualquer número.

Exemplo de uso:
```
num a = 10;   // int
a = 3.14;     // double
```

# 6. Booleanos: bool

Em Dart, o tipo booleano, representado pela palavra-chave bool, possui dois valores possíveis: `true (verdadeiro)` e `false (falso)`. Ele é usado para representar valores lógicos em expressões condicionais e operações lógicas. 

```
bool ativo = true;
bool vazio = false;
```

Somente true ou false são válidos.
**0 ou null não são considerados falsos, como em JavaScript ou C.**


# 7. Texto: String

Em Dart, uma `String` é uma sequência de caracteres UTF-16 imutável (não pode ser modificada após a criação). Ou seja, sempre que você altera uma string, na verdade você está criando uma nova string na memória.

Dart é otimizado para lidar com strings de forma eficiente, inclusive para aplicações gráficas (como no Flutter).

Formas de declarar strings

# - Aspas simples ou duplas

Ambas são equivalentes:

```
String nome = 'George';
String cidade = "Cuiabá";
```
# - Strings multilinha ou Dicionário

Usa-se três aspas:
```
String bio = '''
Sou desenvolvedor Flutter,
apaixonado por tecnologia
e café!
''';
```

# - Interpolação de Strings

Você pode inserir variáveis ou expressões diretamente na string com $:

```
String nome = 'George';
int idade = 25;

String mensagem = 'Olá, meu nome é $nome e tenho $idade anos.';
String calc = '5 + 3 = ${5 + 3}';
```
Se for uma expressão ou método, use ${}.

# Métodos comuns do tipo DOUBLE:

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
print(nome.contains("ge"));


- .replaceAll()

Substitui todos os trechos de uma String em outra
```
nome = "george"
nome.replaceAll('e', '3')
```

- .substring()

Recorta parte da String, sendo a posição 0 o inicio de qualquer String, o método .substring pode receber dois parametros, o primeiro indicando onde iniciar a coleta da String e o segundo indicando quantos carateres deve ser lidos, caso haja apenas um paremetro o método retorna toda a String iniciando pela posição informada.
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










1. Sintaxe básica

```
void main() {
  print('Olá, Dart!');
}
```
- main() é o ponto de entrada.
- print() exibe algo no console.

 
3. Variáveis

```
var nome = 'George';       // tipo inferido
String curso = 'Eng. Comp';

final idade = 23;          // imutável após atribuição
const PI = 3.1415;         // constante em tempo de compilação
```

- var: variável comum
- final: só pode ser atribuído uma vez (em tempo de execução)
- const: constante de tempo de compilação

4. Funções
```
int somar(int a, int b) {
  return a + b;
}

void saudacao(String nome) {
  print("Olá, $nome!");
}
```

Funções podem ser anônimas e passadas como argumentos!

 5. Controle de Fluxo

 ```
 if (idade >= 18) {
  print("Maior de idade");
} else {
  print("Menor de idade");
}

for (int i = 0; i < 5; i++) {
  print(i);
}

while (ativo) {
  // repete enquanto 'ativo' for true
}
```

6. Coleções (List, Set, Map)
```
List<String> frutas = ['maçã', 'banana', 'uva'];
Set<int> numeros = {1, 2, 3};
Map<String, String> usuario = {
  'nome': 'George',
  'email': 'george@example.com'
};
```

List = lista (vetor, array)
	•	Set = conjunto (sem repetição)
	•	Map = dicionário/chave-valor

7. Classes e Objetos

```
class Pessoa {
  String nome;
  int idade;

  Pessoa(this.nome, this.idade);

  void apresentar() {
    print("Olá, sou $nome e tenho $idade anos.");
  }
}

void main() {
  var p = Pessoa("George", 23);
  p.apresentar();
}
```

8. Null Safety (Dart 2.12+)

Evita erros de null em tempo de execução.

```
String? nome; // Pode ser nulo
nome = null;

String nomeSeguro = "George"; // Nunca pode ser nulo
```

9. Programação Assíncrona (Future e async/await)

```
Future<String> buscarDados() async {
  await Future.delayed(Duration(seconds: 2));
  return "Dados carregados";
}

void main() async {
  String resultado = await buscarDados();
  print(resultado);
}
```

Por que o Dart é ótimo para o Flutter?
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


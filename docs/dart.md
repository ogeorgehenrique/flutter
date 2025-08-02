O que é o Dart?

Dart é uma linguagem de programação moderna, criada pelo Google em 2011.

Ela foi projetada para ser:
	•	Simples de aprender
	•	Rápida (pode compilar para código nativo ou JavaScript)
	•	Orientada a objetos
	•	Segura (com tipagem estática)
	•	Otimizada para interfaces de usuário (UIs) responsivas e reativas

É a linguagem oficial para criar apps Flutter.

⸻

🕰️ Breve História do Dart
| Ano     | Evento                                                                                          |
|---------|-------------------------------------------------------------------------------------------------|
| 2011    | Google lança o Dart como alternativa ao JavaScript                                              |
| 2013    | Dart começa a ser usado em projetos web                                                         |
| 2017    | Google lança o Flutter (beta) com Dart                                                          |
| 2021+   | Dart entra no TOP 20 do ranking TIOBE                                                           |
| Hoje    | Dart é usada em milhares de apps, inclusive produtos do próprio Google (GPay, Ads, Nest, etc.) |

Fundamentos da Linguagem Dart

Vamos agora montar o alicerce que sustenta qualquer app Flutter:

1. Sintaxe básica

```
void main() {
  print('Olá, Dart!');
}
```
- main() é o ponto de entrada.
- print() exibe algo no console.

 2. Tipos de Dados

 Dart é tipada (como Java/C#), mas pode ser inferida (como Python/JS).

```
int idade = 25;
double altura = 1.80;
bool ativo = true;
String nome = "George";
var cidade = "Cuiabá"; // inferência automática
```

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


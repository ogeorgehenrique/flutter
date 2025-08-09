# Flutter?

Flutter é um kit de ferramentas (framework) de interface do usuário (UI) de código aberto, criado pelo Google em 2017, usado para desenvolver aplicativos nativos para dispositivos móveis (iOS e Android), web e desktop a partir de uma única base de código. Em outras palavras, com Flutter, você pode escrever o código uma vez e, com poucas ou nenhuma modificação, executar o aplicativo em várias plataformas. 

Você pode usar o Flutter para criar:
- Aplicativos móveis (Android, iOS)
- Aplicativos web (via navegador)
- Aplicações desktop (Windows, macOS, Linux)
- Aplicações embarcadas (ex: smart displays)

Ele usa a linguagem de programação Dart, também desenvolvida pelo Google.

**O que torna o Flutter especial?**
- Desenvolvimento multiplataforma: O Flutter permite que você crie aplicativos para diferentes sistemas operacionais com um único código, economizando tempo e recursos. 
- Desempenho: Aplicativos Flutter são conhecidos por seu bom desempenho, muitas vezes se aproximando do desempenho de aplicativos nativos. 
- Design: O Flutter oferece uma vasta biblioteca de widgets personalizáveis, permitindo que você crie interfaces de usuário atraentes e consistentes em diferentes plataformas. 
- Produtividade: O Flutter possui recursos como o "hot reload", que permite que você veja as alterações no aplicativo em tempo real, agilizando o processo de desenvolvimento. 
- Comunidade: O Flutter tem uma comunidade ativa e crescente de desenvolvedores, o que significa que há muitos recursos, tutoriais e suporte disponíveis. 

**Vantagens do Flutter**

| Vantagem                  | Descrição                                                                 |
|---------------------------|---------------------------------------------------------------------------|
| 🔁 Hot Reload             | Permite ver mudanças em tempo real, sem reiniciar o app.                  |
| 🧩 Reutilização de código | Uma base de código para Android, iOS, Web, Desktop.                       |
| 🎨 UI personalizável      | Renderiza a interface do zero — alta liberdade visual.                    |
| 🚀 Performance nativa     | Usa o Skia e compila para código nativo (AOT/JIT).                        |
| 🛠 Ecossistema em crescimento | Vários plugins, integração com Firebase, suporte da comunidade.      |


Em resumo, Flutter é uma ferramenta poderosa e flexível para o desenvolvimento de aplicativos, oferecendo benefícios como multiplataforma, bom desempenho, design atraente e alta produtividade.

# O que é o Flutter e Como Ele Funciona?

Pense no Flutter não apenas como um conjunto de ferramentas, mas como uma nova maneira de pensar sobre a construção de interfaces.

## O Conceito Principal: Tudo é um Widget

A primeira e mais importante regra no Flutter é: **tudo é um widget.**

Mas o que isso significa?

Imagine que você está montando uma tela de aplicativo com peças de LEGO. Cada peça, não importa o tamanho ou a função, é um "bloco". No Flutter, esses blocos são chamados de Widgets.

Um botão? É um widget (`ElevatedButton`).

Um texto? É um widget (`Text`).

O espaçamento entre dois itens? É um widget (`Padding` ou `SizedBox`).

A tela inteira? É um widget (`Scaffold`).

Até mesmo o alinhamento de um item no centro da tela é feito por um widget (`Center`).

Você constrói sua interface aninhando esses widgets uns dentro dos outros, criando uma árvore hierárquica chamada "`Widget Tree`" (Árvore de Widgets).

Analogia: Pense na sua árvore de widgets como uma árvore genealógica. O widget principal (`MaterialApp`, por exemplo) é o ancestral mais antigo, e dele descendem as telas (`Scaffold`), que por sua vez têm filhos como a barra de aplicativo (`AppBar`) e o corpo da tela (`body`), que contêm botões, textos, etc.

## A Arquitetura do Flutter: As Camadas

Para entender como o Flutter consegue ser tão rápido e flexível, precisamos olhar para sua arquitetura em camadas. Imagine uma cebola:

**Camada Dart (Framework):** É aqui que nós, desenvolvedores, passamos 99% do nosso tempo. Esta camada é escrita inteiramente em Dart, a linguagem de programação do Flutter. Ela contém toda a biblioteca de widgets (`Material Design, Cupertino`), as animações, o sistema de gestos, etc. É a camada de mais alto nível.

**Camada C/C++ (Engine):** O coração do Flutter. Esta camada é escrita em C++ e é responsável pelas coisas "pesadas". A principal responsabilidade do Engine é:
**1. Skia:** Uma biblioteca gráfica 2D de código aberto do Google. É o Skia que literalmente desenha cada pixel na tela. O Flutter não usa os componentes de interface nativos (OEM Widgets) do Android ou iOS. Ele desenha sua própria interface do zero, como um motor de jogo. É por isso que um botão no Flutter tem a mesma aparência em um Android 8 e em um Android 14.
**2. Dart Runtime:** Fornece o ambiente de execução para a sua aplicação.
**3. Text Rendering:** Lida com a renderização de fontes e textos.

**Camada Específica da Plataforma (Embedder):** É a camada mais "baixa", que se comunica diretamente com o sistema operacional (Android, iOS, Windows, etc.). Ela é responsável por coisas como:
1. Criar uma "tela" (canvas) onde o Flutter possa desenhar.
2. Lidar com eventos de entrada (toques na tela, teclado, mouse).
3. Gerenciar o ciclo de vida do aplicativo.

## O Processo de Renderização: Da Árvore de Widgets aos Pixels

Aqui está a mágica! Como seu código Dart se transforma em pixels na tela?

1. Widget Tree: Você cria sua árvore de widgets, que é basicamente uma "planta" da sua interface. Ela diz o que você quer mostrar.
2. Element Tree: O Flutter pega sua `Widget Tree` e a transforma em uma `Element Tree`. Cada Widget tem um Element correspondente. O `Element` é a "instância viva" do widget na árvore; ele sabe sua localização e gerencia as atualizações.
3. RenderObject Tree: O Element cria um `RenderObject`. É aqui que a mágica do layout acontece. O RenderObject sabe seu tamanho, sua posição e como ele deve ser "pintado". É ele que calcula as dimensões (constraints), o posicionamento e, finalmente, a pintura na tela.

**Por que tantas árvores? Eficiência!**

Quando algo muda na sua interface (por exemplo, você clica em um botão e um texto muda), o Flutter não reconstrói tudo do zero. Ele compara a nova `Widget Tree` com a antiga. Apenas os `Elements` cujos widgets mudaram são atualizados. Se a mudança for apenas de cor, por exemplo, o `RenderObject` só precisa se "repintar", sem precisar recalcular todo o layout. Esse processo é incrivelmente rápido e é a base da performance do Flutter.



# Widgets

Em Flutter, widgets são os blocos de construção da interface do usuário. **Tudo o que você vê em uma tela de aplicativo Flutter é um widget**, desde os elementos mais simples, como texto e botões, até os layouts mais complexos, como contêineres e listas. Cada widget representa uma parte imutável da interface, e a combinação e composição desses widgets resulta na interface completa do seu aplicativo. 

Em detalhes:
- **Tudo é um widget:** No Flutter, a filosofia é que tudo é um widget. Isso significa que até mesmo layouts e estruturas de navegação são construídos usando widgets.
- Widgets descrevem a interface: Widgets definem como a interface do usuário deve ser exibida, incluindo aspectos visuais (como texto, cores, formas) e interações (como botões que respondem a toques).
- Composição de widgets: Widgets podem ser compostos uns com os outros para criar layouts mais complexos. Por exemplo, um botão pode ser colocado dentro de um contêiner, que por sua vez pode ser colocado dentro de um layout de linha ou coluna. Um exemplo comum é um widget Text que exibe texto na tela, ou um widget Button que permite ao usuário interagir com o aplicativo. Estes podem ser combinados com outros widgets, como um widget Column que organiza os widgets verticalmente, ou um widget Row que os organiza horizontalmente. 
- Árvore de Widgets: A estrutura da interface do usuário em Flutter é organizada em uma árvore de widgets. Cada widget pode ter filhos (outros widgets), criando uma hierarquia que define a relação entre os elementos da interface.
- Personalização de widgets: O Flutter permite personalizar widgets de várias maneiras, seja modificando suas propriedades ou usando widgets específicos para criar efeitos visuais ou comportamentos personalizados. 
- Widgets stateless e stateful: Existem dois tipos principais de widgets em relação ao estado:

## StatelessWidgets
São widgets que não possuem estado interno e sua aparência é determinada apenas pelas propriedades fornecidas no momento da criação. Eles são usados para exibir informações estáticas ou quando o estado não precisa ser alterado.

## StatefulWidgets
São widgets que possuem estado interno e sua aparência pode mudar ao longo do tempo, por exemplo, em resposta a ações do usuário ou atualizações de dados. 


**Widgets Básicos - As Ferramentas Essenciais**

Aqui vamos focar nos widgets que você usará em 90% do tempo.

## 1. `Container` - A Caixa Mágica

Pense no Container como a "caixa" ou o "pote" do Flutter. É um dos widgets mais versáteis. Ele pode ser usado para:

1. Dar cor a uma área: Com a propriedade `color`.
2. Definir um tamanho: Com `width` (largura) e `height` (altura).
3. Adicionar espaçamento interno (preenchimento): Com `padding`.
4. Adicionar espaçamento externo (margem): `Com margin`.
5. Decorar com bordas, sombras e formas: Com a propriedade `decoration`. **Importante:** Se você usa a propriedade `decoration`, a `color` deve ser colocada dentro do `BoxDecoration`, e não diretamente no `Container`.

Exemplo:
```
Container(
  width: 200.0, // Largura de 200 pixels
  height: 200.0, // Altura de 200 pixels
  padding: EdgeInsets.all(16.0), // Espaçamento interno de 16 pixels em todos os lados
  margin: EdgeInsets.only(top: 20.0), // Espaçamento externo de 20 pixels apenas no topo
  decoration: BoxDecoration(
    color: Colors.blue, // Cor de fundo azul
    borderRadius: BorderRadius.circular(12.0), // Bordas arredondadas
    border: Border.all(color: Colors.black, width: 3.0), // Borda preta de 3 pixels
    boxShadow: [
      BoxShadow(
        color: Colors.black.withOpacity(0.5),
        spreadRadius: 5,
        blurRadius: 7,
        offset: Offset(0, 3), // Posição da sombra
      ),
    ],
  ),
  child: Center( // Um filho para o container
    child: Text(
      'Eu sou um Container!',
      style: TextStyle(color: Colors.white),
    ),
  ),
);
```
**Resultado Visual:** Uma caixa azul de 200x200 com bordas arredondadas, uma borda preta e uma sombra, contendo um texto branco centralizado.


## 2. `Row` e `Column` - Organizando em Linhas e Colunas

Esses são os seus principais widgets para organizar outros widgets na tela.

`Column`: Organiza seus filhos verticalmente (em uma coluna).

`Row`: Organiza seus filhos horizontalmente (em uma linha).

Ambos possuem uma propriedade `children` que aceita uma lista de widgets (`List<Widget>`).

As duas propriedades mais importantes para eles são:

1. `mainAxisAlignment`: Como os filhos são alinhados no eixo principal.
	- Para `Column`, o eixo principal é o vertical.
	- Para `Row`, o eixo principal é o horizontal.

2. `crossAxisAlignment`: Como os filhos são alinhados no eixo cruzado.
	- Para `Column`, o eixo cruzado é o horizontal.
	- Para `Row`, o eixo cruzado é o vertical.

Exemplo com `Column:
```
Column(
  mainAxisAlignment: MainAxisAlignment.spaceEvenly, // Espaçamento igual entre eles
  crossAxisAlignment: CrossAxisAlignment.start, // Alinha os filhos à esquerda
  children: <Widget>[
    Text('Item 1'),
    Icon(Icons.star, size: 50),
    ElevatedButton(onPressed: () {}, child: Text('Botão')),
  ],
);
```
**Resultado Visual:** O texto "Item 1", um ícone de estrela e um botão, organizados um embaixo do outro, com espaçamento igual entre eles e todos alinhados à esquerda da coluna.

Exemplo com `Row`:
```
Row(
  mainAxisAlignment: MainAxisAlignment.spaceAround, // Espaço ao redor de cada item
  crossAxisAlignment: CrossAxisAlignment.center, // Centraliza verticalmente na linha
  children: <Widget>[
    Icon(Icons.home, size: 40),
    Icon(Icons.search, size: 40),
    Icon(Icons.person, size: 40),
  ],
);
```
**Resultado Visual:** Três ícones lado a lado, com espaço ao redor de cada um, centralizados verticalmente.

## 3. `Text` - Mostrando Texto

Simples, mas essencial. O widget `Text` é usado para exibir qualquer string de texto.

Sua propriedade mais poderosa é a `style`, que aceita um `TextStyle` para customizar a aparência do texto.

```
Text(
  'Olá, Mundo do Flutter!',
  textAlign: TextAlign.center, // Alinhamento do texto dentro do seu espaço
  style: TextStyle(
    color: Colors.deepPurple,
    fontSize: 24.0,
    fontWeight: FontWeight.bold, // Negrito
    fontStyle: FontStyle.italic, // Itálico
    letterSpacing: 2.0, // Espaçamento entre as letras
  ),
),
```
## 4. `Scaffold` - A Estrutura da Tela

O `Scaffold` (andaime, em português) é um widget que fornece uma estrutura visual básica para uma tela de aplicativo no estilo Material Design. Ele facilita a adição de elementos comuns como:

- `appBar`: A barra no topo da tela.
- `body`: O conteúdo principal da sua tela.
- `floatingActionButton`: O botão de ação flutuante (geralmente no canto inferior direito).
- `drawer`: O menu lateral que desliza para fora.
- `bottomNavigationBar`: A barra de navegação na parte inferior.

Quase toda tela que você criar no seu aplicativo começará com um `Scaffold`.

Exemplo:
```
Scaffold(
  appBar: AppBar(
    title: Text('Meu Primeiro App'),
  ),
  body: Center(
    child: Text(
      'Este é o corpo (body) do meu Scaffold!',
      style: TextStyle(fontSize: 22),
    ),
  ),
  floatingAc tionButton: FloatingActionButton(
    onPressed: () {
      // Ação a ser executada quando o botão for pressionado
    },
    child: Icon(Icons.add),
  ),
)
```
**Resultado Visual:** Uma tela completa de aplicativo, com uma barra azul no topo escrita "Meu Primeiro App", um texto centralizado no corpo da tela e um botão circular com um ícone de "+" no canto inferior direito.

## StatelessWidget vs. StatefulWidget

No Flutter, os widgets se dividem em duas categorias principais, baseadas em uma única pergunta: "Este widget precisa mudar depois de ser desenhado na tela?"

## 1. StatelessWidget (Widget Sem Estado)

Como o nome sugere, um `StatelessWidget` não tem um "estado" interno que possa ser alterado. Uma vez construído, ele permanece o mesmo até ser destruído.

**O que é?** É um widget cujas propriedades são imutáveis. Todas as suas variáveis devem ser `final`. Isso significa que, uma vez que você passa os dados para ele (via construtor), esses dados não podem ser alterados dentro do próprio widget.

**Como funciona?** Ele tem apenas um método principal no seu ciclo de vida: `build()`. O Flutter chama esse método `build()` uma única vez (ou quando seu widget "pai" o reconstrói com novos dados) para desenhar a interface na tela. Ele descreve a parte da UI com base na configuração inicial que recebeu.

**Analogia:** Pense em um `StatelessWidget` como uma placa de rua ou uma fotografia impressa. Uma vez criada, ela não muda seu conteúdo. O texto na placa é sempre o mesmo.

**Quando usar?** Use para qualquer parte da interface que não precisa mudar dinamicamente.

1. Um ícone (`Icon`).
2. Um texto estático (`Text('Bem-vindo!')`).
3. Um botão cujo visual não muda (`ElevatedButton`).
4. Telas de apresentação, cabeçalhos, logos, etc.

Exemplo de Código:
```
// Um widget que exibe um cartão de boas-vindas.
// As informações (nome e ícone) são recebidas e não mudam.
class WelcomeCard extends StatelessWidget {
  // As propriedades são 'final', pois não podem ser alteradas.
  final String name;
  final IconData icon;

  // O construtor recebe os dados iniciais.
  const WelcomeCard({Key? key, required this.name, required this.icon}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    // O método build descreve a UI com base nos dados recebidos.
    return Container(
      padding: EdgeInsets.all(16.0),
      decoration: BoxDecoration(
        color: Colors.green,
        borderRadius: BorderRadius.circular(10.0),
      ),
      child: Row(
        children: [
          Icon(icon, color: Colors.white),
          SizedBox(width: 10), // Apenas um espaçamento
          Text(
            'Olá, $name!',
            style: TextStyle(color: Colors.white, fontSize: 20),
          ),
        ],
      ),
    );
  }
}
```

## 2. StatefulWidget (Widget Com Estado)

Este é o widget que você usará para criar interfaces dinâmicas. Ele pode mudar sua aparência em resposta a interações do usuário ou ao recebimento de novos dados.

**O que é?** É um widget que pode manter informações internas (o "estado") que podem mudar durante o tempo de vida do widget.

**Como funciona?** Aqui está a grande diferença: um `StatefulWidget` na verdade é composto por duas classes:

A classe `Widget` em si (ex: `CounterWidget`). Ela é imutável, assim como um StatelessWidget, e pode receber dados iniciais.

A classe `State` (ex: `_CounterWidgetState`). Esta é a parte mutável. É aqui que você guarda as variáveis que vão mudar, e é ela que contém o método `build()`.

**A Mágica do `setState()`:** Para notificar o Flutter que o estado mudou e que a tela precisa ser redesenhada, você obrigatoriamente precisa chamar a função `setState()`. Ao fazer isso, o Flutter executa o código que está dentro de `setState` e depois chama o método `build()` novamente, atualizando a interface com os novos valores do estado.

**Analogia:** Pense em um StatefulWidget como um quadro branco ou uma tela de videogame. Você pode apagar, reescrever e mudar o que está sendo exibido a qualquer momento. Um interruptor de luz também é um bom exemplo: ele tem dois estados ("ligado" e "desligado") e pode alternar entre eles.

**Quando usar?** Use sempre que a interface precisar ser atualizada sem recarregar a tela inteira.

1. Um Checkbox que o usuário pode marcar/desmarcar.
2. Um Slider para controlar o volume.
3. Um campo de formulário (TextField) onde o usuário digita um texto.
4. Um contador que incrementa quando um botão é pressionado.

Exemplo:
```
// 1. A classe do Widget (imutável)
class CounterWidget extends StatefulWidget {
  const CounterWidget({Key? key}) : super(key: key);

  @override
  State<CounterWidget> createState() => _CounterWidgetState();
}

// 2. A classe do Estado (mutável)
class _CounterWidgetState extends State<CounterWidget> {
  // A variável de estado. Ela não é 'final'.
  int _counter = 0;

  void _incrementCounter() {
    // setState() é chamado para notificar o Flutter da mudança.
    setState(() {
      // O Flutter executa este código e depois reconstrói o widget.
      _counter++;
    });
  }

  @override
  Widget build(BuildContext context) {
    // O build é chamado toda vez que setState é executado.
    return Column(
      mainAxisAlignment: MainAxisAlignment.center,
      children: <Widget>[
        Text(
          'Você pressionou o botão esta quantidade de vezes:',
        ),
        Text(
          '$_counter', // Exibe o valor atual do contador
          style: Theme.of(context).textTheme.headlineMedium,
        ),
        ElevatedButton(
          onPressed: _incrementCounter, // Chama o método para mudar o estado
          child: Icon(Icons.add),
        )
      ],
    );
  }
}
```
## StatelessWidget Vs StatefulWidget

| Característica     | StatelessWidget | StatefulWidget |
|--------------------|-----------------|----------------|
| **Mudança de Estado** | Não pode mudar seu estado interno. Imutável. | Pode mudar seu estado interno. Mutável. |
| **Dados**          | Os dados são recebidos via construtor e são `final`. | Os dados podem ser recebidos e o estado interno pode ser alterado. |
| **Ciclo de Vida**  | Simples (`constructor`, `build`). | Mais complexo (envolve o objeto `State`). |
| **setState()**     | Não possui. | Essencial. Usado para notificar o framework para redesenhar. |
| **Classes Envolvidas** | Uma classe. | Duas classes (`Widget` e `State`). |
| **Quando Usar**    | Para UI estática. Telas de "Sobre", ícones, textos fixos. | Para UI dinâmica. Formulários, contadores, animações. |

Entender quando usar um ou outro é fundamental para a performance e organização do seu código. A regra de ouro é: comece sempre com um `StatelessWidget`. Se você perceber que precisa que algo mude dentro dele, transforme-o em um `StatefulWidget`.

runApp


🧩 Principais Conceitos

Widgets

Tudo no Flutter é um widget:
	•	Um botão? É um widget.
	•	Um texto? Também.
	•	Um layout (coluna, linha, espaçamento)? Widget!

Existem dois tipos principais:
	•	StatelessWidget: não guarda estado (dados que mudam).
	•	StatefulWidget: armazena estado (permite mudanças na UI com setState()).

⸻



Estrutura Básica de um Projeto Flutter

```
meu_app/
├── android/        <- código nativo Android
├── ios/            <- código nativo iOS
├── lib/            <- código Dart principal
│   └── main.dart   <- ponto de entrada do app
├── web/            <- código para rodar no navegador
├── pubspec.yaml    <- dependências e configurações
└── test/           <- testes automatizados
```

Exemplo Simples
```
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
 @override
 Widget build(BuildContext context) {
   return MaterialApp(
     home: Scaffold(
       appBar: AppBar(title: Text("Olá, Flutter!")),
       body: Center(child: Text("Bem-vindo ao Flutter!")),
     ),
   );
 }
}
```

🚀 Caminho de Estudo Recomendado

Se você quiser, posso te guiar com um roteiro de aprendizado progressivo com prática. Aqui está uma visão geral:

📘 Módulo 1 – Fundamentos
	•	O que é Flutter e Dart
	•	Instalação e ambiente de desenvolvimento (VSCode ou Android Studio)
	•	Estrutura de um projeto Flutter
	•	Widgets básicos (Text, Container, Row, Column)

📗 Módulo 2 – Layouts e Navegação
	•	Widgets de layout
	•	Navegação entre telas
	•	Passagem de dados entre rotas

📙 Módulo 3 – Estado e Interatividade
	•	StatefulWidget e setState
	•	Gerenciamento de estado (Provider, Riverpod, Bloc etc.)

📕 Módulo 4 – Integrações
	•	Firebase (auth, firestore, storage)
	•	Consumo de APIs REST
	•	Armazenamento local (SharedPreferences)

📓 Módulo 5 – Publicação e Otimização
	•	Geração de builds
	•	Publicar na Play Store e App Store
	•	Melhorias de performance

⸻

Se quiser, posso criar projetos práticos, como:
	•	Um app de lista de tarefas
	•	Um app de controle de gastos
	•	Um app de receitas com imagens
	•	Um app com autenticação via Firebase


	Etapa 1: Preparando o Ambiente

1. Instale o Flutter SDK

Acesse o site oficial:
👉 https://flutter.dev/docs/get-started/install

Escolha seu sistema (Windows, macOS ou Linux) e siga os passos de instalação do SDK.

2. Instale um Editor de Código

Recomendado:
	•	Visual Studio Code (VSCode) com as extensões:
	•	Flutter
	•	Dart

⚠️ Se você já usa o Android Studio, também funciona muito bem, mas vamos focar no VSCode por ser mais leve.

3. Configure o Flutter

No terminal (ou no PowerShell / CMD no Windows), digite:

```
flutter doctor
```

Esse comando verifica se tudo está instalado corretamente.


📌 Etapa 2: Criando Seu Primeiro Projeto Flutter

No terminal:

```
flutter create hello_flutter
cd hello_flutter
```

Isso cria e abre um projeto com um app de exemplo.

No VSCode, abra o arquivo: `lib/main.dart`

E substitua o conteúdo por:

```
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Meu Primeiro App',
      home: Scaffold(
        appBar: AppBar(
          title: Text('Olá, Flutter!'),
        ),
        body: Center(
          child: Text('Bem-vindo ao Flutter 🚀'),
        ),
      ),
    );
  }
}
```

Agora rode o app com:
```
flutter run
```

Ou aperte F5 no VSCode com um emulador aberto (Android Emulator, ou um dispositivo conectado).



📌 Etapa 3: Aprendendo os Widgets Básicos

Vamos explorar os widgets essenciais:

1. Text

Exibe textos:
```
Text('Olá mundo', style: TextStyle(fontSize: 24))
```

2. Container

Permite estilizar e posicionar:

Container(
  padding: EdgeInsets.all(16),
  color: Colors.blue,
  child: Text('Dentro de um container'),
)

3. Column e Row

Organizam widgets verticalmente ou horizontalmente:

```
Column(
  children: [
    Text('Linha 1'),
    Text('Linha 2'),
  ],
)
```

```
Row(
  mainAxisAlignment: MainAxisAlignment.spaceBetween,
  children: [
    Icon(Icons.star),
    Icon(Icons.favorite),
  ],
)
```

4. Scaffold

Cria a estrutura da tela (app bar, body, etc).

5. MaterialApp

Inicia a aplicação com design Material (padrão do Google para Android/iOS).

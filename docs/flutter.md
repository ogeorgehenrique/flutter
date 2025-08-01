O que é o Flutter?

O Flutter é um framework open-source criado pelo Google, lançado em 2017, para o desenvolvimento de interfaces (UI) nativas e multiplataforma com uma única base de código.
Você pode usar o Flutter para criar:
	•	Aplicativos móveis (Android, iOS)
	•	Aplicativos web (via navegador)
	•	Aplicações desktop (Windows, macOS, Linux)
	•	Aplicações embarcadas (ex: smart displays)

Ele usa a linguagem de programação Dart, também desenvolvida pelo Google.

Como o Flutter Funciona?

Arquitetura Simplificada
	1.	Motor (Engine)
Escrita em C++, essa é a base do Flutter. Ele usa o mecanismo de renderização Skia para desenhar a interface na tela. Isso permite uma renderização super rápida, sem depender dos componentes nativos da plataforma.
	2.	Framework em Dart
Onde você programa: widgets, layout, navegação, animações etc.
	3.	Camada de plataforma (Platform Channels)
Quando o app precisa interagir com APIs específicas da plataforma (ex: câmera, sensores, arquivos locais), o Flutter usa platform channels para comunicar-se com código nativo (Java/Kotlin para Android, Swift/Obj-C para iOS).

⸻

🧩 Principais Conceitos

🧱 Widgets

Tudo no Flutter é um widget:
	•	Um botão? É um widget.
	•	Um texto? Também.
	•	Um layout (coluna, linha, espaçamento)? Widget!

Existem dois tipos principais:
	•	StatelessWidget: não guarda estado (dados que mudam).
	•	StatefulWidget: armazena estado (permite mudanças na UI com setState()).

⸻

🎯 Vantagens do Flutter

| Vantagem                  | Descrição                                                                 |
|---------------------------|---------------------------------------------------------------------------|
| 🔁 Hot Reload             | Permite ver mudanças em tempo real, sem reiniciar o app.                  |
| 🧩 Reutilização de código | Uma base de código para Android, iOS, Web, Desktop.                       |
| 🎨 UI personalizável      | Renderiza a interface do zero — alta liberdade visual.                    |
| 🚀 Performance nativa     | Usa o Skia e compila para código nativo (AOT/JIT).                        |
| 🛠 Ecossistema em crescimento | Vários plugins, integração com Firebase, suporte da comunidade.      |

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

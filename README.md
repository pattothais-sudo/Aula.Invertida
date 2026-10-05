# Finanças com Sucesso

## Sobre o projeto

O projeto **Finanças com Sucesso** é um aplicativo desenvolvido em Flutter para realizar o controle simples de despesas pessoais.

O aplicativo permite cadastrar uma despesa informando sua descrição e seu valor, visualizar a lista de despesas, consultar o valor total e excluir despesas deslizando o item para o lado.

Os dados cadastrados são armazenados no próprio aparelho utilizando a biblioteca `shared_preferences`.

## Objetivo da atividade

O objetivo foi analisar um código desenvolvido por outro programador, compreender seu funcionamento, identificar as bibliotecas e recursos utilizados e realizar a implementação do aplicativo.

## Tecnologias utilizadas

* Flutter
* Dart
* Material Design 3
* Shared Preferences
* JSON

## Bibliotecas utilizadas

### `dart:convert`

É uma biblioteca que já faz parte do Dart.

Neste projeto ela é utilizada para trabalhar com JSON.

Principais funções utilizadas:

* `jsonEncode()` — transforma os dados em texto JSON.
* `jsonDecode()` — transforma o texto JSON novamente em dados que podem ser utilizados pelo aplicativo.

### `flutter/material.dart`

É uma biblioteca do Flutter utilizada para construir a interface do aplicativo.

Ela fornece recursos como:

* `MaterialApp`
* `Scaffold`
* `AppBar`
* `TextField`
* `ElevatedButton`
* `ListView`
* `ListTile`
* `Dismissible`
* `Icon`
* `Text`

Também permite utilizar o Material Design 3.

### `shared_preferences`

É uma biblioteca externa utilizada para armazenar pequenas informações no dispositivo.

Neste projeto ela é utilizada para salvar as despesas cadastradas, permitindo que os dados continuem disponíveis mesmo depois que o aplicativo for fechado.

A chave utilizada para armazenar as despesas é:

```text
despesas
```

## Estrutura do código

### `main()`

É o ponto inicial do aplicativo.

```dart
void main() {
  runApp(const FinanceiroApp());
}
```

A função `runApp()` inicia o aplicativo e mostra o widget principal.

### `FinanceiroApp`

É um `StatelessWidget` responsável pela configuração inicial do aplicativo.

Nele são definidos:

* Nome do aplicativo
* Tema
* Material Design 3
* Tela inicial

### `Financeiro`

É um `StatefulWidget`, pois os dados da tela podem mudar durante a utilização do aplicativo.

### `_FinanceiroState`

É onde ficam as principais informações e funções do aplicativo.

São utilizados dois controladores:

```dart
final descricao = TextEditingController();
final valor = TextEditingController();
```

Eles permitem pegar os valores digitados pelo usuário nos campos de texto.

A lista:

```dart
List<Map<String, dynamic>> despesas = [];
```

armazena as despesas cadastradas.

Cada despesa possui:

* descrição
* valor
* data

## Funcionamento

### Carregamento das despesas

Quando o aplicativo é iniciado, a função `initState()` chama:

```dart
carregarDespesas();
```

Essa função procura as despesas salvas no `SharedPreferences`.

### Adicionar despesa

A função:

```dart
adicionarDespesa()
```

verifica se os campos foram preenchidos, transforma o valor digitado em número e adiciona uma nova despesa à lista.

Depois disso, os dados são salvos no aparelho.

### Excluir despesa

A função:

```dart
excluirDespesa()
```

remove uma despesa da lista e salva novamente os dados.

A exclusão pode ser feita deslizando a despesa para a esquerda.

### Cálculo do total

A função:

```dart
total()
```

soma os valores de todas as despesas cadastradas.

O resultado aparece na parte superior da lista.

## Recursos da interface

O aplicativo utiliza:

* Campo para descrição da despesa
* Campo para valor
* Botão para adicionar
* Exibição do total
* Lista de despesas
* Data da despesa
* Botão/gesto para exclusão
* Mensagem quando não existem despesas cadastradas

## Armazenamento dos dados

Os dados são transformados em JSON antes de serem armazenados.

Exemplo:

```json
[
  {
    "descricao": "Mercado",
    "valor": 50.0,
    "data": "2026-10-05"
  }
]
```

Quando o aplicativo é aberto novamente, o JSON é lido e convertido para a lista de despesas.

## Pontos analisados

Durante a análise do código, foram identificados alguns conceitos importantes:

* Diferença entre `StatelessWidget` e `StatefulWidget`
* Uso de `setState()`
* Uso de `TextEditingController`
* Armazenamento local com `SharedPreferences`
* Conversão de dados com JSON
* Uso de funções assíncronas com `Future` e `async/await`
* Construção de listas com `ListView.builder`
* Exclusão com `Dismissible`
* Cálculo utilizando `fold()`
* Organização da interface com widgets do Flutter

## Como executar o projeto

É necessário ter o Flutter instalado.

Após baixar o projeto, abra a pasta no VS Code e execute:

```bash
flutter pub get
```

Depois:

```bash
flutter run
```

Para gerar o APK:

```bash
flutter build apk
```

O arquivo será gerado em:

```text
build/app/outputs/flutter-apk/app-release.apk
```

## Conclusão

O código analisado apresenta uma aplicação simples de controle financeiro utilizando Flutter.

A aplicação demonstra conceitos importantes de desenvolvimento mobile, como criação de interfaces, gerenciamento de estado, armazenamento local, manipulação de dados e interação com o usuário.

A implementação permitiu compreender como diferentes recursos do Flutter e do Dart trabalham juntos para criar um aplicativo funcional.

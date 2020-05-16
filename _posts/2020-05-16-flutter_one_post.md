---
layout: post
title:  "Série Flutter - App Flutter com JSON"
date:   2020-05-16 09:23:39
categories: others
---

# Como construir um Flutter JSON App

Neste tutorial vamos desenvolver um aplicativo que acessa um arquivo JSON local e exibe suas informações em uma lista. Para fins ditáticos, usaremos o princípio de código limpo para o desenvolvimento, 

Para seguir o tutorial é importante ter os seguintes conhecimentos:

* POO - Programação Orientada à Objeto
* Experiência básica com Flutter

## Primeira Etapa - Configurações Básicas

Primeiramente, crie um projeto Flutter chamado **jsontest** (ou com o nome que desejar).

Precisamos antes de tudo, adicionar o arquivo JSON no projeto. Para esse tutorial, usaremos esse arquivo: [data.json](/assets/data.json).

Com o arquivo em mãos, adicionemos sua referência no arquivo **pubspec.yaml** desse modo (é interessante criar uma pasta para deixar o arquivo): 

![flutter_pubspec.yaml](/assets/image_pubspec_flutter.PNG)

Próxima configuração é em relação a disposição das pastas e arquivos. Para este tutorial, iremos separar os códigos em arquivos, identificando e destacando suas respectivas responsabilidades.

Análise a pasta **lib** nessa imagem:

![flutter_pubspec.yaml](/assets/image_directory_flutter.PNG)

* Na pasta **lib** ficará todo o nosso código.
* Na pasta **models** ficaram as nossas classes **Character** e **CharacterProvider**
    * **Character** é a representação dos dados do arquivo JSON seguindo as regras da POO.
    * **CharacterProvider** é a classe que puxará os dados do arquivo JSON e criará as instâncias dos objetos dos respectivos dados.
* Na pasta **pages** ficaram as nossas classes que exibiram as telas com seus respectivos componentes gráficos.
* E por fim, mas não menos importante, o arquivo **main.dart** que ligará todos os arquivos e executará o aplicativo.

## Segunda Etapa - Criação do Model e do Provider

Seria mais fácil exibirmos os dados do arquivo JSON diretamente nas **pages**, mas não é o correto quando se trata de código limpo. 

Precisamos separar o acesso ao JSON bem como a classe que representará os dados do arquivo. Essa separação facilitará a manutenção do código e também futuras **features** (tipo trocar JSON por uma API ou um SQLite da vida).

### Criando a representação dos dados:

A classe **Character** representará os dados do arquivo na nossa aplicação:

Arquivo **/lib/models/Character.dart**:

![flutter_pubspec.yaml](/assets/image_character_flutter.PNG)

### Criando o provedor dos dados:

O arquivo **CharacterProvider** fará o acesso ao arquivo JSON. Feito o acesso, ele irá ler os dados e os decodificará para a criação das instâncias da nossa Model. Se quisermos, no futuro, poderemos trocar esse arquivo por um Provider que tirará os dados de uma API. Essa troca não trará muitos problemas no restante dos códigos do aplicativo.

Arquivo **/lib/models/CharacterProvider.dart**:

![flutter_pubspec.yaml](/assets/image_provider_flutter.PNG)

## Terceira Etapa - Exibir os dados na tela

Terceira e penúltima etapa é exibirmos os dados tirados do arquivo. Nas etapas anteriores criamos o código necessário para converter JSON em instâncias de objetos, seguindo a lógica de um código mais limpo possível.

Agora tendo os objetos instanciados, só precisamos exibi-los da forma que desejarmos, seja em uma **ListView** ou uma **GridView** (aí vai da sua preferência e/ou conhecimento). Neste tutorial optaremos por uma **ListView** sem muitas frescuras.

Dentro da pasta **pages**, criaremos o arquivo **Home.dart**.

Primeiramente, importaremos as bibliotecas necessárias: 

![flutter_pubspec.yaml](/assets/image_dependency_flutter.PNG)

Feito isso, adicionaremos o código necessário para criar uma páginas dinâmica, com o widget **Scaffold()** que já vem com aparência e comportamentos pré-configurados:

(Detalhe para o método **initState()**, onde instanciamos uma lista de **Character** toda vez que a aplicação for iniciada através do método **loadCharacter** que definimos no **CharacterProvider** -- aí é que está a magia)

![flutter_pubspec.yaml](/assets/image_homepage_flutter.PNG)

Dentro do widget **Scaffold()**, adicionaremos o seguinte código:

![flutter_pubspec.yaml](/assets/image_scaffold_flutter.PNG)

Perceba que não estamos exibindo o JSON diretamente, mas sim uma lista de **Character** que por sua vez foi tirada de um arquivo JSON.Desse modo temos cada arquivo fazendo uma determinada função.

Vamos para a última etapa!

## Quarta Etapa - Configurar o **main.dart**

Agora precisamos juntar todos essas partes de códigos que criamos em um arquivo principal que será responsável por executar a aplicação.

Se você criou o projeto Flutter recentemente, vai encontrar nesse arquivo um código documentado (é importante que você leia-o e entenda as nuances do Flutter se já não o fez, mas neste tutorial não usaremos ele).

Apague ele todo e adicione o seguinte código:

![flutter_pubspec.yaml](/assets/image_main_flutter.PNG)

## Pronto!

Se tudo ocorreu bem até aqui, a execução será bem sucedida. Se gerar algum erro,, talvez você tenha que verificar as linhas de importação em cada arquivo.

![flutter_pubspec.yaml](/assets/image_dependency_flutter.PNG)

Certifique que o nome do projeto que você criou esteja como está na imagem acima, seguindo a norma: **package:<nome_do_seu_projeto>/models...**.

Se surgir, mande sua dúvida no meu email, **joogabrielsntn66@gmail.com**, que eu tentarei ajudar da melhor forma.

Que a Força esteja com vocês!, fiquem em casa!

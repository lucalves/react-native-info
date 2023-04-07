# Inicializando o projeto 💻

> Nessa seção, será apresentado como inicializar um projeto para começar a desenvolver utilizando React Native.

Para inicializar o projeto, optaremos por utilizar o projeto sem boiterplates (projetos pré-configurados), porém mencionaremos alguns boiterplates se caso você tenha interesse em conferir a medida que for entendendo mais como funciona o desenvolvimento com React Native.

O motivo pelo qual optaremos por não utilizar boiterplates é para ser mais simples de entender o fluxo do desenvolvimento de um aplicativo, geralmente quando um time cria um projeto a partir de um projeto pré-configurado, eles sabem exatamente o que está acontecendo para poder desenvolver a partir dele.

Muitos vem com bibliotecas como react-navigation, axios, redux, etc. Se você não entender o objetivo de cada uma delas, não vai ser interessante utilizar o boiterplate. A menos que você seja um desenvolvedor com mais experiência, aí recomendamos utilizar os boiterplates para facilitar e melhorar o tempo de desenvolvimento (não ser preciso configurar várias bibliotecas, já que vem tudo pré-configurado).

## Inicializando um projeto (sem boiterplate)

Essa é a maneira de criar um projeto mais interessante para quem tá começando a trabalhar com React Native.

Essas são as opções mais populares para inicializar um projeto totalmente do zero, ambas são mencionadas na documentação oficial do React Native:

- **create-expo-app**:

Por meio dessa ferramenta, você irá criar seu aplicativo através do Expo. Expo é uma estrutura de código aberto para aplicativos executados nativamente.

A vantagem é que você precisa somente do aplicativo Expo Go, e escaneando um QR Code você consegue ver o seu aplicativo rodando no seu celular. Muito rápido para configurar, ótimo para criar aplicativos e testar sem a necessidade de um cabo usb para compilar no seu celular ou gerar um apk.

- **react-native init**:

> Utilizaremos essa forma na criação do nosso aplicativo de exemplo.

O React Native possui uma interface de linha de comando integrada, que você pode usar para gerar um novo projeto. Essa opção é bastante útil para você aprender a desenvolver seu aplicativo do zero.

Para mais detalhes de como inicializar seu projeto, consulte a [documentação](https://reactnative.dev/docs/environment-setup).

## Boiterplates

Na programação, um _código boiterplate_, ou simplesmente _boiterplate_, são estruturas de código que geralmente são criadas com algumas pré-configurações (exemplo: instalação de pacotes, configurações de eslint e prettier), para melhorar o tempo de desenvolvimento do time/empresa e evitar que repitam o processo de sempre instalar as mesmas dependências para inicializar um projeto.

> O uso deles são recomendados para desenvolvedores mais experientes que saibam utilizar as ferramentas que vêm instaladas por padrão nos boiterplates.

Alguns exemplos de boiterplates em react native:

- **ignite**:

Um dos mais conhecidos, mantido pela Infinite Red e pela comunidade em código aberto, vem diversos pacotes pré-configurados como Flipper, Jest, Detox, Expo, MobX, React Navigation, etc.

Pode ser inicializado por meio do comando:

``npx ignite-cli@latest new <name_app>``

Encontre mais detalhes na [documentação do ignite](https://github.com/infinitered/ignite).

- **react-native-starter-kit**:

O projeto é super útil para dar o pontapé inicial em seu projeto, pois fornece muitas das ferramentas comuns que você pode usar, todas prontas para uso. São elas, por exemplo: Redux, React Native Router Flux, Linter do AirBNB, React Native Splash Screen, e muitos outros.

Para mais detalhes, confira na [documentação](https://github.com/mcnamee/react-native-starter-kit#-docs).

- **thecodingmachine/react-native-boiterplate**:

Esse boiterplate é mantido pela [The Coding Machine](https://github.com/thecodingmachine) e fornece uma arquitetura otimizada para a criação de aplicativos móveis sólidos de plataforma cruzada por meio da separação de preocupações entre a interface do usuário e a lógica de negócios.

Ele é totalmente documentado para que cada parte do código que chega ao seu aplicativo possa ser entendida e usada.

Consulte mais detalhes no [repositório oficial](https://github.com/thecodingmachine/react-native-boilerplate).

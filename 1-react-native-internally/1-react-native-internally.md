# React Native Internamente ⚙️

> Nesse tópico será descrito o que é o React Native, como ele ajuda os desenvolvedores a criar aplicativos nativos e como funciona internamente, como é sua engine.

React Native é um projeto disponibilizado e mantido pelos desenvolvedores do Facebook e possui uma estrutura que permite aos desenvolvedores criar aplicativos nativos usando Javascript.

Os aplicativos React Native têm acesso direto a todas as APIs nativas e visualizações oferecidas pelo sistema operacional móvel subjacente. Assim, os aplicativos RN têm a mesma sensação e desempenho de um aplicativo nativo.

## Renderização 🔄

É importante falarmos sobre alguns conceitos de renderização no React Native:

- **Fabric**
- **Render, Commit and Mount**
- **Cross platform Implementation**
- **View Flattening**
- **Threading Model**

### Fabric

Fabric é o novo sistema de renderização do React Native, evoluindo bastante o sistema de renderização antigo. Os princípios básicos são unificar a lógica de renderização em C++ e desbloquear novos recursos para o React Native da camada nativa Android e iOS.

Essa nova arquitetura fornece benefícios em qualidade de código, desempenho e extensabilidade:

- Melhorias na segurança da tipagem
- Código C++ compartilhado entre as plataformas
- Melhor Interoperabilidade da Plataforma Host
- Performance melhorada
- Consistência entre plataformas
- Inicialização mais rápida
- Menos serialização de dados entre JS e plataforma host

Consulte mais detalhes sobre o Fabric, na [documentação oficial](https://reactnative.dev/architecture/fabric-renderer).

### Render, Commit, and Mount

O renderizador React Native passa por uma sequência de trabalhos para renderizar a lógica React para as plataformas nativas (Android, iOS, macOS, Windows). Essa sequência de trabalho é chamada de pipeline de renderização e ocorre para renderizações iniciais e atualizações no estado da UI (User Interface):

![Render Phases](https://d33wubrfki0l68.cloudfront.net/dd89ae658f364cd434906164c095887108928f7e/b7225/assets/images/phase-one-render-cdd8336227468340a4c6b37d485e5bf8.png)

1. **Render**: O React executa a lógica do produto que cria uma React Element Trees em JavaScript. A partir dessa árvore, o renderizador cria uma [React Shadow Tree](https://reactnative.dev/architecture/glossary#react-shadow-tree-and-react-shadow-node) em C++.

2. **Commit**: Depois que uma React Shadow Tree é totalmente criada, o renderizador aciona um commit. Isso promove tanto a React Element Tree quanto a recém-criada React Shadow Tree como a “próxima árvore” a ser montada. Isso também agenda o cálculo de suas informações de layout.

3. **Mount**: A React Shadow Tree, agora com os resultados do cálculo do layout, é transformada em uma [Host View Tree](https://reactnative.dev/architecture/glossary#host-view-tree-and-host-view).

Para encontrar mais detalhes de cada estado da pipeline, acesse a [documentação oficial](https://reactnative.dev/architecture/render-pipeline).

### Cross Platform Implementation

O renderizador React Native utiliza uma implementação de renderização _core_ para ser compartilhada entre plataformas.

Aproveitar o C++ para o sistema de renderização principal apresenta várias vantagens. Uma única implementação reduz o custo de desenvolvimento e manutenção.

![Image Cross Platform](https://d33wubrfki0l68.cloudfront.net/1b5590a7ce6d4f9b805b020876fb161fb622eb90/eb9f1/assets/images/xplat-implementation-diagram-7611cf9dfb6d15667365630147d83ca5.png)

O renderizador fornece dois lados de suas APIs C++:

1. **Para se comunicar com o React**: Se comunica com o renderizador para renderizar uma React Tree e “ouvir” eventos (por exemplo, onLayout, onKeyPress, touch, etc)

2. **Para se comunicar com a plataforma nativa**: O renderizador React Native se comunica com a plataforma host para montar exibições de host na tela (criar, inserir, atualizar ou excluir exibições de host) e escuta eventos gerados pelo usuário na plataforma host.

### View Flattening

O View Flattening é uma otimização do renderizador React Native para evitar árvores de layout profundas.

A API do React foi projetada para ser declarativa e reutilizável por meio de composição. Isso fornece um ótimo modelo para desenvolvimento intuitivo. No entanto, na implementação, essas qualidades da API levam à criação de React Element Trees profundas, onde a grande maioria dos React Element Nodes afeta apenas o layout de uma View e não renderiza nada na tela. Chamamos esses tipos de nós de nós "somente layout".

Conceitualmente, cada um dos nós da árvore de elementos React tem uma relação de 1:1 com uma visualização na tela, portanto, renderizar uma árvore de elemento React profunda que é composta por uma grande quantidade de Node “Layout-Only” leva a um desempenho ruim durante a renderização.

Como parte do processo de renderização, o React Native produzirá as seguintes árvores:

![React Tree](https://d33wubrfki0l68.cloudfront.net/3f911132047469db255352764593f170187e749a/10d74/assets/images/diagram-one-3f2f9d7a2fa9d97b6b86fa3bd9b886d1.png)

É importante observar que essa otimização permite que o renderizador evite a criação e a renderização de duas exibições de host. Do ponto de vista do usuário, não há alterações visíveis na tela.

### Threading Model

O renderizador React Native foi projetado para ser thread-safe. Em um alto nível, a segurança do encadeamento é garantida pelo uso de estruturas de dados imutáveis ​​nas partes internas da estrutura (imposta pelo recurso de “correção constante” do C++). Isso significa que cada atualização no React cria ou clona novos objetos no renderizador em vez de atualizar as estruturas de dados. Isso permite que a estrutura exponha APIs thread-safe e síncronas para React.

O renderizador usa três threads diferentes:

**UI thread** (geralmente chamado de main thread): O único segmento que pode manipular exibições de host.
**JavaScript thread**: é aqui que a fase de renderização do React é executada.
**Background thread**: Thread dedicada ao layout.

Vamos revisar os cenários de execução suportados para cada fase:

![Render Scenarios](https://d33wubrfki0l68.cloudfront.net/fb7d0c08d948749cad7e16f9a489949b0407d2d7/627e2/docs/assets/architecture/threading-model/symbols.png)

## Ferramenta de build 🚀

### Hermes

- [ ] À ser incluso.

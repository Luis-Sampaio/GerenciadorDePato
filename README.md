# Projeto Simulador de Patos

Este é um projeto de console em C# desenvolvido para demonstrar a aplicação prática de conceitos fundamentais de Programação Orientada a Objetos (POO) e Padrões de Design. A aplicação simula diferentes tipos de patos, 
cada um com características e habilidades únicas, que podem ser selecionadas e testadas pelo usuário através de um menu interativo.

## 🎯 Conceitos e Padrões Aplicados

O principal objetivo deste projeto é exemplificar como os princípios da POO podem ser usados para criar um código flexível, extensível e de fácil manutenção.

### 1. Programação Voltada a Interfaces (Strategy Pattern)

Este é o conceito central do projeto. Em vez de adicionar todos os comportamentos possíveis (voar, nadar, grasnar, etc.) à classe base `Pato`, o que forçaria todos os patos a terem implementações para todos os comportamentos 
(mesmo que não fizessem sentido, como um pato de borracha voando), utilizamos interfaces para definir "famílias de algoritmos" (comportamentos).

- **Interfaces de Comportamento**: Foram criadas interfaces para cada habilidade, como `IVoar`, `INadar`, `IQuack`, `IBrigar`, `IEncantar` e `IPular`.
- **Composição em vez de Herança**: As classes concretas de patos (como `PatoDeBriga`, `PatoDeMetal`, `PatoBorracha`) herdam da classe base `Pato` e implementam apenas as interfaces correspondentes às suas habilidades.

Essa abordagem, conhecida como **Strategy Pattern**, permite que novos comportamentos e novos tipos de patos sejam adicionados ao sistema com o mínimo de alteração no código existente, honrando o **Princípio Aberto/Fechado (Open/Closed Principle)**.

### 2. Pilares da Programação Orientada a Objetos

- **Abstração e Herança**: Uma classe base `Pato` define os atributos comuns a todos os patos (`nome`, `cor`, `peso`). As classes específicas, como `PatoCabecaVermelha` e `PatoFormoso`, herdam essas características, evitando a repetição de código.

- **Polimorfismo** : O polimorfismo é amplamente utilizado, principalmente na classe `SelecionadorDePato`. Uma `List<Pato>` armazena objetos de diferentes tipos concretos (Marreco, PatoCruzeirense, etc.).
- O programa interage com cada um deles através da referência da classe base `Pato`, chamando métodos como `Display()`, que possuem implementações (`override`) diferentes para cada tipo de pato.

- **Encapsulamento**: A lógica de cada parte do sistema está contida em sua própria classe, com responsabilidades bem definidas. Por exemplo:
  - **`MenuPrincipal`**: Encapsula a lógica de navegação do menu principal.
  - **`GerenciadorDePatos`**: Encapsula a criação e o fornecimento da lista de patos disponíveis.
  - **`SelecionadorDePato`**: Encapsula a lógica de seleção e interação com as habilidades de um pato.

### 3. Separação de Responsabilidades (Separation of Concerns)

O projeto está organizado em namespaces para separar as diferentes camadas da aplicação:
- **`namespace Patos`**: Contém toda a lógica de domínio, ou seja, as definições e implementações dos diferentes tipos de patos.
- **`namespace Menu`**: Contém a lógica de apresentação e interação com o usuário (UI), como a exibição de menus, regras e créditos.

Essa separação torna o código mais organizado, legível e fácil de dar manutenção.


### 🚀 Estrutura do Projeto
```
/
├── Patos/              # Contém as classes que definem os patos e seus comportamentos
│   ├── IBrigar.cs
│   ├── IEncantar.cs
│   ├── INadar.cs
│   ├── IPular.cs
│   ├── IQuack.cs
│   ├── IVoar.cs
│   ├── Pato.cs         # Classe base abstrata (inferida)
│   ├── Marreco.cs
│   ├── PatoBorracha.cs
│   └── ... (outras classes de patos)
│
├── Menu/               # Contém as classes responsáveis pela interface com o usuário
│   ├── MenuPrincipal.cs
│   ├── SelecionadorDePato.cs
│   ├── ExibidorDeCreditos.cs
│   └── ExibidorDeRegras.cs
│
└── Program.cs          # Ponto de entrada da aplicação
```

Em resumo, este projeto foi construído como um trabalho acadêmico por quatro alunos para a disciplina de Programação Orientada a Objetos. O objetivo principal foi aplicar na prática os conceitos fundamentais da POO, como polimorfismo, herança e encapsulamento, 
com um foco especial no uso de interfaces para a implementação do padrão de design Strategy, resultando em um código flexível, modular e de fácil extensão.

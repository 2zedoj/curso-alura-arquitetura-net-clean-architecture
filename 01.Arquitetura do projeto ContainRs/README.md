
# 📦 01. Arquitetura do Projeto ContainRs

Nesta pasta contém o estudo prático realizado no tópico de estudos "Arquitetura do projeto ContainRs" a partir do curso de Arquitetura .NET com foco em **Clean Architecture**, da plataforma Alura.

O projeto base simula um sistema de **registro de clientes para aluguel de contêineres**, evoluindo gradualmente com melhorias arquiteturais, boas práticas e aplicação de conceitos como **SOLID**, **Design Patterns** e separação de responsabilidades.

Neste tópico de estudos, temos o foco inicial em entendermos o conceito de arquitetura de software e o quão importante é termos uma boa arquitetura. Para isso, foi dado um desafio prático, que fez com que conseguissemos identificar a necessidade de uma boa estrutura.



## 🚀 Tecnologias Utilizadas

-   .NET SDK 8
-   SQL Server
-   Entity Framework Core
-   ASP.NET MVC
-   Visual Studio

## 📚 Objetivo do Projeto

O objetivo principal deste projeto é compreender, na prática:

-   Conceitos de **Arquitetura de Software**
-   Conceitos iniciais de **Clean Architecture**
-   Uso do padrão **MVC (Model-View-Controller)**
-   Boas práticas de desenvolvimento
-   Separação de responsabilidades
-   Evolução de sistemas legados para arquiteturas mais sustentáveis


## 🏗️ Estrutura Inicial do Projeto

O projeto inicia com uma arquitetura tradicional em MVC:

    ContainRs.WebApp/  
	    │  
	    ├── Controllers  
	    ├── Models  
	    ├── Views  
	    ├── Services  
	    ├── Data  
	    └── wwwroot

### 📌 Conceitos importantes

-   **Controllers** → Responsáveis por receber requisições e coordenar ações
-   **Models** → Representam dados e regras de negócio
-   **Views** → Responsáveis pela interface com o usuário
-   **Services** → Contêm regras de negócio adicionais
-   **Data** → Camada de acesso a dados


## ⚙️ Setup do Projeto

### 🔧 Pré-requisitos

-   .NET SDK 8 instalado
-   SQL Server configurado

### ▶️ Executando o projeto

Para criar o banco de dados e aplicar as migrations, execute:

    dotnet ef database update \  
    --project .\ContainRs.WebApp\ContainRs.WebApp.csproj \  
    --startup-project .\ContainRs.WebApp\ContainRs.WebApp.csproj



## 🧠 Evolução do Projeto (Aprendizados)

Vendo como funciona a arquitetura, foi nos dado um exercicio prático, para entender a necessidade de uma boa arquitetura, sendo a tarefa:

### ✔️ Validação de Idade

Foi implementada uma regra de negócio importante:

> Apenas clientes **maiores de 18 anos** podem se cadastrar.

Alterações realizadas:

 -   Adição do campo **Data de Nascimento**
 -   Validação no **Model**
 -   Validação no **Controller**
 -   Atualização da **View**



Ao entendermos a arquitetura do projeto, foi fácil aplicar o sistema de validação de idade, pois sabemos a responsabilidade de cada camada e seu objetivo.
Isso evita um dos erros mais comuns no início da carreira: sair codando sem entender o sistema.

Quando isso acontece:
- você coloca lógica no lugar errado
- quebra funcionalidades existentes
- dificulta futuras manutenções

Entender a arquitetura antes de codar economiza tempo e evita retrabalho.

## 🧠 Novo Cenário

Agora imagine o seguinte cenário, você recebe uma demanda, do qual de validar o score do cliente durante o cadastro dele no sistema. O fluxo deve seguir da seguinte forma:

 - Score >= 600 (Permite cadastrar o cliente)
 - Score < 600 (Bloqueia o cadastro e emite uma mensagem, "Score baixo")
 
CALMA LÁ!!! Sei que está animado para já começar a codar que eu seii.

![enter image description here](https://miro.medium.com/v2/resize:fit:1000/0*HmIECLMB2YwdmUCS.gif)

Agora pense:

- Essa validação deveria ficar no Controller?
- No Model?
- Em um Service?
- Ou em uma camada externa?

Esse tipo de pergunta é exatamente o que a arquitetura de software nos ajuda a responder.
Agora, com a nossa demanda, precisamos entender EXATAMENTE o que iremos fazer no sistema. Então pegue um café e com calma analise o projeto e sua arquitetura de software. Se tiver documentação, melhor ainda!!

![enter image description here](https://i.pinimg.com/originals/d5/d0/3c/d5d03c1ad932a7dd4160ea577294af3a.gif)

Aqui entendemos a importância de uma boa arquitetura. Caso você leu a documentação, viu o código e mesmo assim não entendeu aonde que vai ter que aplicar a demanda.

![enter image description here](https://media.tenor.com/QU5h00CSbVUAAAAM/this-is-fine-fire.gif)

Muita calma nessa hora, você provavelmente encontrou uma arquitetura de software, que chamamos de arquitetura espaguete, não, não é um espaguete.

![enter image description here](https://i.pinimg.com/originals/ea/16/87/ea1687630df89db6030b82e9028b20dd.gif)

A arquitetura espaguete  é um antipadrão de software caracterizado por um código desestruturado, com fluxo de controle confuso, emaranhado e difícil de manter, assemelhando-se a um prato de espaguete.
Isso dificulta muito ao desenvolvedor realizar novas funcionalidades e manutenções dentro do código, por isso que hoje exigimos um padrão alto nas arquiteturas e existem diferentes tipos, como hexagonal, MVC, DDD, entre outros. Eles nos permite identificar exatamente as responsabilidades e assim temos uma arquitetura translúcida.
Assim, entendemos o porque é EXTREMAMENTE necessário termos uma boa arquitetura de software.
E é exatamente esse tipo de problema que uma boa arquitetura evita. Ela não serve apenas para organizar o código, mas para facilitar decisões no dia a dia do desenvolvimento.

![enter image description here](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjzxbXctfPPZV3DCnwqmURPrWyno7GxNXSOwgmOCh7beVL7hkPqrDTv4Fh61_hMe8eJPYJcEPhumcnhPic4dyAnLZ8YpjxZ4-X4G1Lsd2nPCN98I3VNj9tvD2fX8V5TrGkkp-SU8_myCDg/s0/substantivos+flex%25C3%25A3o+g%25C3%25AAnero+biforme+epiceno+sobrecomum+comum+de+dois.gif)

## 🧩 Conceitos Fundamentais

### 🏛️ Arquitetura de Software

Arquitetura de software é a forma como os componentes de um sistema são organizados e se comunicam entre si, visando:

-   Facilidade de manutenção
-   Escalabilidade
-   Clareza
-   Evolução contínua

----------


### 🔄 Padrão MVC

No contexto deste projeto:

- **Model** → Representa o cliente (ex: dados, validação de idade)
- **View** → Formulário de cadastro exibido ao usuário
- **Controller** → Recebe os dados do formulário e decide o que fazer com eles

Isso permite que cada parte tenha uma responsabilidade clara, facilitando manutenção e evolução.

----------

### 🧼 Clean Architecture

Baseada nos conceitos de Robert C. Martin, essa abordagem propõe:

-   Independência de frameworks
-   Independência de banco de dados
-   Código desacoplado
-   Facilidade de testes
-   Alta manutenibilidade


## 📈 Benefícios de uma Boa Arquitetura

-   Código mais organizado
-   Facilidade de entendimento
-   Facilidade de manutenção
-   Evolução contínua do sistema
-   Melhor integração com novas funcionalidades




## 📌 Conclusão

Neste módulo, o foco não foi implementar soluções complexas, mas sim entender como a arquitetura influencia diretamente o desenvolvimento.

Foi possível perceber que:

- Antes de codar, é essencial entender a estrutura do sistema
- A separação de responsabilidades facilita a implementação de novas regras
- O padrão MVC ajuda a organizar o código de forma clara

Esse entendimento será fundamental para os próximos passos, onde a arquitetura evoluirá para modelos mais robustos como a Clean Architecture.

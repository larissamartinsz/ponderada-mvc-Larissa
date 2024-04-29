# Arquitetura MVC
- Nome do Projeto: TechBridge
- Descrição: O projeto consiste basicamente em propiciar uma ferramenta capaz de facilitar a integração de pessoas de diferentes lugares do mundo. Para isso, a solução possuirá duas frentes: 1.  Entender perfis comportamentais e coletar feedbacks de jogadores; 2. Oferecer essas informações aos tutores, para que esses saibam como ajudar nas problemáticas de cada grupo.
- Arquitetura: MVC (Model-View-Controller)
- Ferramenta de Diagramação: Draw.io

### Modelos (Models):
Para arquitetar os modelos dessa aplicação, optou-se por dividi-los em 3 entidades, User, direcionado aos jogadores do Cesim, Tutor, que se relaciona aos professores/tutores dos times, e Grupo, para designar dados que correspondem ao grupo no geral.

- User: Enquanto dados que correspondem ao usuário jogador do Cesim estabeleceu-se 8 atributos. Dentre eles, alguns ditam informações previamente estabelecidos como: id, nome, foto de perfil, país e grupo, enquanto outros armazenam informações que serão definidas na aplicação como: perfil de liderança, índice de felicidade e tarefas.

- Grupo: O model do grupo possui informações que são comuns entre participantes de um mesmo time. Nesse sentido, tem-se o nome do grupo, o tutor responsável, os integrantes que compõem o grupo e a média de felicidade do grupo que será calculada a partir da média de cada integrante.

- Tutor: Para os tutores, os dados importantes são o nome, o país e uma foto para compor o perfil dele. Bem como, para que haja uma conexão entre os dados, deve-se saber também o grupo ao qual ele estará tutorando durante o jogo.

Essas entidades se relacionam ao passo que cada User será integrante de um Grupo e cada grupo terá um Tutor. Logo, esses dados irão se relacionar para que haja uma organização de informações em que o Grupo reuna os Users e o Tutor correspondente, mas ao mesmo tempo cada User e Tutor tenha suas próprias informações.

### Controladores (Controllers):

Para fazer as interações entre os modelos e a visão do site, fez-se necessária a criação de 5 controladores, em que cada controlador será responsável por algumas ações (methods). Os controller criados, com suas respectivas relações e responsabilidades, foram:

- Users: Esse controlador fará a interação entre o modelo User e as Views de cada tela do site. Sendo assim, para a tela de Perfil de Integrante, o controlador irá procurar as informações do integrante da equipe correspondente no Model User. Do mesmo modo, para o Login o controller irá procurar as informações do usuário no model User. Igualmente, na Tela Inicial, o controller procurará as informações do usuário, como o grupo que ele faz parte, para que os integrantes sejam exibidos corretamente no sidebar. Bem como, o controller User irá gravar as informações adicionadas no forms do Meu Perfil para atualizar o Model de User. Bem como, no que tange preencher o Meu Perfil e fazer Login, o controller User também irá interagir com o model Tutor.

- Medidor de Felicidade: Esse controller irá gravar as informações que forem inseridas no forms da view de Tela Inicial tanto no model de User como também no de Grupo. Para o model de Grupo, essa informação terá também que ser calculada, pois esse armazenará a média de felicidade de todos os integrantes.

- Formulário: O controller Formulário irá interagir com a view Teste de Perfil, gravando as respostas, bem como, calculando o resultado que será armazenado no model de User, mais especificamente no atributo perfil de liderança.

- Tutor: Esse controller irá procurar o grupo que o tutor desejar e exibir as informações no Painel de Tutor, interagindo, portanto, com a view de Painel de Tutor e o Model de Grupo.

- Tarefas: O controller de Tarefas terá o papel de gerenciar quais tarefas aparecerão no carrossel da view Tela Inicial, podendo procurar, ou concluir uma tarefa. Essas tarefas serão armazenadas no atributo user do model User.


### Views (Views):

Nessa arquitetura MVC, o projeto foi dividido em 6 views, em que cada uma corresponde a uma tela da aplicação. As views são:

- Teste de Perfil: Nessa view terá um formulário com perguntas cuja objetivo é perfilar o candidato enquanto tipo de personalidade em um trabalho em grupo.

- Perfil de integrante: Será onde o usuário poderá encontrar um perfil de um integrante do próprio grupo, ou seja, nessa tela serão exibidas informações individuais de um User que faz parte da equipe.

- Meu perfil: Nessa view poderão ser editadas, através do forms, ou exibidas as informações do Usuário.

- Painel de Tutor: Somente o usuário Tutor terá acesso a essa view e ela será o caminho para que ele acesse os grupos e posteriormente o perfil de cada integrante do grupo.

- Login: Essa view será basicamente a tela de Login onde um forms deve ser preenchido para que o usuário tenha acesso ao site.

- Tela inicial: Essa será a primeira tela que o usuário terá acesso depois do login e nela ele poderá interagir para ter acesso a outras partes e funcionalidades, ela permitirá acesso ao perfil dos integrantes por meio do side bar, terá um form para medir a felicidade e um carrossel de tarefas.

### Infraestrutura:
Nesse projeto serão utilizados alguns componentes, sendo eles: o framework Sails.js, o banco de dados PostgreSQL, gerenciador DBeaver e o Render. Esses componentes consistem em:

- Sails.js: Framework de desenvolvimento web baseado em Node.js que segue o padrão arquitetural MVC (Model-View-Controller).

- PostgreSQL: Sistema de gerenciamento de banco de dados relacional de código aberto, utilizado para armazenar dados estruturados.

- DBeaver: Ferramenta de gerenciamento de banco de dados de código aberto que oferece uma interface gráfica intuitiva e poderosa para interagir com diversos bancos de dados relacionais e NoSQL.

- Render: Plataforma de hospedagem em nuvem que oferece serviços de hospedagem para aplicativos da web e bancos de dados.

Com base nisso, pode-se relacionar que a fim de facilitar a organização da infraestrutura da aplicação web, será utilizado o framework Sails.js que permite a implementação do padrão MVC no sistema. Como banco de dados, tem se o sistema de gerenciamento, PostegreSQL, uma dependência externa, e o Render como servidor para hospedar o banco de dados e a aplicação em si. Além disso, para interagir com o banco de dados, será utilizada a ferramenta DBeaver que permite executar consultas SQL.

Já a integração com a arquitetura MVC ocorre, uma vez que o Sails.js é um facilitador desse processo ao gerenciar os controladores e ao manipular a lógica entre as camadas (Model-View-Controller). Bem como, pode-se observar essa integração quando o PostgreSQL atua juntamente com o Modelo, armazenando e gerenciando os dados.

Desse modo, compreende-se que esses elementos se integram harmoniosamente para o desenvolvimento eficiente e organizado da aplicação, resultando em uma combinação facilitadora dos processos de implementação do MVC e de gerenciamento dos dados.



### Justifique as escolhas feitas e como elas impactam o projeto.
#### Implicações da Arquitetura:

A escolha desses componentes propicia diversos benefícios ao projeto. Como por exemplo, a utilização do Sails.js, com a arquitetura MVC oferece uma estrutura clara e organizada simplificando a manutenção do projeto, bem como sua escalabilidade e testabilidade.

No mesmo sentido, o sistema de gerenciamento de dados, PostgreSQL, oferece uma forma segura e eficiente de armazenamento. Bem como, o Render, possibilita a implantação, escalabilidade e gerenciamento da aplicação. Por fim, o DBeaver, permite executar consultas SQL, gerenciar, visualizar dados e realizar outras operações de administração de forma muito conveniente.

Em suma, tudo isso impacta o projeto positivamente, uma vez que garante a qualidade do mesmo. Bem como, a segurança, a integridade dos dados e agilidade no desenvolvimento do projeto são viabilizados por meio desse conjunto de componentes, assegurando a eficácia da aplicação.

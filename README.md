# Sistema de Amigo Secreto
### ADMIN
- Cadastrar o nosso amigo secreto;
- Cadastrar o Grupo;
- Cadastrar as pessoas.

### SITE
- Tela de login via CPF;
- Teka de buffer para sorteio;
- Tela de exibição do match.

### REGRAS
- A prova de idosos;
- Senha única para admin;
- O evento pode (ou não) ser agrupado;
- Login por CPF;
- Os matches não podem ficar visíveis no banco de dados;
- Todos os matches são feitos no ínicio do evento.

### 1 PLANEJAMENTO DO BANCO DE DADOS
- Cadastro de três coisas distintas: Eventos, grupos e pessoas;
- Banco de dados cruzado;
- Banco de dados relacional;
- Nomes dos dados em inglês;

Events
- id INT PK AUTO_INCREMENT;
- status BOOLEAN default=false;
- title STRING;
- description STRING;
- grouped BOOLEAN default=false.

EventGroups
- id INT PK AUTO_INCREMENT;
- id_event INT (RELACIONADO a events.id);
- name STRING.

eventPeople
- id INT PK AUTO_INCREMENT;
- id_event INT (RELACIONADO a events.id);
- id_event INT (Relacionado a eventGroups.id);
- name STRING;
- cpf STRING;
- matched STRING default="".

### 2 PLANEJAMENTO DE ROTAS
- CRUD = Create, Read, Update e Delete (Criar, ler, atualizar e deletar o evento);
- Soft delete = Não delete o registro do db, mas terá um status como false;
- O projeto tem três entidades, event, groups e people. Sendo que cada um terá seu CRUD;
- /admin = add em tudo que for necessário.

Rota para Events
- (Read) GET /admin/events = todos os eventos;
- (Read) GET /admin/events/:id = listar um evento único. Os dados de um evento só;
- (Create) POST /admin/events = criar um evento novo;
- (Update) PUT /admin/events/:id = alteração de um evento;
- DELETE /admin/events/:id = deletar um evento.

Rota para Groups
- Um grupo faz parte de um evento
- GET /admin/events/:id_event/groups = estou querendo os grupos do evento;
- GET /admin/events/:id_event/groups/:id = dados de um grupo especifico;
- POST /admin/events/:id_event/groups = criar grupos diferentes em um evento especifico;
- PUT /admin/events/:id_event/groups/:id = identifico quem eu quero alterar. Aqui eu consigo alterar as informações de um grupo especifico;
- DELETE /admin/events/:id_event/groups/:id 

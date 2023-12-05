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

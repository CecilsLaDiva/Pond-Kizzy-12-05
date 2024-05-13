Feito com base no artefato do meu projeto! Mas tomei cuidado pra n ficar igual! Obrigada pela correção.



Markdown:

Entidade:

user: Armazenamento de dados do usuário. Todos os atributos dessa entidade serão inseridos no banco de dados no ato de cadastro na plataforma.

Atributos:

- *id*: Chave de identificação dos dados. Utilizada como chave primária para consultas ao banco. Esse atributo será chave estrangeira nas entidades student (1:1), feedback(1:n), tutor(1:1), answers(1:n), profile(1:1) e tickets(1:n);
- *firstname*: Armazena o primeiro nome do usuário. Essa informação será utilizada, principalmente, na tela de perfil e nas telas de avaliação (autoavaliação, avaliação de pares e feedback);
- *lastname*: Armazena o último nome do usuário, para fins de identificação. Será impresso na área de boas-vindas da tela de perfil.
- *email*: Armazena o email do usuário, necessário para fazer login na página.
- *password*: Armazena a senha de acesso ao usuário, sendo, também, necessária para fazer login.
- *type*: Armazena o tipo de usuário, se ele é tutor ou estudante. A depender da resposta, verifica o tipo de acesso ao site.

Entidade:

student: Entidade utilizada para guardar os dados do usuário identificado como estudante, permitindo a obtenção de algumas informações sobre ele além daquelas que já foram declaradas no cadastro.
 
Atributos:

- *id*: Chave de identificação dos dados. Utilizada como chave primária para consultas ao banco. Esse atributo será chave estrangeira nas entidades student_team(n:1), feedback(1:1) e tickets(1:n).
- *birthday*: Armazena a data de nascimento do estudante, apenas para fins de cadastro.
- *phonenumber*: Armazena o telefone do estudante, apenas para fins de cadastro.
- *nationality*: Armazena a nacionalidade do estudante. Essa informação será mostrada na tela de time, que tem como principal funcionalidade apresentar ao usuário os seus teammates.
- *nationality2*: Armazena a segunda nacionalidade de um usuário, caso ele possua uma, sendo usada apenas para fins de cadastro.
- *id_user*: Chave estrangeira oriunda da entidade "user", esse atributo retorna o id do usuário, sendo usado para relacionar as duas entidades ("user" e "student"), permitindo a criação de uma usuário estudante. Aqui, a relação de cardinalidade de id_user e student é de um para um, ou seja, cada id de usuário se relaciona a apenas um estudante.
- *id_education*: Chave estrangeira oriunda da entidade "education", esse atributo retorna o id da instituição educacional do estudante, permitindo a obtenção de informações sobre a universidade na qual ele estuda. Aqui, a relação de cardinalidade de id_education e student é de um para muitos, visto que cada instituição educacional pode ter mais de um aluno participando do jogo.

Entidade:

tutor: Entidade utilizada para guardar os dados do usuário identificado como tutor, permitindo a ele acesso a uma tela diferente da dos estudantes, visto que ele precisa acessar mais de um time.
 
Atributos:

- *id*: Chave de identificação dos dados. Utilizada como chave primária para consultas ao banco. Esse atributo será chave estrangeira na entidade team(1:n).
- *id_user*: Chave estrangeira oriunda da entidade "user", esse atributo retorna o id do usuário, sendo usado para relacionar as duas entidades ("user" e "tutor"), permitindo a criação de uma usuário tutor. Aqui, a relação de cardinalidade de id_user e tutor é de um para um, ou seja, cada id de usuário se relaciona a apenas um tutor.
- *id_education*: Chave estrangeira oriunda da entidade "education", esse atributo retorna o id da instituição educacional do tutor, permitindo a obtenção de informações sobre a universidade na qual ele leciona. Aqui, a relação de cardinalidade de id_education e tutor é de um para muitos, visto que cada instituição educacional pode ter mais de um tutor participando do jogo.
- *id_team*: Chave estrangeira oriunda da entidade "team", esse atributo é responsável por atribuir a cada tutor os seus respectivos times. Aqui, a relação de cardinalidade de id_team para tutor é de muitos para um, visto que um tutor pode ter mais de um time, mas cada time tem, necessariamente, um tutor.

Entidade:

education: Entidade utilizada para guardar os dados educacionais dos participantes do jogo, permitindo uma organização melhor deles e um melhor acesso a essas informações no banco de dados.
 
Atributos:

- *id*: Chave de identificação dos dados. Utilizada como chave primária para consultas ao banco. Nesse caso, será chave estrangeira nas entidades tutor(1:1) e student(1:1).
- *university*: Armazena o nome da universidade participante do jogo, informação essa que será mostrada aos usuários na tela de time, a fim de que eles saibam onde os seus teammates estudam.
- *country*: Armazena o nome do país no qual se localiza a universidade em questão, informação essa que também será mostrada aos usuários na tela de perfil de cada membro do seu grupo, junto da informação com o nome da universidade.
- *educationName*: Armazena o nome do curso que o aluno faz, informação que também será mostrada na tela de perfil de cada membro do time, junto das demais informações educacionais.
- *educationLevel*: Armazena o nível da graduação (major, minnor, graduação, pós-graduação, etc), informação que também será mostrada no perfil de cada membro do time.

Entidade:

team: Entidade utilizada para organizar a separação dos times participantes do jogo, permitindo a separação dos alunos em times e a ligação dos tutores aos seus respectivos times.
 
Atributos:

- *id*: Chave de identificação dos dados. Utilizada como chave primária para consultas ao banco. Nesse caso, será utilizada como chave estrangeira nas entidades student_team(1:n) e tutor(n:1).
- *teamName*: Armazena o nome do time, a ser exibido na tela de time da aplicação.
- *id_tutor*: Chave estrangeira oriunda da entidade tutor, esse atributo é responsável por atribuir um tutor ao time. Aqui, a relação de cardinalidade de tutor para team é de um para muitos, visto que um tutor pode ter mais de um time.
- *id_education*: Chave estrangeira oriunda da entidade education, esse atributo é responsável por atribuir um time a uma instituição educacional. Aqui, a relação de cardinalidade de team para education é de um para muitos, visto que cada instituição educacional pode ter mais de um time.

Entidade:

student_team: Entidade utilizada para registrar a relação entre estudantes e seus times, permitindo, assim, a organização dos usuários por time e a exibição correta de seus perfis.
 
Atributos:

- *id*: Chave de identificação dos dados. Utilizada como chave primária para consultas ao banco.
- *id_student*: Chave estrangeira oriunda da entidade student, esse atributo é responsável por atribuir o estudante ao time. Aqui, a relação de cardinalidade de student para student_team é de um para muitos, visto que um estudante pode estar em vários times.
- *id_team*: Chave estrangeira oriunda da entidade team, esse atributo é responsável por atribuir um time a um estudante. Aqui, a relação de cardinalidade de team para student_team é de um para muitos, visto que um time pode ter vários alunos.
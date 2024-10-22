# Descrição do desafio módulo 3 – Processamento de Dados Simplificado com Power BI

## Diretrizes para transformação dos dados

### Verifique os cabeçalhos e tipos de dados

- Verificado todos os cabeçalhos e tipos de dados de todas as tabelas.

- Employee
  - Alterar o nome da coluna Ssn para Codigo;
  - Excluir a coluna Minit;
  - Alterar o nome da coluna Bdate para Data_Nascimento;
  - Alterar a coluna Sex para Sexo;
  - Alterae a coluna Salary para Salario;
  - Alterar a coluna Super_ssn para Codigo_Superior;
  - Alterar a coluna Dno para id_departamento;
  - Excluir as demais colunas.
- Departament
  - Alterar o nome da coluna Dname para Descricao;
  - Alterar o nome da coluna Dnumber para id_departamento e reordenar para ficar na primeira coluna;
  - Alterar o nome da coluna Mgr_ssn para id_responsavel;
  - Alterar o nome da coluna Mgr_start_date para Data_inicio;
  - Alterar o nome da coluna Dept_create_date para Data_criacao;
  - Excluir as demais colunas.
- dependent
  - Alterar o nome da coluna Essn para Codigo;
  - Alterar o nome da coluna Dependent_name para Nome_dependente;
  - Alterar a coluna Sex para Sexo;
  - Alterar o nome da coluna Bdate para Data_Nascimento;
  - Alterar o nome da coluna Relationship para Grau_Parentesco;
  - Excluir as demais colunas.
- dept_locations
  - Alterar o nome da coluna Dnumber para id_departamento;
  - Alterar o nome da coluna Dlocation para Localizacao;
  - Excluir as demais colunas.
- project
  - Alterar o nome da coluna Pname para Projeto;
  - Alterar o nome da coluna Pnumber para id_projeto e reordenar para ficar na primeira coluna;
  - Alterar o nome da coluna Plocation para Localizacao;
  - Alterar o nome da coluna Dnum para id_departamento;
- project
  - Alterar o nome da coluna Essn para Codigo;
  - Alterar o nome da coluna Pname para Projeto;
  - Alterar o nome da coluna Pno para id_projeto

### Modifique os valores monetários para o tipo double preciso

- Employee
- Alterado oo Salario para número decimal fixo

### Verifique a existência dos nulos e analise a remoção

- James Borg é o único registro que está com a informação de gerente nulo. Provavelmente, ele é o presidente da empresa.

### Os employees com nulos em Super_ssn podem ser os gerentes- Verifique se há algum colaborador sem gerente

- Sim, existe colaborador sem gerente (James Borg)

### Verifique se há algum departamento sem gerente

- Todos os departamentos possuem responsáveis

### Se houver departamento sem gerente, suponha que você possui os dados e preencha as lacunas

- Não se aplica

### Verifique o número de horas dos projetos

- Mesclar consulta com employee para incluir o nome completo e o departamento a que pertence;
- Mesclar consulta com project para incluir o Projeto e Departamento_Localizacao.

- Total de horas dos projetos: 275 horas

  - Computerization Administration-Stafford 55,00
  - Newbenefits Administration-Stafford 55,00
  - ProductX Research-Bellaire 52,50
  - ProductY Research-Sugarland 37,50
  - ProductZ Research-Houston 50,00
  - Reorganization Headquarters-Houston 25,00

### Separar colunas complexas

- Employee
  - Dividir a coluna Address para Complemento_endereço, Endereço, Cidade e Estado;

### Mesclar consultas employee e departament para criar uma tabela employee com o nome dos departamentos associados aos colaboradores- A mescla terá como base a tabela employee- Fique atento, essa informação influencia no tipo de junção

- Criada a tabela (employee Department);

### Realize a junção dos colaboradores e respectivos nomes dos gerentes - Isso pode ser feito com consulta SQL ou pela mescla de tabelas com Power BI- Caso utilize SQL, especifique no README a query utilizada no processo.

- Efetuado com mescla no powerBI.

### Mescle as colunas de Nome e Sobrenome para ter apenas uma coluna definindo os nomes dos colaboradores

- Employee
  - Concatenar as colunas Fname e Lname e alterar o nome da coluna para "Nome_Completo";
  - Excluir as colunas Fname e Lname;

### Mescle os nomes de departamentos e localização- Isso fará que cada combinação departamento-local seja único- Isso irá auxiliar na criação do modelo estrela em um módulo futuro.

- dept_locations
  - Criada a coluna Departamento-Local após a mescla dos campos Departamento e Localizacao (departamento_local);
  - Criado índice a partir do campo Departamento-Local (id_departamento_local)
- project
  - Mesclar colunas Descricao e Localizacao para criar a coluna departamento_local;
  - Mesclar consulta na tabela dept_locations para incluir o campo id_departamento_local
  - Excluir as colunas Localizacao e Departamento
- works_on
  - mesclar consulta com employee pra criar a Nome_Completo;
  - mesclar consulta com projet para criar as colunas Projeto e departamento_local;

### Explique por que, neste caso supracitado, podemos apenas utilizar o mesclar e não o atribuir.

- Mesclar é usado para combinar dados de diferentes fontes.
- Atribuir é usado para mapear ou converter valores dentro de uma mesma fonte de dados.

### Agrupe os dados a fim de saber quantos colaboradores existem por gerente

- Wong: 3 colaboradores
- Borg: 2 colaboradores
- Wallace: 2 colaboradores

obs.: 1 colaborador está sem gerente

### Elimine as colunas desnecessárias, que não serão usadas no relatório, de cada tabela

- Colunas eliminadas.

### Considerações:

- De acordo com as informações dispobilizadas, entendo que:
  - O colaborador pertence a um departamento, porém
  - O colaborador pode participar de projetos em várias localidades independente do local onde está lotado;

Documentação do Projeto de Pacotes de Banco de Dados

Este projeto utiliza pacotes em PL/SQL para a gestão de uma aplicação acadêmica. Ele inclui procedimentos, funções e cursores organizados em três pacotes: PKG_ALUNO, PKG_DISCIPLINA e PKG_PROFESSOR. Abaixo, segue a explicação detalhada das funcionalidades implementadas e suas respectivas tabelas de suporte.

Estrutura do Projeto

1. PKG_ALUNO

Este pacote gerencia as operações relacionadas aos alunos.

1.1. Procedure: Exclusão de Aluno

Descrição: Remove um aluno da tabela aluno com base no id_aluno fornecido.

Uso: excluir_aluno(p_id_aluno IN NUMBER)

Tabelas Envolvidas:

aluno: Contém os dados dos alunos.

Ação: Apaga o registro do aluno indicado.

Tratamento de Erros:

Notifica quando o aluno não é encontrado.

Realiza ROLLBACK em caso de erro inesperado.

1.2. Cursor: Listagem de Alunos Maiores de 18 Anos

Descrição: Lista todos os alunos cuja data de nascimento indica idade superior a 18 anos.

Uso: listar_alunos_maiores_de_18()

Tabelas Envolvidas:

aluno: Consulta a idade de cada aluno com base na data de nascimento.

1.3. Cursor: Listagem de Alunos por Curso

Descrição: Lista os alunos matriculados em um curso específico.

Uso: listar_alunos_por_curso(p_id_curso NUMBER)

Tabelas Envolvidas:

aluno: Armazena os dados dos alunos.

matricula: Relaciona alunos com disciplinas.

disciplina: Relaciona disciplinas aos cursos.

2. PKG_DISCIPLINA

Este pacote gerencia as disciplinas cadastradas no sistema.

2.1. Procedure: Cadastro de Disciplina

Descrição: Insere uma nova disciplina no banco de dados.

Uso: cadastrar_disciplina(p_nome IN VARCHAR2, p_descricao IN CLOB, p_carga_horaria IN NUMBER)

Tabelas Envolvidas:

disciplina: Contém informações sobre as disciplinas oferecidas.

Ação: Adiciona uma nova disciplina com os dados fornecidos.

2.2. Cursor: Total de Alunos por Disciplina

Descrição: Lista o número de alunos matriculados em disciplinas com mais de 10 alunos.

Uso: listar_total_alunos_por_disciplina()

Tabelas Envolvidas:

disciplina: Contém informações básicas sobre disciplinas.

matricula: Armazena os dados de matrícula de alunos em disciplinas.

2.3. Cursor: Média de Idade por Disciplina

Descrição: Calcula a média de idade dos alunos matriculados em uma disciplina específica.

Uso: calcular_media_idade_por_disciplina(p_id_disciplina IN NUMBER)

Tabelas Envolvidas:

aluno: Proporciona os dados de nascimento para cálculo da idade.

matricula: Relaciona alunos com disciplinas.

2.4. Procedure: Listar Alunos de uma Disciplina

Descrição: Lista todos os alunos matriculados em uma disciplina específica.

Uso: listar_alunos_por_disciplina(p_id_disciplina IN NUMBER)

Tabelas Envolvidas:

aluno: Contém informações dos alunos.

matricula: Relaciona alunos às disciplinas.

3. PKG_PROFESSOR

Este pacote gerencia os dados e as operações relacionadas aos professores.

3.1. Cursor: Total de Turmas por Professor

Descrição: Lista os professores com mais de uma turma associada.

Uso: listar_professores_com_mais_de_uma_turma()

Tabelas Envolvidas:

professor: Contém os dados dos professores.

turma: Relaciona professores às turmas.

3.2. Function: Total de Turmas de um Professor

Descrição: Calcula o número de turmas associadas a um professor específico.

Uso: total_turmas_professor(p_id_professor IN NUMBER) RETURN NUMBER

Tabelas Envolvidas:

turma: Consulta as turmas atribuídas ao professor fornecido.

3.3. Function: Professor de uma Disciplina

Descrição: Retorna o nome do professor associado a uma disciplina específica.

Uso: professor_disciplina(p_id_disciplina IN NUMBER) RETURN VARCHAR2

Tabelas Envolvidas:

professor: Contém os dados dos professores.

turma: Relaciona disciplinas aos professores responsáveis.

Como Executar

Pré-requisitos:

Banco de dados Oracle configurado e acessível.

Tabelas criadas conforme o esquema acima.

Execução:

Copie os scripts para um ambiente SQL Developer ou similar.

Execute cada comando para criar os pacotes e suas respectivas procedures, cursores e funções.

Testes:

Para validar cada funcionalidade, use chamadas explícitas aos procedimentos ou funções, fornecendo os parâmetros necessários.

Estrutura das Tabelas

Tabela: aluno

Colunas:

id_aluno: Identificador único do aluno.

nome: Nome completo do aluno.

data_nascimento: Data de nascimento do aluno.

Tabela: disciplina

Colunas:

id_disciplina: Identificador único da disciplina.

nome: Nome da disciplina.

descricao: Descrição detalhada.

carga_horaria: Carga horária total.

Tabela: professor

Colunas:

id_professor: Identificador único do professor.

nome: Nome do professor.

Tabela: turma

Colunas:

id_turma: Identificador único da turma.

id_professor: Referência ao professor responsável.

Tabela: matricula

Colunas:

id_aluno: Referência ao aluno matriculado.

id_disciplina: Referência à disciplina matriculada.

Considerações Finais

Este projeto foi desenvolvido para ilustrar como pacotes PL/SQL podem ser utilizados para organizar e automatizar tarefas em um banco de dados acadêmico. 

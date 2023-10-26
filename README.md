# AulaBancoDados_DP

* EXERCICIO 1 * Modelagem Conceitual: Entidade-relacionamento 
O hospital necessita de um sistema para sua área clínica que ajude a controlar consultas realizadas. Os médicos podem ser generalistas, especialistas ou residentes e têm seus dados pessoais cadastrados em planilhas digitais. Cada médico pode ter uma ou mais especialidades, que podem ser pediatria, clínica geral, gastroenterologia e dermatologia. Alguns registros antigos ainda estão em formulário de papel, mas será necessário incluir esses dados no novo sistema.

Os pacientes também precisam de cadastro, contendo dados pessoais (nome, data de nascimento, endereço, telefone e e-mail), documentos (CPF e RG) e convênio. Para cada convênio, são registrados nome, CNPJ e tempo de carência.

As consultas também têm sido registradas em planilhas, com data e hora de realização, médico responsável, paciente, valor da consulta ou nome do convênio, com o número da carteira. Também é necessário indicar na consulta qual a especialidade buscada pelo paciente.

Deseja-se ainda informatizar a receita do médico, de maneira que, no encerramento da consulta, ele possa registrar os medicamentos receitados, a quantidade e as instruções de uso. A partir disso, espera-se que o sistema imprima um relatório da receita ao paciente ou permita sua visualização via internet.

RESPOSTAS:

![image](https://github.com/FabinhoStriker32/AulaBancoDados_DP/assets/146888542/6ca36c86-a588-476a-8dfc-30aa3e4f6fea)

* EXERCICIO 2 * Os Segredos do Hospital

E não era exatamente aquilo! 


Após a primeira versão do projeto de banco de dados para o sistema hospitalar, notou-se a necessidade de expansão das funcionalidades, incluindo alguns requisitos essenciais a essa versão do software. As funcionalidades em questão são para o controle na internação de pacientes. Será necessário expandir o Modelo ER desenvolvido e montar o banco de dados, criando as tabelas para o início dos testes.

No hospital, as internações têm sido registradas por meio de formulários eletrônicos que gravam os dados em arquivos. 

Para cada internação, são anotadas a data de entrada, a data prevista de alta e a data efetiva de alta, além da descrição textual dos procedimentos a serem realizados. 

As internações precisam ser vinculadas a quartos, com a numeração e o tipo. 

Cada tipo de quarto tem sua descrição e o seu valor diário (a princípio, o hospital trabalha com apartamentos, quartos duplos e enfermaria).

Também é necessário controlar quais profissionais de enfermaria estarão responsáveis por acompanhar o paciente durante sua internação. Para cada enfermeiro(a), é necessário nome, CPF e registro no conselho de enfermagem (CRE).

A internação, obviamente, é vinculada a um paciente – que pode se internar mais de uma vez no hospital – e a um único médico responsável.

Faça a ligação do diagrama acima ao diagrama desenvolvido na atividade antrior, construindo relacionamentos com entidades relacionadas. E eleve o seu diagrama para que já selecionando os tipos de dados que serão trabalhados e em quais situações. 

Por último, crie um script SQL para a geração do banco de dados e para instruções de montagem de cada uma das entidades/tabelas presentes no diagrama completo (considerando as entidades do diagrama da atividade anterior e as novas entidades propostas no diagrama acima). Também crie tabelas para relacionamentos quando necessário. Aplique colunas e chaves primárias e estrangeiras.
Use ferramentas, como ERPlus, Lucidchart, draw.io (via web) e MySQL Workbench, ou mesmo um editor de imagens para o diagrama. 

Você pode utilizar o MySQL Workbench ou o DBdiagram.io para montar os scripts SQL.

Importante: desse modelo já devemos gerar a etapa lógica da nossa modelagem!

RESPOSTAS:

![image](https://github.com/FabinhoStriker32/AulaBancoDados_DP/assets/146888542/95d4efc5-a376-458b-9747-e273d9e4d387)


* EXERCICIO 3 * O Prisioneiro dos Dados 

De que serve o banco sem dados? 

Então vamos alimentar o banco! 

Com o banco de dados para o sistema hospitalar completamente montado, é necessário incluir dados para realizar os devidos testes e validar sua viabilidade quanto ao sistema. Nesta etapa, também é importante realizar a separação de alguns scripts iniciais para o banco, com os dados que serão necessários a um povoamento inicial do sistema.

ogando nas regras que você criou: 
Crie scripts de povoamento das tabelas desenvolvidas na atividade anterior
Observe as seguintes atividades: 
Inclua ao menos dez médicos de diferentes especialidades.

Ao menos sete especialidades (considere a afirmação de que “entre as especialidades há pediatria, clínica geral, gastrenterologia e dermatologia”).

Inclua ao menos 15 pacientes.

Registre 20 consultas de diferentes pacientes e diferentes médicos (alguns pacientes realizam mais que uma consulta). As consultas devem ter ocorrido entre 01/01/2015 e 01/01/2022. Ao menos dez consultas devem ter receituário com dois ou mais medicamentos.

Inclua ao menos quatro convênios médicos, associe ao menos cinco pacientes e cinco consultas.

Criar entidade de relacionamento entre médico e especialidade. 

Criar Entidade de Relacionamento entre internação e enfermeiro. 

Arrumar a chave estrangeira do relacionamento entre convênio e médico.

Criar entidade entre internação e enfermeiro.

Colocar chaves estrangeira dentro da internação (Chaves Médico e Paciente).

Registre ao menos sete internações. Pelo menos dois pacientes devem ter se internado mais de uma vez. Ao menos três quartos devem ser cadastrados. As internações devem ter ocorrido entre 01/01/2015 e 01/01/2022.

Considerando que “a princípio o hospital trabalha com apartamentos, quartos duplos e enfermaria”, inclua ao menos esses três tipos com valores diferentes.

Inclua dados de dez profissionais de enfermaria. Associe cada internação a ao menos dois enfermeiros.

Os dados de tipo de quarto, convênio e especialidade são essenciais para a operação do sistema e, portanto, devem ser povoados assim que o sistema for instalado.

RESPOSTAS:

O script se encontra no repositório, "Untitled (1).sql"

* EXERCICIO 4 * A Ordem do Alterar.

Não... Não acabou... 

Um banco de dados pode sofrer alterações ao longo da sua concepção e do seu desenvolvimento. Nesse momento devemos nos preparar para atualizar nossas estratégias. 

No banco que já foi criado para o Projeto do Hospital, foi realizado algumas alterações nas tabelas e nos dados.

RESPOSTAS:

Foi criado um script que adiciona uma coluna “em_atividade” para os médicos, indicando se ele ainda está atuando no hospital ou não.
Também foi criado um script para atualizar ao menos dois médicos como inativos e os demais em atividade.
ALTER TABLE medico ADD COLUMN em_atividade VARCHAR(20);
UPDATE medico SET em_atividade = 'Inativo' WHERE id_medico = 1;
...
UPDATE medico SET em_atividade = 'Em atividade' WHERE id_medico = 10;
ALTER TABLE medico ALTER COLUMN em_atividade SET DEFAULT 'Em atividade';

* EXERCICIO 5 * As Relíquias dos Dados.

  Uma vez que o banco estiver bem estruturado e desenhado, é possível realizar testes, simulando relatórios ou telas que o sistema possa necessitar. A tarefa consiste em criar consultas que levem aos resultados esperados.

  Todos os dados e o valor médio das consultas do ano de 2020 e das que foram feitas sob convênio.
  
SELECT * FROM consulta WHERE YEAR(data_consulta) = 2020 OR id_convenio = 1;
SELECT AVG(valor) FROM consulta WHERE YEAR(data) = 2020 OR convenio = 1;

Todos os dados das internações que tiveram data de alta maior que a data prevista para a alta.

SELECT * FROM internacao WHERE data_alta > data_prev_alta;
Receituário completo da primeira consulta registrada com receituário associado.
SELECT * FROM receita WHERE consulta_id = (SELECT MIN(id_receita) FROM consulta);

Todos os dados da consulta de maior valor e também da de menor valor (ambas as consultas não foram realizadas sob convênio).
SELECT * FROM consulta WHERE id_convenio = NULL ORDER BY valor DESC;
SELECT * FROM consulta WHERE id_convenio = NULL ORDER BY valor ASC;

Todos os dados das internações em seus respectivos quartos, calculando o total da internação a partir do valor de diária do quarto e o número de dias entre a entrada e a alta.
SELECT i.id_internacao, i.data_entrada, i.data_prev_alta, i.data_alta, i.procedimento,
       q.numero AS numero_quarto, t.valor_diaria,
       DATEDIFF(i.data_alta, i.data_entrada) AS num_dias,
       DATEDIFF(i.data_alta, i.data_entrada) * t.valor_diaria AS total_internacao
FROM internacao i
JOIN quarto q ON i.id_internacao = q.id_quarto
JOIN tipo_quarto t ON q.id_tipoquarto = t.id_tipoquarto;

Nome do paciente, data da consulta e especialidade de todas as consultas em que os pacientes eram menores de 18 anos na data da consulta e cuja especialidade não seja “pediatria”, ordenando por data de realização da consulta.
SELECT p.nome AS nome_paciente, c.data_consulta, e.nome AS especialidade
FROM consulta c
JOIN paciente p ON c.id_paciente = p.id_paciente
JOIN especialidade e ON c.especialidade_id = e.id_especialidade
WHERE TIMESTAMPDIFF(YEAR, STR_TO_DATE(p.data_nascimento, '%Y-%m-%d'), c.data_consulta) < 18
AND e.nome != 'Pediatria'
ORDER BY c.data_consulta;

Nome do paciente, nome do médico, data da internação e procedimentos das internações realizadas por médicos da especialidade “gastroenterologia”, que tenham acontecido em “enfermaria”.
SELECT p.nome AS NomePaciente, m.nome AS NomeMedico, i.data_internacao, i.procedimentos
FROM internacao i
JOIN medico m ON i.id_medico = m.id_medico
JOIN paciente p ON i.id_paciente = p.id_paciente
JOIN especialidade_medico em ON m.id_medico = em.id_medico
JOIN especialidade e ON em.id_especialidade = e.id_especialidade
WHERE e.nome_especialidade = 'gastroenterologia'
  AND i.local_internacao = 'enfermaria'

Os nomes dos médicos, seus CRMs e a quantidade de consultas que cada um realizou.
SELECT m.nome AS NomeMedico, m.CRM, COUNT(c.id_consulta) AS QuantidadeConsultas
FROM medico m
LEFT JOIN consulta c ON m.id_medico = c.id_medico
GROUP BY m.id_medico
Todos os médicos que tenham "Gabriel" no nome.
SELECT * FROM medico WHERE nome = "Gabriel";

Os nomes, CREs e número de internações de enfermeiros que participaram de mais de uma internação.
SELECT e.nome AS NomeEnfermeiro, e.crm AS CRM, COUNT(i.id_internacao) AS NumeroInternacoes
FROM enfermeiro e
JOIN participacao p ON e.id_enfermeiro = p.id_enfermeiro
JOIN internacao i ON p.id_internacao = i.id_internacao
GROUP BY e.nome, e.crm
HAVING COUNT(i.id_internacao) > 1


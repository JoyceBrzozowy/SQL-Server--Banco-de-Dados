# SQL-Server

## Management Studio  
```sql
SELECT * FROM [dbo].[MSreplication_options]
Executar
Consulta
SELECT * FROM [dbo].[spt_fallback_db]
Forçar um erro, editando o nome na tabela
SELECT * FROM [dbo].[MSreplication_optionsXXXX]
```

Executar


Criar banco de dados

Nova Consulta

CREATE DATABASE SUCOS_VENDAS_01

Execute o comando


Localização do arquivo físico, política de crescimento, nome do arquivo de log

CREATE DATABASE SALES_VENDAS_02
ON ( NAME = SUCO_VENDAS_DAT,  
    FILENAME = 'C:\TEMP\DATA\SALES_VENDAS_02.mdf',  
    SIZE = 10,  
    MAXSIZE = 50,  
    FILEGROWTH = 5 )  
LOG ON  
( NAME = SUCOS_VENDAS_LOG,  
    FILENAME = 'C:\TEMP\DATA\SALES_VENDAS_02.ldf',  
    SIZE = 5MB,  
    MAXSIZE = 25MB,  
    FILEGROWTH = 5MB )

Antes de executar, certifique-se que o diretório C:\TEMP\DATA\ existe. Se não, crie-o.

Apagando um banco de dados

DROP DATABASE SUCOS_VENDAS_01

Crie uma nova consulta e digite:

DROP DATABASE SUCOS_VENDAS_01

Depois execute-a.

Você pode excluir o banco de dados apenas com o mouse. Clique com o botão da direita do mouse sobre o banco SUCOS_VENDAS_02 e selecione a opção Excluir:
Uma caixa de diálogo é apresentada.
Se você acessar o botão Script, com a opção Ação de script para uma nova janela de consulta, você terá o comando de exclusão do banco de dados.
 Executando este comando, o banco SUCOS_VENDAS_02 é excluído.

Qual a diferença entre os campos string com e sem N na frente do seu tipo?
N significa Unicode. Permite o armazenamento de todos os caracteres.

Digamos que eu tenha um sistema de dados de uma multinacional que controla chamados de suporte. Um chamado é aberto no Japão e resolvido pela equipe da Alemanha. Que tipo de campo data é o melhor para que possamos fazer cálculos corretos para obter o tempo de resposta dos chamados?

Datetimeoffset
Temos que levar em conta o fuso horário da data para tratarmos de datas em diferentes partes do mundo.

Meu amigo é astrônomo. Ele quer criar um telescópio que conte estrelas. O equipamento vai estar ligado a um banco de dados SQL Server. Que tipo de dados numérico seria o melhor para contar o número de estrelas?

BigInt
Claro que o BigInt não é infinito, mas ele poderia suportar o contador de estrelas por um tempo considerável. Logo esta seria a melhor opção.


Criando a primeira tabela
1) Acesse o Management Studio.

2) Crie a tabela de cliente, digitando o comando abaixo:

CREATE TABLE [TABELA DE CLIENTES](
    [CPF] [VARCHAR] (11) ,
    [NOME] [VARCHAR] (100) ,
    [ENDERECO 1] [VARCHAR] (150) ,
    [ENDERECO 2] [VARCHAR] (150) ,
    [BAIRRO] [VARCHAR] (50) ,
    [CIDADE] [VARCHAR] (50) ,
    [ESTADO] [VARCHAR] (2) ,
    [CEP] [VARCHAR] (8) ,
    [DATA DE NASCIMENTO] [DATE],
    [IDADE] [SMALLINT],
    [SEXO] [VARCHAR] (1) ,
    [LIMITE DE CREDITO] [MONEY] ,
    [VOLUME DE COMPRA] [FLOAT] ,
    [PRIMEIRA COMPRA] [BIT]
)


Criando uma tabela através de assistente
4) Crie agora uma outra tabela, porém usando o Assistente do Management Studio. Clique com o botão da direita do mouse sobre o nome do banco de dados e selecione Novo --> Tabela:

5) No grid, preencha com os dados da nova tabela, conforme mostrado abaixo:

[CODIGO DO PRODUTO] Varchar(10)
[NOME DO PRODUTO] Varchar(50)
[EMBALAGEM] Varchar(20)
[TAMANHO] Varchar(10)
[SABOR] Varchar(20)
[PREÇO DE LISTA] Smallmoney]

Salvar e depois inclua o nome da tabela clique em ok, e depois com o botão direito do mouse sobre as tabela selecione a opção atualizar.

Clique com o botão da direita do mouse sobre a tabela de clientes e selecione Script de Tabela como --> CREATE Para --> Janela do Editor da Nova Consulta:

Você terá: 

CREATE TABLE [TABELA DE CLIENTES](
    [CPF] [VARCHAR] (11) ,
    [NOME] [VARCHAR] (100) ,
    [ENDERECO 1] [VARCHAR] (150) ,
    [ENDERECO 2] [VARCHAR] (150) ,
    [BAIRRO] [VARCHAR] (50) ,
    [CIDADE] [VARCHAR] (50) ,
    [ESTADO] [VARCHAR] (2) ,
    [CEP] [VARCHAR] (8) ,
    [DATA DE NASCIMENTO] [DATE],
    [IDADE] [SMALLINT],
    [SEXO] [VARCHAR] (1) ,
    [LIMITE DE CREDITO] [MONEY] ,
    [VOLUME DE COMPRA] [FLOAT] ,
    [PRIMEIRA COMPRA] [BIT]

Modifique o nome da tabela no script para TABELA DE CLIENTES.

Execute  e depois de atualizar você terá uma nova tabela.

Apagando uma tabela

Clique com o botão da direita do mouse sobre Tabela de Clientes e selecione Script de Tabela como --> CREATE Para --> Janela do Editor da Nova Consulta:
 Edite o nome da tabela para Tabela de Clientes 3
Execute, atualize e verifique se a tabela foi criada
Apague a Tabela de Clientes 2. Para isso, crie uma nova consulta e digite o comando

DROP TABLE [dbo].[TABELA DE CLIENTES 2]

 Execute o comando, atualize as tabelas e verifique que a tabela não existe mais
 Exclua a Tabela de Clientes 3 através do assistente. Para isso, clique com o botão da direita do mouse sobre ela e escolha a opção Excluir
Abrirá uma caixa de diálogo, clique em ok e a tabela será excluída.

Incluindo dados na tabela
INSERT INTO [TABELA DE PRODUTOS]
([CODIGO DO PRODUTO], [NOME DO PRODUTO], [EMBALAGEM], [TAMANHO], [SABOR], [PREÇO DE LISTA])
VALUES
('1040107','Light - 350 ml - Melancia', 'Lata', '350 ml', 'Melancia', 4.56)
Você pode incluir vários registros. Crie uma nova consulta e digite
INSERT INTO [TABELA DE PRODUTOS]
([CODIGO DO PRODUTO], [NOME DO PRODUTO], [EMBALAGEM], [TAMANHO], [SABOR], [PREÇO DE LISTA])
VALUES
('1037797','Clean - 2 Litros - Laranja', 'PET', '2 Litros', 'Laranja', 16.01)

INSERT INTO [TABELA DE PRODUTOS]
([CODIGO DO PRODUTO], [NOME DO PRODUTO], [EMBALAGEM], [TAMANHO], [SABOR], [PREÇO DE LISTA])
VALUES
('1000889','Sabor da Montanha - 700 ml - Uva', 'Garrafa', '700 ml', 'Uva', 6.31)
Alterando registros
INSERT INTO [TABELA DE PRODUTOS]
([CODIGO DO PRODUTO], [NOME DO PRODUTO], [EMBALAGEM], [TAMANHO], [SABOR], [PREÇO DE LISTA])
VALUES
('544931', 'Frescor do Verão - 350 ml - Limão', 'PET', '350 ml','Limão',3.20)

INSERT INTO [TABELA DE PRODUTOS]
([CODIGO DO PRODUTO], [NOME DO PRODUTO], [EMBALAGEM], [TAMANHO], [SABOR], [PREÇO DE LISTA])
VALUES
('1078680', 'Frescor do Verão - 470 ml - Manga', 'Lata', '470 ml','Manga',5.18)
Altere estes dois registros novos. Para isto, crie uma nova consulta e digite:
UPDATE [TABELA DE PRODUTOS] SET 
[EMBALAGEM] = 'Lata',
[PREÇO DE LISTA] = 2.46
WHERE [CODIGO DO PRODUTO] = '544931'

UPDATE [TABELA DE PRODUTOS] SET
[EMBALAGEM] = 'Garrafa'
WHERE [CODIGO DO PRODUTO] = '1078680'
Excluindo registros
DELETE FROM [TABELA DE PRODUTOS]
WHERE [CODIGO DO PRODUTO] = '1088216'
Chave primária
INSERT INTO [TABELA DE PRODUTOS]
([CODIGO DO PRODUTO], [NOME DO PRODUTO], [EMBALAGEM], [TAMANHO], [SABOR], [PREÇO DE LISTA])
VALUES
('788975', 'Pedaços de Frutas - 1,5 Litros - Maça', 'PET', '1,5 Litros', 'Maça', 18.01)

INSERT INTO [TABELA DE PRODUTOS]
([CODIGO DO PRODUTO], [NOME DO PRODUTO], [EMBALAGEM], [TAMANHO], [SABOR], [PREÇO DE LISTA])
VALUES
('788975', 'Pedaços de Frutas - 1,5 Litros - Maça', 'PET', '1,5 Litros', 'Maça', 18.01)
Crie a chave primária para evitar que isso acima aconteça. Mas antes, exclua estes registros repetidos, digitando e executando o comando:
DELETE FROM [TABELA DE PRODUTOS] WHERE [CODIGO DO PRODUTO] = '788975'
Digite o comando de criação da chave primária. Digite:
ALTER TABLE [TABELA DE PRODUTOS]
ADD CONSTRAINT PK_PRODUTOS 
PRIMARY KEY CLUSTERED ([CODIGO DO PRODUTO])
Isto acontece por causa da propriedade NULL dos campos que estão virando chaves primárias.
23) Digite o comando abaixo:
INSERT INTO [TABELA DE PRODUTOS]
([CODIGO DO PRODUTO], [NOME DO PRODUTO], [EMBALAGEM], [TAMANHO], [PREÇO DE LISTA])
VALUES
('788975', 'Pedaços de Frutas - 1,5 Litros - Maça', 'PET', '1,5 Litros', 18.01)
Resolvendo o problema da chave primária
ALTER TABLE [TABELA DE PRODUTOS]
ALTER COLUMN {CODIGO DO PRODUTO]
VARCHAR(10) NOT NULL
Execute o comando de inclusão novamente:
INSERT INTO [TABELA DE PRODUTOS]
([CODIGO DO PRODUTO], [NOME DO PRODUTO], [EMBALAGEM], [TAMANHO], [SABOR], [PREÇO DE LISTA])
VALUES
('788975', 'Pedaços de Frutas - 1,5 Litros - Maça', 'PET', '1,5 Litros', 'Maça', 18.01)
Manipulando datas e campos lógicos
Crie uma nova consulta. Edite os comandos abaixo para criar a chave primária da tabela de clientes para o campo CPF:
ALTER TABLE [TABELA DE CLIENTES]
ALTER COLUMN [CPF]
VARCHAR(11) NOT NULL

ALTER TABLE [TABELA DE CLIENTES]
ADD CONSTRAINT PK_CLIENTES
PRIMARY KEY CLUSTERED ([CPF])
Altere o comando digitando:
INSERT INTO [dbo].[TABELA DE CLIENTES]
           ([CPF]
           ,[NOME]
           ,[ENDERECO 1]
           ,[ENDERECO 2]
           ,[BAIRRO]
           ,[CIDADE]
           ,[ESTADO]
           ,[CEP]
           ,[DATA DE NASCIMENTO]
           ,[IDADE]
           ,[SEXO]
           ,[LIMITE DE CREDITO]
           ,[VOLUME DE COMPRA]
           ,[PRIMEIRA COMPRA])
     VALUES
           ('00300000001'
           ,'João da Silva'
           ,'Rua Projetada A número 10'
           ,''
           ,'Centro'
           ,'Rio de Janeiro'
           ,'RJ'
           ,'20000000'
           ,'1990-10-25'
           ,27
           ,'M'
           ,120000.50
           ,1000
           ,1)
Consultando os dados
1) Acesse o Management Studio.
2) Abra o arquivo Incluindo dados tabela produtos e clientes.sql e execute o script. Diversos registros serão incluídos na tabela de produtos e de clientes.
3) Se você verificar a tabela de produtos, terá:

4) O mesmo para a tabela de clientes:

5) Quando listamos o conteúdo das tabelas, o SQL Server Management Studio escreveu justamente o comando para consulta de dados:

6) Se editarmos o comando acima e, no lugar de TOP 1000 você modificar para TOP 5, verá apenas 5 registros:


7) Se, no lugar dos campos, colocar um asterisco (como abaixo) verá a mesma coisa se estivesse digitado todos os campos.
SELECT * FROM [TABELA DE CLIENTES]

8) Você pode restringir as colunas a serem exibidas. Digite o comando abaixo e execute-o.
SELECT [CPF], [NOME] FROM [TABELA DE CLIENTES]

9) Você pode mudar o nome das colunas criando o que é chamado de ALIAS:
SELECT [CPF] AS IDENTIFICADOR, [NOME] AS CLIENTE 
FROM [TABELA DE CLIENTES]

10) Ou também modificar a ordem de exibição das colunas no resultado da consulta:
SELECT [NOME] AS CLIENTE, [CPF] AS IDENTIFICADOR
FROM [TABELA DE CLIENTES]

Filtrando registros
11) Para limitar o resultado da consulta, inclua uma condição, muito parecida quando você aprendeu a excluir e alterar registros de uma tabela. Digite:
SELECT * FROM [TABELA DE PRODUTOS] WHERE [CODIGO DO PRODUTO] = '1000889'
12) Você verá apenas o registro selecionado:

13) Você pode limitar a seleção usando como critério qualquer outro campo. Digite:
SELECT * FROM [TABELA DE PRODUTOS] WHERE [SABOR] = 'Uva'

14) Se você limitar para verificar somente sabores Limão, verá mais registros. Digite:
SELECT * FROM [TABELA DE PRODUTOS] WHERE [SABOR] = 'Limão'

15) E qualquer condição de WHERE vale para os comandos UPDATE e DELETE. Digite:
DELETE FROM [TABELA DE PRODUTOS] WHERE [SABOR] = 'Limão'
Você verá na mensagem de retorno que 4 registros foram afetados.
16) Se você executar novamente o comando de seleção, nada será retornado:
SELECT * FROM [TABELA DE PRODUTOS] WHERE [SABOR] = 'Limão'

Filtrando usando maior, menor, diferente
17) Você pode fazer filtros envolvendo números. Digite:
SELECT * FROM [TABELA DE PRODUTOS] WHERE [PREÇO DE LISTA] = 4.555

18) Você pode verificar os produtos que custam mais que 10. Digite:
SELECT * FROM [TABELA DE PRODUTOS] WHERE [PREÇO DE LISTA] > 10

19) Ou menores que 10:
SELECT * FROM [TABELA DE PRODUTOS] WHERE [PREÇO DE LISTA] < 10

20) Você pode usar o maior e igual, ou menor ou igual para incluir o critério de seleção no resultado:
SELECT * FROM [TABELA DE PRODUTOS] WHERE [PREÇO DE LISTA] >= 4.555

21) Você pode usar o maior e menor para condições que envolvam strings. O critério de determinar quem é maior ou menor será o de ordem alfabética:
SELECT * FROM [TABELA DE PRODUTOS] WHERE EMBALAGEM <= 'Lata'

22) Há também o critério de selecionar alguém diferente de um valor. Para isso, use o símbolo <>:
SELECT * FROM [TABELA DE PRODUTOS] WHERE [PREÇO DE LISTA] <> 4.555

Filtrando por datas
23) Você pode usar as datas como critério de seleção. O SQL Server irá usar a ordem definida no calendário para determinar quem é maior ou menor. Digite:
SELECT * FROM [TABELA DE CLIENTES] WHERE [DATA DE NASCIMENTO] = '1995-09-11'

24) Ou então:
SELECT * FROM [TABELA DE CLIENTES] WHERE [DATA DE NASCIMENTO] <= '1995-09-11'

25) Você pode usar algumas funções aplicadas à data que determinam condições sobre o dia, mês ou ano. Veja o exemplo abaixo:
SELECT * FROM [TABELA DE CLIENTES] WHERE YEAR([DATA DE NASCIMENTO]) < 1995






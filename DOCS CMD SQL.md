
# ***Documentação do Código - Criação de Banco de Dados***

Comando básico para criação e manipulação de um banco de dados com imagens ilustrativas

# **✍️ CMD `CREATE DATABASE IF NOT EXISTS`**

Descrição
---------

Este código é uma instrução SQL para criar um banco de dados chamado "db\_flashCardBar" utilizando a linguagem PHP. A cláusula "IF NOT EXISTS" verifica se o banco de dados já existe antes de criar um novo, evitando duplicações. O conjunto de caracteres (character set) utilizado é o "utf8mb4" e a colação (collation) é "utf8mb4\_unicode\_ci", que são adequados para suportar caracteres Unicode, incluindo emojis e outros caracteres multibyte.

Código
------

sql

```sql
CREATE DATABASE IF NOT EXISTS db_flashCardBar CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

Detalhes
--------

*   `CREATE DATABASE`: É uma instrução SQL utilizada para criar um novo banco de dados no sistema de gerenciamento de banco de dados (SGBD).
*   `IF NOT EXISTS`: É uma cláusula condicional que verifica se o banco de dados já existe antes de criar um novo. Se o banco de dados já existir, a instrução é ignorada, evitando duplicações.
*   `db_flashCardBar`: É o nome do banco de dados que está sendo criado. Você pode substituir esse nome pelo nome que desejar para o seu banco de dados.
*   `CHARACTER SET utf8mb4`: É uma especificação do conjunto de caracteres que o banco de dados deve suportar. "utf8mb4" é um conjunto de caracteres que suporta todos os caracteres Unicode, incluindo emojis e outros caracteres multibyte.
*   `COLLATE utf8mb4_unicode_ci`: É uma especificação da collation, ou seja, a forma como os caracteres são comparados e ordenados. "utf8mb4\_unicode\_ci" é uma collation que trata os caracteres como case-insensitive (não diferencia maiúsculas de minúsculas) e suporta caracteres Unicode.

Referências
-----------

*   [Documentação oficial do MySQL - CREATE DATABASE](https://dev.mysql.com/doc/refman/8.0/en/create-database.html)
*   [Documentação oficial do MySQL - Character Sets and Collations](https://dev.mysql.com/doc/refman/8.0/en/charset-general.html)


# **✍️ CMD `USE`**

Descrição
---------

Este código é uma instrução SQL para selecionar o banco de dados "db\_flashCardBar" como o banco de dados atual a ser utilizado em uma aplicação PHP. A instrução "USE" é usada para especificar o banco de dados com o qual as próximas instruções SQL irão interagir.

Código
------

sql

```sql
USE db_flashCardBar;
```

Detalhes
--------

*   `USE`: É uma instrução SQL utilizada para selecionar o banco de dados que será utilizado como o banco de dados ativo. Todas as próximas instruções SQL executadas após essa instrução irão operar no banco de dados especificado.
*   `db_flashCardBar`: É o nome do banco de dados que será selecionado como o banco de dados atual. Você pode substituir esse nome pelo nome do banco de dados que você deseja utilizar em sua aplicação.

Referências
-----------

*   [Documentação oficial do MySQL - USE](https://dev.mysql.com/doc/refman/8.0/en/use.html)


# **✍️ CMD `CREATE TABLE IF NOT EXISTS`**

Descrição
---------

Este código é uma instrução SQL para criar uma tabela chamada "tb\_baralhos" em um banco de dados utilizando a linguagem PHP. A tabela é projetada para armazenar informações sobre baralhos de cartas, com colunas para o identificador do baralho (idBar), o nome do baralho (c\_bar), a data de criação do baralho (c\_dt), a data de criação do registro (c\_dtc), e a data de modificação do registro (c\_dtMod). A instrução também inclui definições de chave primária (PRIMARY KEY), tipo de armazenamento (ENGINE), conjunto de caracteres (CHARSET) e collation (COLLATE) para a tabela.

Código
------

sql

```sql
CREATE TABLE IF NOT EXISTS tb_baralhos (
    idBar VARCHAR(255) NOT NULL,
    c_bar VARCHAR(255) NOT NULL,
    c_dt DATE NOT NULL,
    c_dtc DATE NOT NULL DEFAULT DATE(NOW()),
    c_dtMod TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    PRIMARY KEY (idBar)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci COMMENT='Tabela de usuários do sistema';
```

Detalhes
--------

*   `CREATE TABLE`: É uma instrução SQL utilizada para criar uma nova tabela no banco de dados.
*   `IF NOT EXISTS`: É uma cláusula condicional que verifica se a tabela já existe antes de criar uma nova. Se a tabela já existir, a instrução é ignorada, evitando duplicações.
*   `tb_baralhos`: É o nome da tabela que está sendo criada. Você pode substituir esse nome pelo nome que desejar para sua tabela.
*   `idBar`: É o nome da primeira coluna da tabela, que é usada para armazenar o identificador do baralho. O tipo de dado é VARCHAR com tamanho máximo de 255 caracteres, e é definido como NOT NULL, ou seja, obrigatório.
*   `c_bar`: É o nome da segunda coluna da tabela, que é usada para armazenar o nome do baralho. O tipo de dado é VARCHAR com tamanho máximo de 255 caracteres, e é definido como NOT NULL, ou seja, obrigatório.
*   `c_dt`: É o nome da terceira coluna da tabela, que é usada para armazenar a data de criação do baralho. O tipo de dado é DATE e é definido como NOT NULL, ou seja, obrigatório.
*   `c_dtc`: É o nome da quarta coluna da tabela, que é usada para armazenar a data de criação do registro. O tipo de dado é DATE e é definido como NOT NULL por padrão, mas é definido como DEFAULT DATE(NOW()), ou seja, se nenhum valor for fornecido, será automaticamente preenchido com a data atual do sistema.
*   `c_dtMod`: É o nome da quinta coluna da tabela, que é usada para armazenar a data de modificação do registro. O tipo de dado é TIMESTAMP e é definido como NOT NULL por padrão, mas é definido como DEFAULT CURRENT\_TIMESTAMP ON UPDATE CURRENT\_TIMESTAMP, ou seja, será automaticamente atualizado com a data e hora atual do sistema sempre que o registro for modificado.
*   `PRIMARY KEY`: É uma definição da chave primária da tabela, que é usada para identificar de forma única cada registro



Vantagens de usar VARCHAR:
--------------------------

1.  Economia de espaço: A coluna VARCHAR é mais eficiente em termos de espaço de armazenamento em comparação com a coluna TEXT. Isso ocorre porque o VARCHAR armazena apenas a quantidade de caracteres inseridos, enquanto a coluna TEXT reserva um espaço fixo, independentemente do número de caracteres inseridos. Portanto, quando se espera que a quantidade de texto armazenado seja variável e geralmente menor do que o espaço reservado pela coluna TEXT, o uso de VARCHAR pode economizar espaço de armazenamento no banco de dados.
    
2.  Desempenho de busca: O uso de VARCHAR pode ter um melhor desempenho em operações de busca e comparação em comparação com a coluna TEXT. Isso ocorre porque o VARCHAR armazena apenas a quantidade de caracteres inseridos, enquanto a coluna TEXT reserva um espaço fixo, independentemente do número de caracteres inseridos. Portanto, em operações de busca e comparação de texto, a coluna VARCHAR pode ser mais rápida, pois tem menos dados para percorrer.
    
3.  Flexibilidade: O uso de VARCHAR oferece mais flexibilidade em relação ao tamanho máximo dos dados armazenados. É possível especificar o tamanho máximo de caracteres permitidos em uma coluna VARCHAR, o que pode ser útil em situações onde é necessário impor restrições de tamanho máximo de texto. Por outro lado, a coluna TEXT não possui um limite de tamanho máximo específico, o que pode resultar em problemas de desempenho e armazenamento se houver a necessidade de impor restrições de tamanho de texto.
    
4.  Compatibilidade: O uso de VARCHAR é mais compatível com diferentes sistemas de gerenciamento de banco de dados (SGBDs) e tipos de bancos de dados. A coluna TEXT é geralmente específica de alguns SGBDs e pode ter comportamentos diferentes em diferentes tipos de bancos de dados. Por outro lado, o uso de VARCHAR é mais padronizado e amplamente suportado em vários SGBDs, tornando-o uma opção mais versátil em diferentes ambientes de banco de dados.
    

Conclusão
---------

Em resumo, o uso de colunas VARCHAR pode ter vantagens significativas em termos de economia de espaço, desempenho de busca, flexibilidade e compatibilidade em comparação com o uso de colunas TEXT. É importante considerar as necessidades específicas do projeto e as características do banco de dados ao escolher entre VARCHAR e TEXT para armazenamento de texto.


Configurações básicas de Tabela
======================================


1.  ENGINE: A configuração "ENGINE" define o mecanismo de armazenamento a ser usado para a tabela. No caso do código fornecido, o valor "InnoDB" é especificado. O mecanismo InnoDB é um mecanismo de armazenamento transacional que é amplamente usado no MySQL e é conhecido por suportar recursos como transações ACID (Atomicidade, Consistência, Isolamento e Durabilidade), chaves estrangeiras e bloqueios granulares.
    
2.  DEFAULT CHARSET: A configuração "DEFAULT CHARSET" define o conjunto de caracteres padrão a ser usado para a tabela. No código fornecido, o valor "utf8mb4" é especificado. O conjunto de caracteres utf8mb4 é uma extensão do conjunto de caracteres UTF-8 que suporta uma gama mais ampla de caracteres, incluindo emoji e caracteres especiais de várias línguas.
    
3.  COLLATE: A configuração "COLLATE" define a ordem de classificação padrão a ser usada para a tabela. No código fornecido, o valor "utf8mb4\_unicode\_ci" é especificado. O "ci" no final significa "case-insensitive", o que indica que a ordenação de caracteres não é sensível a maiúsculas e minúsculas.
    

Conclusão
---------
As configurações de tabela, como ENGINE, DEFAULT CHARSET e COLLATE, são importantes para definir o comportamento e as características das tabelas em um banco de dados. É importante considerar as necessidades específicas do projeto e as características do banco de dados ao configurar uma tabela, para garantir o correto funcionamento e desempenho do sistema.

👉Resultado
---------
![image](https://user-images.githubusercontent.com/93455937/232827943-a20ebf2d-3a40-4041-aa26-9a5abfde1156.png)




# **✍️ CMD `SHOW COLUMNS FROM tb_baralhos`**

Descrição
---------

Este código é uma instrução SQL para exibir as colunas de uma tabela chamada "tb\_baralhos" utilizando a linguagem PHP. A instrução "SHOW COLUMNS" é usada para obter informações sobre as colunas de uma tabela existente no banco de dados.

Código
------

sql

```sql
SHOW COLUMNS FROM tb_baralhos;
```

Detalhes
--------

*   `SHOW COLUMNS`: É uma instrução SQL utilizada para obter informações detalhadas sobre as colunas de uma tabela existente no banco de dados.
*   `FROM tb_baralhos`: É a cláusula que especifica a tabela da qual se deseja obter informações das colunas. "tb\_baralhos" é o nome da tabela da qual as colunas serão exibidas. Você pode substituir esse nome pelo nome da tabela que deseja obter informações.

Resultados
----------

A instrução "SHOW COLUMNS" retorna um conjunto de resultados que contém informações detalhadas sobre as colunas da tabela especificada. Essas informações podem incluir o nome da coluna, o tipo de dado, o tamanho máximo do dado, se a coluna permite nulos (NULL), se é uma chave primária, se é uma chave estrangeira, entre outras informações relevantes sobre as colunas da tabela.

Referências
-----------

*   [Documentação oficial do MySQL - SHOW COLUMNS](https://dev.mysql.com/doc/refman/8.0/en/show-columns.html)

👉Resultado
---------
![image](https://user-images.githubusercontent.com/93455937/232831343-399f0226-455d-42c3-943f-cf5f3b44c538.png)


===========================================================

# **✍️ CMD `SET SQL_SAFE_UPDATES`**

Descrição
---------
Configuração do **SQL\_SAFE\_UPDATES;** Este código é composto por duas instruções SQL para configurar a variável de sistema `SQL_SAFE_UPDATES` no MySQL. A primeira instrução `SET SQL_SAFE_UPDATES = 0;` desativa o modo seguro de atualizações no banco de dados, permitindo a execução de atualizações sem a cláusula `WHERE`, o que pode ser arriscado em alguns casos. A segunda instrução `SET SQL_SAFE_UPDATES = 1;` reativa o modo seguro de atualizações, que é a configuração padrão do MySQL, tornando obrigatória a utilização da cláusula `WHERE` em atualizações.

Código
------

sql

```sql
SET SQL_SAFE_UPDATES = 0;
-- Realize as atualizações necessárias aqui
```
sql
```sql
-- Realize as atualizações necessárias aqui
SET SQL_SAFE_UPDATES = 1;
```

Detalhes
--------

*   `SET SQL_SAFE_UPDATES`: É uma instrução SQL utilizada para definir o valor da variável de sistema `SQL_SAFE_UPDATES` no MySQL. Essa variável controla se é permitido ou não realizar atualizações sem a cláusula `WHERE` em tabelas que não possuam uma chave primária ou única definida.
*   `0`: É o valor que define o modo inseguro de atualizações, onde atualizações sem cláusula `WHERE` são permitidas.
*   `1`: É o valor que define o modo seguro de atualizações, onde atualizações sem cláusula `WHERE` são bloqueadas.

Importante
----------

*   É recomendado utilizar o modo seguro de atualizações, com `SQL_SAFE_UPDATES` definido como `1`, para evitar atualizações acidentais ou indesejadas em todas as situações em que não há uma necessidade específica de desativá-lo.
*   Antes de desativar o modo seguro de atualizações com `SQL_SAFE_UPDATES` definido como `0`, é importante ter cuidado e garantir que as atualizações sejam realizadas com atenção e segurança, utilizando cláusulas `WHERE` adequadas para evitar atualizações indesejadas em registros incorretos.

Referências
-----------

*   [Documentação oficial do MySQL - SET Syntax for Variable Assignment](https://dev.mysql.com/doc/refman/8.0/en/set-variable.html)
*   [Documentação oficial do MySQL - Server SQL Modes](https://dev.mysql.com/doc/refman/8.0/en/sql-mode.html)


# **✍️ CMD `DROP TABLE tb_baralhos;`**


Descrição
---------

Este código é uma instrução SQL para excluir uma tabela chamada "tb\_baralhos" de um banco de dados utilizando a linguagem PHP. A tabela será permanentemente removida do banco de dados.

Código
------

sql

```sql
DROP TABLE tb_baralhos;
```

Detalhes
--------

*   `DROP TABLE`: É uma instrução SQL utilizada para excluir uma tabela de um banco de dados no sistema de gerenciamento de banco de dados (SGBD).
*   `tb_baralhos`: É o nome da tabela que está sendo excluída. Você pode substituir esse nome pelo nome da tabela que deseja excluir do seu banco de dados.

Atenção
-------

A exclusão de uma tabela é uma operação irreversível e todos os dados contidos na tabela serão permanentemente removidos. Certifique-se de ter um backup adequado dos dados antes de executar essa instrução em um ambiente de produção.

Referências
-----------

*   [Documentação oficial do MySQL - DROP TABLE](https://dev.mysql.com/doc/refman/8.0/en/drop-table.html)


# **✍️ CMD `DELETE FROM tb_baralhos WHERE idBar = 7;`**


Descrição
---------

Este código é uma instrução SQL para excluir um registro da tabela "tb\_baralhos" em um banco de dados, especificamente o registro que possui o valor "7" no campo "idBar". Essa instrução é utilizada para deletar dados de uma tabela em um sistema de gerenciamento de banco de dados (SGBD) usando a linguagem PHP.

Código
------

sql

```sql
DELETE FROM tb_baralhos WHERE idBar = 7;
```

Detalhes
--------

*   `DELETE FROM`: É uma instrução SQL utilizada para excluir registros de uma tabela em um banco de dados.
*   `tb_baralhos`: É o nome da tabela da qual o registro será excluído. Você deve substituir esse nome pelo nome da tabela que deseja excluir o registro.
*   `WHERE`: É uma cláusula condicional que permite especificar a condição para exclusão dos registros. Neste caso, a condição é "idBar = 7", ou seja, será excluído o registro cujo valor do campo "idBar" seja igual a 7. Você pode ajustar essa condição de acordo com os critérios de exclusão desejados.
*   `idBar`: É o nome do campo que será utilizado na condição de exclusão. Você deve substituir esse nome pelo nome do campo correto da sua tabela.
*   `7`: É o valor que será utilizado na condição de exclusão. Você pode substituir esse valor pelo valor correto que deseja utilizar para excluir o registro desejado.

Referências
-----------

*   [Documentação oficial do MySQL - DELETE Statement](https://dev.mysql.com/doc/refman/8.0/en/delete.html)



# **✍️ CMD `SELECT * FROM tb_baralhos`**

Descrição
---------

Este código é uma instrução SQL para realizar uma consulta de todos os registros da tabela "tb\_baralhos". A tabela "tb\_baralhos" é parte de um sistema de CRUD (Create, Read, Update, Delete) em PHP, seguindo a arquitetura de MVC (Model-View-Controller) para a organização do código-fonte.

Código
------

sql

```sql
SELECT * FROM tb_baralhos;
```

Detalhes
--------

*   `SELECT`: É uma instrução SQL utilizada para realizar consultas em um banco de dados, retornando dados específicos de uma tabela.
*   `*`: É um caractere curinga que representa todas as colunas da tabela. Neste caso, a consulta está retornando todas as colunas da tabela "tb\_baralhos".
*   `FROM`: É uma cláusula SQL utilizada para especificar a tabela da qual se deseja realizar a consulta.
*   `tb_baralhos`: É o nome da tabela da qual os dados estão sendo consultados. Você pode substituir esse nome pelo nome da tabela que deseja consultar em seu banco de dados.

Referências
-----------

*   [Documentação oficial do MySQL - SELECT](https://dev.mysql.com/doc/refman/8.0/en/select.html)
*   [Documentação oficial do PHP - PDO (PHP Data Objects)](https://www.php.net/manual/en/book.pdo.php)
*   [Documentação oficial do padrão MVC](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller)



# **✍️ CMD `INSERT INTO `**

Descrição
---------

Este código é uma instrução SQL para inserir dados em uma tabela chamada "tb\_baralhos". A instrução realiza a inserção de um novo registro na tabela com os valores especificados para as colunas "idBar", "c\_bar" e "c\_dt".

Código
------

sql

```sql
INSERT INTO tb_baralhos 
    (idBar, c_bar, c_dt) 
    VALUES 
    (1, 'Baralho #001', '2023-01-01');
```

Detalhes
--------

*   `INSERT INTO`: É uma instrução SQL utilizada para adicionar novos registros em uma tabela específica.
*   `tb_baralhos`: É o nome da tabela na qual os dados estão sendo inseridos. Você pode substituir esse nome pelo nome da tabela em que deseja inserir os dados.
*   `(idBar, c_bar, c_dt)`: São as colunas da tabela às quais os valores estão sendo atribuídos. Neste caso, são as colunas "idBar", "c\_bar" e "c\_dt".
*   `VALUES`: É uma cláusula que especifica os valores a serem inseridos nas colunas da tabela.
*   `(1, 'Baralho #001', '2023-01-01')`: São os valores que estão sendo inseridos nas colunas da tabela. Neste caso, é um novo registro com os valores "1" para "idBar", "Baralho #001" para "c\_bar" e "2023-01-01" para "c\_dt". Os valores devem estar na mesma ordem das colunas especificadas anteriormente.

Referências
-----------

*   [Documentação oficial do MySQL - INSERT INTO Statement](https://dev.mysql.com/doc/refman/8.0/en/insert.html)


👉Resultado
---------
![image](https://user-images.githubusercontent.com/93455937/232838004-9a789c55-145a-4814-a283-e3fbea11149f.png)
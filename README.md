# Aviso

Deixando claro: o conteúdo abaixo partiu de um curso gratuito e ninguém tem autorização para redistribuí-lo. Se quiser estudar o tema, procure o curso aberto da trilha de Java com Spring Boot. Se a plataforma fechar o acesso ou passar a cobrar, não depende de mim — mas o material de lá é muito bom e quem assina um plano alcança bem mais.


# Geral

A primeira aula usada como base foi a de introdução a bancos relacionais e SQL.

Usei uma ferramenta de diagramas online para desenhar o que aprendi durante o curso. O acesso ao espaço de trabalho do curso foi pelo menu lateral, e também gravei um vídeo comentando a ferramenta.

Em outra aula o professor criou o banco num serviço gerenciado na nuvem. Como a opção de teste não apareceu para mim, criei o banco pelas ferramentas que minha hospedagem já oferecia.

Dados de acesso:
- servidor: pelo painel da hospedagem, entrando na administração do banco;
- nome do banco: u257595541_viagens
- usuário: u257595541_viagens
- senha: se você chegar pelo link do painel, não é pedida.

**OBS:** é preciso clicar no botão de entrar no administrador do banco específico.

Basicamente foi isso que a aula mostrou sobre criação de tabela:

![create table](images/criacao-de-tabela.png)

Sobre as cláusulas de consulta e inserção não tive novidade, só a de poder usar a forma alternativa do operador de diferença, que eu só conhecia numa das grafias.

Nas aulas de atualização e remoção também não anotei nada além do que eu já sabia.

O professor usou uma inserção a partir de um resultado de consulta, o que é bem útil:
![insert select](images/insercao-a-partir-de-consulta.png)

E também renomeou tabela:
![renaming a table](images/renomeando-tabela.png)

Ajustando uma coluna:
![modifying a column](images/alterando-coluna.png)

Guarde que só pode existir uma chave primária por tabela.

É possível ter valor nulo numa chave estrangeira:
![null values in foreign keys](images/nulos-em-chave-estrangeira.png)

Repare que receber nulo ou não depende da restrição declarada na coluna. Na tela de inserção aparecem as duas coisas:

- uma caixa de marcação que, quando assinalada, grava nulo no registro;
- uma lista com os valores existentes da outra tabela. Ao escolher um valor, a caixa de nulo é desmarcada automaticamente.

A sintaxe de criação de chave estrangeira varia entre os sistemas gerenciadores, e existe uma página clássica de referência com os exemplos.

![sql creation foreign key](images/criacao-de-chave-estrangeira.png)

Na imagem anterior o comando mostra a criação de chaves primárias de um jeito que também funciona no MySQL.

Dá para ter mais de uma chave estrangeira numa tabela. Pensando com calma é óbvio: basta apontar para tabelas diferentes, como numa tabela de itens de pedido, onde uma coluna aponta para o pedido e outra para o produto.

Incluindo uma restrição:
![adding a constraint](images/incluindo-restricao.png)

Restrições sobre restrições — nunca tinha usado a opção de valor padrão:
![restrictions on constraints](images/restricoes-sobre-restricoes.png)

Incluindo chave primária via alteração de tabela:
![alter table add primary key](images/alteracao-incluindo-chave-primaria.png)

Incluindo chave estrangeira via alteração de tabela:
![alter table add foreign key](images/alteracao-incluindo-chave-estrangeira.png)

Incluindo remoção em cascata na alteração de tabela:
![on delete cascade](images/remocao-em-cascata.png)

Removendo uma restrição manualmente:
![manually deleting a constraint](images/removendo-restricao.png)

Sobre normalização, primeira forma normal:

![first normal form](images/primeira-forma-normal.png)

A palavra "coluna" pode ser omitida:

```
alter table b modify column c tinyint;
```

Ou seja, os dois comandos abaixo têm o mesmo efeito:

```
alter table b modify c tinyint;
```

O mesmo vale na remoção de coluna:

```
alter table b drop column c;
```

![alter without the word 'column'](images/alteracao-sem-a-palavra-coluna.png)

Sobre a segunda forma normal:
![second normal form](images/segunda-forma-normal.png)

Em outras palavras, todos os campos dependem da chave primária, que pode ser simples ou composta.

Sobre a terceira forma normal:
![third normal form](images/terceira-forma-normal.png)

Cada coluna depende apenas da chave, e não de outra coluna.

Resumo das formas normais:

![summary-of-normal-forms.png](images/resumo-das-formas-normais.png)

Formas normais seguintes:
![more normal forms](images/mais-formas-normais.png)

Sobre junção externa completa:
![full join](images/juncao-externa-completa.png)

- Nem todo sistema gerenciador suporta a junção externa completa;
- Ela equivale a uma junção à esquerda mais uma à direita.

Diagrama representando essa junção:
![diagram full join](images/diagrama-juncao-completa.png)

Sobre subconsultas:
![sub queries](images/subconsultas.png)

Sobre funções de agregação:
![aggregation functions](images/funcoes-de-agregacao.png)

Sobre a função de diferença entre datas:
![timestampdiff function](images/diferenca-entre-datas.png)

O agrupamento não é função de agregação: serve para agrupar resultados.

Sobre o plano de execução:
![explain](images/plano-de-execucao.png)

Detalhes do plano:
![details of as explain](images/detalhes-do-plano.png)

Na imagem há a palavra de contagem de linhas examinadas, que mostra se houve varredura completa da tabela e se um índice seria necessário.

Primeiro exemplo de plano:
![first example of an explain](images/exemplo-1-plano.png)

Aqui já existe índice único na coluna de e-mail; repare que a coluna de chave mostra o índice usado.

Segundo exemplo: consulta filtrando por coluna sem índice. Houve varredura completa e o sistema precisou examinar todas as 34 linhas.
![second example of an explain](images/exemplo-2-plano.png)

Criando um índice e repetindo o plano:
![creating an index](images/criando-indice.png)

Terceiro exemplo:
![third example of an explain](images/exemplo-3-plano.png)

Por que duas linhas? Porque existem dois registros com o mesmo nome de pessoa.

Estrutura do comando de criação de índice:
![structure of a create index statement](images/estrutura-do-create-index.png)

Na imagem fica claro que um índice pode envolver mais de uma coluna.

# Encerramento

O repositório do curso está público.

Os slides da aula também estão salvos no projeto.
<h1>Aplicando filtros de SQL queries</h1>



<h2>Descrição</h2>
O atual projeto foi elaborado como atividade no processo de obtenção do certificado Tools of the Trade: Linux and SQL (Google and Coursera, curso necessário para a obtenção do certificado Google Cybersecurity Certification). Minha organização está trabalhando para tornar o sistema mais seguro, e meu trabalho é assegurar que o sistema está de fato seguro investigando potenciais riscos e atualizar o computador dos funcionários quando necessário. Os passos a seguir mostram como usei filtros SQL para desempenhar funções relacionadas a segurança.



<h2>Linguagem ou Utilidades</h2>

- <b>SQL</b> 

<h2>Ambiente utilizado </h2>

- <b>Linux</b>

<h2>Passo-a-passo:</h2>

<p align="center">
<b>Identificar tentativas de login pós-expediente</b><br/>
  Houve um possível incidente de segurança que ocorreu após o horário comercial (depois das 18h) sendo estes tentativas de login que falharam e o caso precisa ser investigado.
<br />
<br />
  O código a seguir demonstra como criei um SQL query para filtrar as tentativas que ocorreram.
<br />
<br />
<a href="https://imgur.com/q7662uE"><img src="https://i.imgur.com/q7662uE.png" title="source: imgur.com" /></a>
<br />
<br />
  A primeira parte da screenshot é o input e a segunda parte é o output. Esta consulta filtra tentativas de
login malsucedidas que ocorreram após as 18h. Comecei primeiramente selecionando todos os dados da
tabela log_in_attempts. Em seguida, usei o WHERE com um operador AND em seguida para filtrar meus
resultados e gerar apenas tentativas de login que ocorreram depois das 18h e não tiveram êxito. A
primeira condição é login_time > '18:00', que filtra as tentativas de login que ocorreram após as 18:00. A
segunda condição é sucess = FALSE (ou 0), que filtra as tentativas de login malsucedidas.
<br />
<br />
<br />
<b>Identificar tentativas de login em datas específicas</b><br/>
Um evento suspeito ocorreu no dia 09/05/2022 e qualquer atividade de login ocorrida em 09/05/2022 ou
no dia anterior precisa ser identificada e investigada.<br />
<br />
  O código a seguir demonstra como criei um SQL query para filtrar as tentativas.
<br />
<br />
<a href="https://imgur.com/eir0PNW"><img src="https://i.imgur.com/eir0PNW.png" title="source: imgur.com" /></a>
<br />
<br />
Essa consulta mostra todas as tentativas de login que ocorreram em 09/05/2022 ou 08/05/2022.
Primeiramente, selecionei todos os dados da tabela log_in_attempts. Em seguida, usei a cláusula WHERE
com um operador OR para filtrar meus resultados e gerar apenas tentativas de login que ocorreram em
ambas as datas. A primeira condição é login_date = '2022-05-09', que filtra logins em 2022-05-09. A
segunda condição é login_date = '2022-05-08', que filtra logins em 2022-05-08.
<br />
<br />
<br />
  <b>Identificar tentativas de login fora do México</b><br />
Depois de investigar os dados da organização sobre tentativas de login, levantou-se a suspeita de que algo
está acontecendo com tentativas de login fora do Méxicom, portanto devem ser investigadas.<br /><br />
O código a seguir demonstra como criei uma SQL query para filtrar tentativas de login que ocorreram
fora do México.
<br />
<br />
<a href="https://imgur.com/XthZhEy"><img src="https://i.imgur.com/XthZhEy.png" title="source: imgur.com" /></a>
<br />
<br />
O comando utilizado retorna todas as tentativas de login ocorridas em outros países além do México.
Iniciei selecionando todos os dados da tabela log_in_attempts. Em seguida, utilizei a cláusula WHERE
com NOT para filtrar os países além do México. Optei por utilizar LIKE com MEX% devido ao conjunto
de dados representar o México como MEX e MÉXICO. O sinal de porcentagem (%) representa qualquer
número de caracteres não especificados quando usado em conjunto com LIKE.
<br />
<br />
<br />
<b>Identificando funcionários no Marketing</b>
<br />
Minha equipe deseja atualizar os computadores de determinados funcionários do departamento de
Marketing. Para fazer isso, preciso obter informações sobre quais máquinas dos funcionários devo
atualizar.
<br />
<br />
O código a seguir demonstra como criei uma SQL query para filtrar máquinas de funcionários do
departamento de Marketing no prédio Leste.
<br />
<br />
<a href="https://imgur.com/43CCOeA"><img src="https://i.imgur.com/43CCOeA.png" title="source: imgur.com" /></a>
<br />
<br />
Primeiro consultei todos os funcionários do departamento de Marketing do prédio Leste. Comecei
selecionando todos os dados da tabela de funcionários. Em seguida, usei uma cláusula WHERE com
AND para filtrar os funcionários que trabalham no departamento de Marketing e no prédio Leste. Usei
LIKE com East% para acessar os dados do escritório que representa o edifício Leste. A primeira condição
é a parte departament = 'Marketing', que filtra os funcionários do departamento de Marketing. A segunda
condição é a parte do office LIKE 'Leste%', que filtra os funcionários do edifício Leste.
<br />
<br />
<br />
<b>Identificar funcionários em Finanças ou Vendas</b>
<br />
As máquinas dos funcionários dos departamentos Financeiro e de Vendas também precisam ser
atualizadas. 
<br />
<br />
A seguir, mostro o comando que utilizei
<br />
<br />
<a href="https://imgur.com/tGDq1fF"><img src="https://i.imgur.com/tGDq1fF.png" title="source: imgur.com" /></a>
<br />
<br />
Esta consulta retorna todos os funcionários dos departamentos Financeiro e de Vendas. Primeiro, comecei
selecionando todos os dados da tabela de funcionários. Utilizei o WHERE com OR para filtrar os
funcionários que estão nos departamentos Financeiro e de Vendas. Usei o operador OR em vez de AND
porque quero todos os funcionários de qualquer um dos dois departamento. A primeira condição é
departament = 'Finance', que filtra funcionários do departamento Financeiro. A segunda condição é
departament = 'Sales', que filtra funcionários do departamento de Vendas.
<br />
<br />
<br />
<b>Identificar funcionários que não são da T.I</b>
<br />
Minha equipe precisa fazer mais uma atualização de segurança nos funcionários que não são do
departamento de Tecnologia da Informação. Para fazer a atualização, primeiro preciso obter informações
sobre esses funcionários.
<br />
<br />
A seguir, demonstro como realizei a operação
<br />
<br />
<a href="https://imgur.com/rof0ax0"><img src="https://i.imgur.com/rof0ax0.png" title="source: imgur.com" /></a>
<br />
<br />
A consulta retorna todos os funcionários que não pertencem ao departamento de Tecnologia da
Informação. Primeiro, comecei selecionando todos os dados da tabela de funcionários. Em seguida, usei
uma cláusula WHERE com NOT para filtrar funcionários que não pertencem a este departamento.
<br />
<br />
<br />
<b>Sumário</b>
<br />
Apliquei filtros em consultas SQL para obter informações específicas sobre tentativas de login e
máquinas de funcionários. Usei duas tabelas diferentes, log_in_attempts e employees. Usei os operadores
AND, OR e NOT para filtrar as informações específicas necessárias para cada tarefa. Também usei LIKE
e o wildcard do sinal de porcentagem (%) para realizar busca por meio de padrões. Os filtros SQL são
fundamentais para a análise de dados em uma empresa ou organização, onde por meio de estruturas em
colunas e tabelas se torna fácil a identificação e iniciação de processos seja para a segurança, ou para
reportar determinada informação.






  
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>

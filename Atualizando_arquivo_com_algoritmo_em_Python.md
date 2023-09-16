<h1>Atualizando arquivo com algoritmo em Python</h1>



<h2>Descrição</h2>
O atual projeto foi elaborado como atividade no processo de obtenção do certificado Automate Cybersecurity Tasks with Python (Google and Coursera, curso necessário para a obtenção do certificado Google Cybersecurity Certification). 
Em uma organização, o acesso a conteúdo restrito é controlado com uma lista de permissões de endereços IP.
O arquivo "allow_list.txt" identifica esses endereços. Uma lista de remoção separada identifica o IP
endereços que não deveriam mais ter acesso a esse conteúdo. Neste projeto irei demonstrar alguns conhecimentos de algoritmo para
automatizar a atualização do arquivo "allow_list.txt" e remover esses endereços IP que não deveriam ter acesso.



<h2>Linguagem ou Utilidades</h2>

- <b>Python</b> 

<h2>Ambiente utilizado </h2>

- <b>Windows</b>

<h2>Passo-a-passo:</h2>

<p align="center">
<b>Abrir o arquivo que contém a allow_list</b><br/>
Primeiramente, atribuí a allow_list.txt à variável denominada import_file como uma string.
<br />
<br />
<a href="https://imgur.com/x57zw6v"><img src="https://i.imgur.com/x57zw6v.png" title="source: imgur.com" /></a>
<br />
<br />
Em seguida, eu abri o arquivo utilizando o comando with
<br />
<br />
<a href="https://imgur.com/eDr48R1"><img src="https://i.imgur.com/eDr48R1.png" title="source: imgur.com" /></a>
<br />
<br />
O comando with é utilizado com a função .open() no modo de leitura (r) para abrir
o arquivo em modo leitura. Com isso, consigo acessar os endereços IP armazenados no arquivo da lista de permissões. A palavra-chave with ajudará a gerenciar o
recursos fechando o arquivo após sair da instrução with. No código com
open(import_file, "r") as file:, a função open() possui dois parâmetros. O primeiro
identifica o arquivo a ser importado e o segundo indica o que quero fazer com o arquivo. O código também atribui à uma
variável chamada file, onde o file armazena a saída da função .open() enquanto eu trabalho dentro dele.
<br />
<br />
<br />
<b>Ler o conteúdo do file</b><br/>
Para ler o conteúdo o file, foi necessário usar o método .read() e convertê-lo em uma string.
<br />
<br />
<a href="https://imgur.com/PTsOTKE"><img src="https://i.imgur.com/PTsOTKE.png" title="source: imgur.com" /></a>
<br />
<br />
A função .open() que inclui o argumento "r" para “ler”, me permite chamar a
função .read() no corpo do file. O método .read() converte o arquivo
em uma string e me permite lê-lo. Apliquei a função .read() à variável do file
e em seguida, atribuí a saída de string deste método à variável ip_addresses. Em resumo, este código me permite utilizar o conteúdo do arquivo "allow_list.txt" em um formato de string
para usar posteriormente.
<br />
<br />
<br />
<b>Converter string em list</b>
<br />
Para remover endereços IP individuais da allow_list, eu preciso que estejam no formato de list.
Utilizei o método .split() para converter a string ip_addresses em uma list:
<br />
<br />
<a href="https://imgur.com/drFklok"><img src="https://i.imgur.com/drFklok.png" title="source: imgur.com" /></a>
<br />
<br />
A função .split() transforma uma string em list. O propósito em utilizar essa função é tornar mais fácil remover individualmente os IP's necessários. Por padrão, a função .split() divide o
texto por espaço em branco em elementos da lista. 
<br />
<br />
<br />
<b>Iterar pela lista de remoção</b><br />
Uma parte fundamental deste algorítmo é iterar pelos IP's dentro da remove_list. Para eu fazer isso será necessário o loop for:
<br />
<br />
<a href="https://imgur.com/IlMUWVL"><img src="https://i.imgur.com/IlMUWVL.png" title="source: imgur.com" /></a>
<br />
<br />
O loop for em Python repete o código para uma sequência. O objetivo do
loop em um algoritmo como este é aplicar instruções de código específicas a todos os elementos em um
sequência. Ele é seguido pela variável element e a palavra-chave in. O in utilizado em remove_list vai passar pelo seu conteúdo e atribuir instruções.
<br />
<br />
<br />
<b>Remover os endereços IP contidos na remove_list</b>
<br />
O objetivo é realizar a remoção de qualquer endereço IP da allow_list, ip_addresses, que está presente na remove_list:
<br />
<br />
<a href="https://imgur.com/d52hhZd"><img src="https://i.imgur.com/d52hhZd.png" title="source: imgur.com" /></a>
<br />
<br />
Dentro do meu loop for, criei uma condicional que avaliou se a variável element foi encontrada na remove_list. Então, dentro dessa condicional, apliquei .remove() a ip_addresses.
<br />
<br />
<br />
<b>Atualizar o file com a lista de IP revisada</b>
<br />
Como etapa final, eu precisei atualizar o arquivo da allow_list com a lista revisada de IPs. Para fazer isso, primeiro precisei converter a lista novamente em uma string. Eu usei a função .join() para isso e em seguida, abri novamente
a variável import_file, mas dessa vez com a função de escrever (w) na variável file.
<br />
<br />
<a href="https://imgur.com/pXoACor"><img src="https://i.imgur.com/pXoACor.png" title="source: imgur.com" /></a>
<br />
<br />
O .join() transforma string em list. Utilizei o \n como quebra de linha para organização, e defini o ip_addresses para nossa nova list. Em seguida, com o .write() eu escrevi nossa nova lista de IP's revisada para
a variável import_file que contém nossa allow_list.
<br />
<br />
Em seguida, após a atualização, abri novamente o import_file como leitura (r) na variável file para observar as alterações que realizei. No corpo da edição, adicionei o resultado final à variável text
e incluindo a função print() para nos mostrar o resultado.
<br />
<br />
<a href="https://imgur.com/r6JpJpj"><img src="https://i.imgur.com/r6JpJpj.png" title="source: imgur.com" /></a>
<br />
<br />
Com isso concluímos o algorítimo, aqui segue um antes e depois onde o antes, todos os IP's estão contidos na allow_list, inclusive os que deveriam ser removidos, e após o algorítimo, foi realizada a remoção dos IP's
necessários.
<br />
<br />
Antes:
<br />
<br />
<a href="https://imgur.com/xPh06Mo"><img src="https://i.imgur.com/xPh06Mo.png" title="source: imgur.com" /></a>
<br />
<br />
Depois:
<br />
<br />
<a href="https://imgur.com/lTHSTGk"><img src="https://i.imgur.com/lTHSTGk.png" title="source: imgur.com" /></a>
<br />
<br />
<br />
<b>Sumário:</b>
<br />
Criei um algoritmo que remove endereços IP identificados em uma variável remove_list para o arquivo "allow_list.txt" de endereços IP aprovados. Este algoritmo envolveu a abertura do
arquivo, convertendo-o em uma string para ser lida e, em seguida, convertendo essa string em uma lista armazenada na
variável ip_addresses. Em seguida, iterei pelos endereços IP em remove_list. Com cada
iteração, avaliei se o elemento fazia parte da lista ip_addresses. Se fosse, apliquei o
.remove() para remover o elemento de ip_addresses. Depois disso, usei o
método .join() para converter os ip_addresses de volta em uma string para que eu possa escrever
o conteúdo do arquivo "allow_list.txt" com a lista revisada de endereços IP. Por fim, abri novamente a "allow_list.txt" como file em modo leitura
para observar se as alterações foram devidamente concluídas.






  
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

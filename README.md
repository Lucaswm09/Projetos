<h1>Permissões de arquivos no Linux</h1>



<h2>Descrição</h2>
O atual projeto foi elaborado como atividade no processo de obtenção do certificado Tools of the Trade: Linux and SQL (Google and Coursera, curso necessário para a obtenção do certificado Google Cybersecurity Certificate). Um time de pesquisa em minha organização precisa atualizar as permissões de determinados arquivos e diretórios dentro do diretório projects, devido as atuais permissões não refletirem o level de autorização que deve ser estabelecido, portanto atualizar essas permissões tornará o sistema seguro. Para completar essa atividade, eu realizei os seguintes passos: 
<br />


<h2>Linguagem ou Utilidades</h2>

- <b>Bash</b> 

<h2>Ambiente utilizado </h2>

- <b>Linux</b>

<h2>Passo-a-passo:</h2>

<p align="center">
<b>Checar detalhes do arquivo e diretórios</b><br/>
  O código seguinte demonstra como utilizei os comandos do Linux para entender as permissões previamente estabelecidas no diretório requisitado.<br />
<br />
<a href="https://imgur.com/9eHoWs9"><img src="https://i.imgur.com/9eHoWs9.png" title="source: imgur.com" /></a>
<br />
<br />
  A primeira linha da screenshot mostra o comando que realizei, e as outras linhas mostram o resultado que é todo o conteúdo dentro do diretório projects. Eu utilizei o comando ls com adição do -la para mostrar detalhadamente os arquivos dentro do diretório incluindo os arquivos secretos. O resultado do meu comando indica que há um diretório chamado drafts, um arquivo secreto chamado .project_x.txt, além de outros cinco arquivos. Os 10 caractéres strings que aparecem na primeira coluna representam as permissões para cada arquivo e diretório.
<br />
<br />
<br />
<b>Descrever as strings de permissões</b><br/>
  Os 10 caractéres da primeira coluna podem ser separados para determinar quem está autorizado a acessar o arquivo e qual o tipo de permissão. Cada letra representa a seguinte permissão:<br /><br />
   1º caracter: Este pode ser um d ou um hífen (-) e indica o tipo do arquivo. Se for um d é um diretório, e se for um hífen (-) é um arquivo regular. <br />
 2º ao 4º caracteres: Estes podem ser indicados como read (r), write (w) ou execute (x) ao usuário sendo diferentes tipos de permissões para ler, escrever ou executar o arquivo/diretório. Se houver um hífen (-) significa que essa permissão não está concedida. <br />
 5º ao 7º caracteres: Esse segmento de caracteres ainda indicam (r), (w) ou (x) mas para um grupo. Se houver hífen (-) então a permissão não está concedida. <br />
 8º ao 10º caracteres: Também indicam (r), (w) ou (x) mas para outro. Se houver um hífen (-) a permissão não está concedida. <br />
<br />
Por exemplo, se a permissão para o project_t.txt for -rw-rw-r--, como o primeiro caractér é um hífen (-) então indica que é um arquivo e não um diretório. O segundo, quinto e oitavo caractéres são todos r, o que indica que tanto o usuário, como grupo e outro possuem permissão para ler (read). O terceiro e o sexto caracteres são w, o que indicam que apenas o usuário e o grupo possuem permissão para escrever. Nenhum dos segmentos possuem permissão para executar no project_t.txt.
<br />
<br />
<br />
  <b>Alterar permissões do arquivo</b><br />
  A organização então determinou que outro não deve haver permissão para escrever (w) em nenhum dos arquivos. Para seguir com essa ordem, eu segui com a modificação da permissão do w para outro no project_k.txt.<br /><br />
O comando a seguir demonstra como foi implementado:<br /><br />
<a href="https://imgur.com/H8iB3A5"><img src="https://i.imgur.com/H8iB3A5.png" title="source: imgur.com" /></a>
<br />
<br />
As primeiras duas linhas mostram o comando que iniciei e as outras linhas foram o output desses comandos. O comando chmod altera a permissão de arquivos de diretórios. O primeiro argumento mostra a permissão que será alterada e o segundo especifica o arquivo ou diretório. Como consta na imagem, eu removi as permissões de escrever (w) de outro para project_k.txt. Após isso utilizei o ls -la para conferir as atualizações.
<br />
<br />
<br />
<b>Alterar permissões do arquivo secreto</b>
<br />
A organização adicionou recentemente o arquivo project_x.txt. Eles não permitem que ninguém tenha o privilégio de escrever (w) no arquivo, mas o usuário e o grupo devem possuir acesso para ler (r).
<br />
<br />
O comando seguinte demonstra como utilizei o Linux para seguir com as alterações:
<br />
<br />
<a href="https://imgur.com/hFGhl0W"><img src="https://i.imgur.com/hFGhl0W.png" title="source: imgur.com" /></a>
<br />
<br />
As primeiras duas linhas mostram o meu comando de input e as outras o output. Sabemos que o .project_x.txt é um arquivo secreto por haver um ponto (.) antes de seu nome. Nesta screenshot, eu removi as permissões de escrever do usuário e do grupo, e então adicionei a permissão de ler para o grupo.
<br />
<br />
<br />
<b>Alterar permissões do diretório</b>
<br />
A organização então solicitou que o usuário researcher2 possuísse acesso ao diretório drafts e seu conteúdo. Isso significa que ninguém além do researcher2 conseguirá executar permissões.
<br />
<br />
O comando a seguir demonstra como segui com a solicitação:
<br />
<a href="https://imgur.com/gqppDIk"><img src="https://i.imgur.com/gqppDIk.png" title="source: imgur.com" /></a>



  
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

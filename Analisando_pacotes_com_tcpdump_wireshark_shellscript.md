<h1>Analisando pacotes com tcpdump, Wireshark e Shell Script</h1>



<h2>Descrição</h2>
O atual projeto foi elaborado como atividade no processo de obtenção do certificado Analyze Network Traffic with tcpdump (Coursera). Há a suspeita de que alguém está tentando inicar sessões SSH em minha estação de trabalho, então decidi estabelecer um shell script de vigilância para capturar qualquer tráfego TCP através do SSH

<h2>Linguagem ou Utilidades</h2>

- <b>tcpdump</b> 

<h2>Ambiente utilizado </h2>

- <b>Linux</b>

<h2>Passo-a-passo:</h2>

<p align="center">
<b>Criar um arquivo chamado checkspy.sh e dar acesso para escrever (+x)</b><br/>
  Inicialmente, eu crio o file no aplicativo Visual Studio Code para começarmos a trabalhar com a definição do código shell script, as imagens a seguir demonstram como realizei esse processo.
<br />
<br />
 Criação do checkspy.sh
<br />
<br />
<a href="https://imgur.com/VcOKcIu"><img src="https://i.imgur.com/VcOKcIu.png" title="source: imgur.com" /></a>
<br />
<br />
  Em seguida, através do comando chmod +x checkspy.sh, eu habilito a função de execução do arquivo criado. Eu utilizo também o -ls la para checar se as permissões foram estabelecidas.
<br />
<br />
<a href="https://imgur.com/2xvDKUF"><img src="https://i.imgur.com/2xvDKUF.png" title="source: imgur.com" /></a>  
<br />
<br />
<br />
<b>Capturar pacotes SSH (porta 22) e salvar a captura em um arquivo chamado proof.pcap, onde o arquivo não deve ultrapassar 2,000,000 bytes e não capturar mais que 10 minutos.</b><br/>
A imagem a seguir mostra a linha de código que eu inseri para habilitar a captura de pacotes da porta 22 e como salvei ele no arquivo denominado proof.pcap<br />
<br />
<br />
<a href="https://imgur.com/vN5A2dd"><img src="https://i.imgur.com/vN5A2dd.png" title="source: imgur.com" /></a>
<br />
<br />
Pelo exercício estar sendo realizado em um laboratório virtual, o comando sudo me permite receber comandos de superusuário por um tempo determinado. Em seguida, incluo o tcpdump com o -i any para determinar a captura em uma rede local (dentro do lab). O argumento -#XXtttt 
permite uma organização e visualização melhor (o # transforma a visualização em caractéres hexadecimais, o XX nos permite a enumeração dos pacotes e o tttt inclue o timestamp das capturas nos permitindo visualizar o tempo que foram capturados). O port 22 define a porta
que iniciaremos a captura. O -w proof.pcap determina onde vamos escrever (será no nosso arquivo proof.pcap). O -C 2 e o -G 600 determina o tamanho e o tempo respectivamente da captura (-C 2 determina o limite de 2,000,000 bytes e -G 600 determina 10 minutos em forma de segundos).
<br />
<br />
<br />
  <b>Executar o arquivo e simular o tráfego SSH</b><br />
A seguinte imagem demonstra o comando que utilizei para executar o shell script. Utilizei o comando ./checkspy.sh para executar o diretório criado do nosso novo shell script.
<br />
<br />
<a href="https://imgur.com/JDMES3b"><img src="https://i.imgur.com/JDMES3b.png" title="source: imgur.com" /></a>
<br />
<br />
Em seguida, no terminal eu executo o comando ssh localhost para simular um tráfego local SSH e ser realizada uma captura de pacotes.
<br />
<br />
<a href="https://imgur.com/xjzPaGK"><img src="https://i.imgur.com/xjzPaGK.png" title="source: imgur.com" /></a>
<br />
<br />
É possível observar quando clicamos no proof.pcap que foram capturadas informações criptografadas do pacote, então conseguimos realizar a captura com sucesso.
<br />
<br />
<a href="https://imgur.com/P82nnZb"><img src="https://i.imgur.com/P82nnZb.png" title="source: imgur.com" /></a>
<br />
<br />
<br />
<b>Analisando pacotes com o Wireshark</b>
<br />
O próximo passo será abrir nosso arquivo criado através do aplicativo Wireshark, que irá nos permitir uma análise mais detalhada das informações contidas dentro do pacote. No Wireshark, eu vou em open file (símbolo da pasta azul) e vou até o diretório onde está o proof.pcap e o executo.
<br />
<a href="https://imgur.com/yNkYPIu"><img src="https://i.imgur.com/yNkYPIu.png" title="source: imgur.com" /></a>
<br />
<br />
Pronto! Agora conseguimos analisar todas as informações necessárias. Conseguimos identificar a comunicação Three-Way-Handhshake (nos possibilitando verificar se há algum tentativa de SYN flood por exemplo), além de informações como a origem do
endereço IP do possível atacante. O Wireshark nos traz também informações sobre cada parte do nosso pacote criptografado quando selecionamos algum segmento, como o tamanho do pacote, o checksum, header lenght, protocolo e entre outros, assim nos possibilitando
uma análise detalhada. Segue a imagem a seguir:
<br />
<br />
<a href="https://imgur.com/9E6W8SY"><img src="https://i.imgur.com/9E6W8SY.png" title="source: imgur.com" /></a>
<br />
<br />
<br />
<b>Sumário</b>
<br />
Apliquei um código shell script para realizarmos uma captura de pacotes na porta 22 para checarmos uma possibilidade de backdoor através do SSH. Como foi um exercício, simulei o tráfego SSH através do comando ssh localhost no terminal
e através do nosso shell script, conseguimos capturar as informações contidas nesse tráfego e analisamos com o Wireshark. Essas ferramentas são fundamentais no dia a dia de um profissional de segurança da informação ou qualquer outra área
da tecnologia que lida com análise e rastreio de informações de redes.


  
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

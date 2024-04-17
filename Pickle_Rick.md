<h1>Objetivo</h1>
<br>

Explorar um servidor web e encontrar os três ingredientes necessários para a poção de Rick Pickles para transformá-lo em Rick Humano.</p>

<p align="center">
  <img width="200" src="https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExNzZtZ3kwOG9vb2hoanc5M3dreWU4bDZsMXp6azl4eG9tNGl5a3JjbyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/JmPenP1svctdfDCEHi/giphy.gif">
</p>

<h2>Inicie a Maquina Virtual</h2>
<br>

O iniciar a VM no TryHackMe, você deve verificar a conectividade usando o comando ping juntamente com o IPv4 que a plataforma disponibiliza para a exploração, o comando e a imagem abaixo são um exemplo.</p>
```
ping -c2 10.10.199.55
```
<p align="center">
  <img width="500" src="https://github.com/mtsXD/CTF/blob/main/IMG/comando_ping.png?raw=true">
</p>

>
>Vale ressaltar que o IP utilizado é o Target IP que oTryHackMe preparou para mim, o seu muito provavelmente será diferente.
<br>

Como houve resposta no ping, pode-se começar a efetuar a fase de reconhecimento do nosso alvo. Utilizaremos o nmap para verificar os serviços e possíveis vulnerabilidades do Target IP.</p>
O comando abaixo é o que frequentemente utilizo para reconhecimento nmap:</p>
```
nmap  -vv -sC -sV -Pn 10.10.199.55
```

<p align="center">
  <img src="https://github.com/mtsXD/CTF/blob/main/IMG/nmap-rickpickle.png?raw=true">
</p>

Analisando a porta 80, HTTP, notamos que está aberta em um servidor web, o que pode ser feito, é colocar o IP do alvo no navegador e verificar o comportamento.</p>

<p align="center">
  <img src="https://github.com/mtsXD/CTF/blob/main/IMG/ip-rickpickle-browser.png?raw=true">
</p>

Primeira coisa a ser feita é ler o conteúdo do site, procurar alguma dica ou alguma palavra chave, no nosso caso, não há nada demais, apenas o Rick sendo Rick e ele pedindo o objetivo desse laboratório.</p>
Porém, agora faremos a Inspeção do conteúdo da página, normalmente há anotações ou links de redirecionamento para outras páginas. No nosso caso, a figura abaixo mostra que encontramos uma palavra chave que ainda não sabemos para que serve, mas sabemos que se algo pedir o nome do usuário, provavelmente será "R1ckRul3s".</p>

<p align="center">
  <img src="https://github.com/mtsXD/CTF/blob/main/IMG/inspen%C3%A7%C3%A3o-rickpickles-browser.png?raw=true">
</p>

Após isso não há mais nada para verificar nesse servidor web, voltando ao terminal, podemos utilizar ferramentas que buscam diretórios e buscar outras dicas e/ou palavras chaves.</p>
Utilizaremos o comando abaixo para abrir as seguintes configurações no seu Kali:</p>
```
dirbuster
```
Ao efetuar o comando, você será direcionado a uma aplicação para efetuar as seguintes configurações. Conforme mostra a figura abaixo:</p>

<p align="center">
  <img width="600" src="https://github.com/mtsXD/CTF/blob/main/IMG/dirbuster-rickpickles.png?raw=true">
</p>

>
>Em Target URL você colocará http://{O ip do THM}:80</p>
>Number of Threads aconcelho a habilitar "Go Faster", ou deixar o valor acima de 200 caso sua memoria seja alta.</p>
>Em file with list or dir/files aconselho a colocar "/usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt" no espaço em branco, uma dica, abra outro terminal e digite sem executar esse comando "/usr/share/wordlists/dirbuster/" após isso, aperte tab, com isso você pode verificar outras opções sem ser necessáriamente a directory-list-2.3-medium.txt. </p>
>Em File extension, você pode colocar apenas "php, txt, html", mas se quiser adicionar mais, pode colocar outras extenções que você conheça.</p>
>Por fim, aperte start.

Após efetuar a verificação, vá na aba Results - List View e verifique todos os resultados com resposta 200 do servidor.</p>
Para poupar o seu tempo, basta clicar no botão auxiliar e solicitar que abra no browser, como mostra a imagem abaixo.</p>

<p align="center">
  <img width="600" src="https://github.com/mtsXD/CTF/blob/main/IMG/dica-dirbuster-rickpickles.png?raw=true">
</p>

Abrindo cada resposta 200, a /robots.txt mostrou uma informação intereçante para ser investigada. A resposta 200 /login.php apresentou uma pagina de acesso, em que temos o nome de usuário que obtemos mais cedo.</p>
O restante das respostas 200, ao serem investigadas, não verifiquei algo relevante, apensa que são conteudos que provavelmete seja da aplicação dentro da pagina de acesso.</p>
A imagem abaixo mostra a pagina de acesso que diretorio /login.php me direcionou.</p>

<p align="center">
  <img src="https://github.com/mtsXD/CTF/blob/main/IMG/dir-php-rickpickles.png?raw=true">
</p>

A primeira coisa que irei fazer, é colocar o nome de usuário que encontramos na inspeção, o texto “R1ckRul3s” e a senha, vou colocar o texto encontrado no robots.txt o “Wubbalubbadubdub” e verificar o resultado, como mostra a imagem abaixo.</p> 

<p align="center">
  <img src="https://github.com/mtsXD/CTF/blob/main/IMG/php-in-rickpickles.png?raw=true">
</p>

Obtemos acesso, podemos inspecionar a página para encontrar alguma dica ou palavra chave, ou podemos efetuar comandos Ubuntu porque o cenário faz parecer que é isso o que deve ser feito, e porque Ubuntu? Volte na imagem do Nmap, lá em cima, lá diz que ele é o sistema operacional em que o ip está trabalhando.</p>
Aqui aconselho a você a fazer a exploração por si, caso esteja perdido, pode continuar lendo o artigo, pois a partir daqui será o comando necessário para obter os ingredientes.</p>
<br>

<h2>Primeiro igrediente.</h2>
Os comando a seguir são os necessários para obter o primeiro igrediente, é necessário que esteja dentro do /portal.php.</p>

```
ls
```

```
less Sup3rS3cretPickl3Ingred.txt
```

<p> Obtemos o  primeiro ingrediente  que é “mr. meeseek hair” para nossa poção.</p>

<p align="center">
  <img width="200" src="https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExZmZ4cGhubmNlMHJ3NW1zbDF4c2NoNHA3Mmw5amw0N3R3NDhtcmN6MCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/11Tsyjflf2xq2A/giphy.gif">
</p>
<br>

<h2>Segundo igrediente.</h2>
Os comando a seguir são os necessários para obter o segundo igrediente, é necessário que esteja dentro do /portal.php.</p>

```
ls ../../..
```
```
ls /home/rick
```
```
tac /home/rick/"second ingredients"
```

<p> Obtemos o  segundo igrediente  que é o “1 jerry tearr” para nossa poção, faltando apenas um.</p>

<p align="center">
  <img width="200" src="https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExa2ttNnhraHI1MGVxanphMDkybDc5YXhwOXQ1ajY1bzE5dDk5cThzciZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/cODrlNTkGnZGVtVagd/giphy.gif">
</p>
<br>

<h2>Terceiro igrediente.</h2>
Os comando a seguir são os necessários para obter o ultimo igrediente, é necessário que esteja dentro do /portal.php.</p>

```
ls ../../..
```
```
sudo ls /root
```
```
sudo less /root/3rd.txt
```

<p> Obtemos o  ultimo igrediente  que é o “fleeb juice” para nossa poção, finalizamos.</p>

<p align="center">
  <img width="200" src="https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExaWZjNWFpaW4zY2twYWY2b216Mm9nZGo5Z283MWdhN2VlN3I3ZzdjcyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/kDg1bNCUZsUpmBdMwA/giphy.gif">
</p>
<br>

Com isso, terminamos, agora você já tem tudo o que é necessário para conquistar a sala.</p>

<p align="center">Obrigado~</p>
<p align="center">
  <img width="500" src="https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExcDNvYzRuaXJ2MTgxbmNqNjV1NTBmdDd3cW51OGZ5cDBkOWs0YWkxbCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/MPExLVFFXMuD8WpEwn/giphy.gif">
</p>

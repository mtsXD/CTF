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


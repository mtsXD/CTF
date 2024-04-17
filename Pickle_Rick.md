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

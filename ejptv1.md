# eJPT v1

### **Antedecentes**
Esta certificación corresponde a la certificación básica de pentester de eLearn Security y consiste en 20 preguntas que deberás obtener al atacar las diferentes máquinas víctimas. Este examen dura 3 días desde que se inicia y lo que busca es demostrar que una persona sabe los conceptos prácticos al realizar un Ethical Hacking (identificar vectores de ataque, escanear redes, detectar S.O. detectar vulnerabilidades, realizar Pentest Web, entre otras cosas).

#### Preparación
Esta prueba presenta una dificultad básica por lo que con estudio se podrá rendir y pasar fácilmente. Para prepararse para esta prueba, primero debes entender los conceptos teóricos del Ethical Hacking, uso de herramientas automáticas como MetaSploit, entre otros. Esto le ayudará a la hora de entender los ataques que está realizando. Por otro lado, háganse una cuenta en Hack The Box, y practiquen máquinas que presenta esta plataforma (si quieren pueden pagar por la cuenta VIP ya que pueden acceder a maquinas retiradas y revisar los WriteUp), para ello pueden usar el github desarrollado por CheatModes4 y levantado por S4vitar. También pueden hacerlo con Vulnhub, Tryhackme o Hackzone que son página con la misma temática. También puede entrar a las academias de Hack de Box donde te capacitan en diversos temas de ciberseguridad.

### **EL EXAMEN**
Dispone de 20 preguntas y se aprueba con un 75% de preguntas buenas (15preguntas buenas). Para ello una persona tiene hasta 3 días para completar los diferentes desafíos. A diferencia de otras certificaciones como CEH Practical, en esta certificación te dan una VPN para poder atacar las máquinas víctimas y puede usar tu propia máquina. Esto presenta una gran ventaja a la hora de trabajar, ya que uno está familiarizado con todas las herramientas de la máquina. Es por ello por lo que recomiendo antes de iniciar la certificación te armes un buen arsenal de herramientas para que no te falte alguna. De igual manera dejaré en este Review algunas que utilicé.
Es importante entender, ya que en esta certificación te hacen las preguntas solo enfocarse en obtener dichas respuestas, así optimizaras el tiempo que se tiene.

#### **Habilidades mínimas**
- Uso de herramientas automáticas
- Fuzzing
- Ataques de Diccionario
- Escaneo de Red
- Escaneo de Vulnerabilidades
- Reconocimiento Web
- CVE


### **HERRAMIENTAS**
Dentro de las herramientas que se utilizará para resolver este examen tenemos.

- Nmap
- Hydra
- MetaSploit
- John the Ripper
- Wireshark, TShark o Tcpdump
- WFUZZ, Dirb, GoBuster


#### **NMAP**
La idea es encontrar puertos abiertos, sistemas operativos, servicios. Para ello se puede usar Nmap. La ventaja de Nmap es que se puede combinar las consultas realizadas, permitiendo agilizar el escaneo dentro de la red víctima. Si quieren guardar lo obtenido en los escaneo se puede utilizar `-oN <ARCHIVO SALIDA>`
   
- Ver Sistema Operativo
```
root@kali:~# nmap -O <IP/RED>
```
- Ver hosts con puerto abierto
```
root@kali:~# nmap -p <PUERTO> <RED>
```
- Ver versión del servicio
```
root@kali:~# nmap -sV <IP/RED>
```
- Enumerar mediante ICMP
```
root@kali:~# nmap -sC <IP/RED>
```

#### **HYDRA**
La idea de este tipo de ataque es tener un probar (por la fuerza) una conexión valida a algún servicio.

- Fuerza Bruta con usuario conocido
```
root@kali:~# hydra -t <NUMERO DE CONEXIÓN PARALELA> -l <USUARIO> -P <ARCHIVO CON PASS> -s <PUERTO> <URL> <SERVICIO>
```
- Fuerza Bruta con lista de usuarios
```
root@kali:~# hydra -t <NUMERO DE CONEXIÓN PARALELA> -L <ARCHIVO CON USUARIO> -P <ARCHIVO CON PASS> -s <PUERTO> <URL> <SERVICIO>
```

#### **MetaSploit**
La idea es poder ejecutar exploit conocidos a una máquina víctima, para ello este framework posee varios módulos como (explotación, post explotación, auxiliares, codificadores).
- Buscar Vulnerabilidad/exploit
```
msf6 > search <DATO A BUSCAR>
```
- Ejecutar Vulnerabilidad/exploit
```
msf6 > use <PATH DE VULNERABILIDAD>
<SETEAR VARIABLES>
msf6 > run
- Setear Variables
```
msf6 > SET <OPCIÓN> <VALOR>
```

#### **JOHN THE RIPPER**
- Saber el tipo de hash
```
root@kali:~# hash-identifier <HASH>
   #########################################################################
   #     __  __                     __           ______    _____           #
   #    /\ \/\ \                   /\ \         /\__  _\  /\  _ `\         #
   #    \ \ \_\ \     __      ____ \ \ \___     \/_/\ \/  \ \ \/\ \        #
   #     \ \  _  \  /'__`\   / ,__\ \ \  _ `\      \ \ \   \ \ \ \ \       #
   #      \ \ \ \ \/\ \_\ \_/\__, `\ \ \ \ \ \      \_\ \__ \ \ \_\ \      #
   #       \ \_\ \_\ \___ \_\/\____/  \ \_\ \_\     /\_____\ \ \____/      #
   #        \/_/\/_/\/__/\/_/\/___/    \/_/\/_/     \/_____/  \/___/  v1.2 #
   #                                                             By Zion3R #
   #                                                    www.Blackploit.com #
   #                                                   Root@Blackploit.com #
   #########################################################################
--------------------------------------------------

Possible Hashs:
[+] <HASH1>
[+] <HASH2>

Least Possible Hashs:
[+] <HASH3>
[+] <HASH4>
--------------------------------------------------
```

- Listar formato
```
root@kali:~# john –list=formats
```
- Revisar hash en un diccionario
```
root@kali:~# john --format=<FORMATO HASH> --wordlist=<diccionario> <archivo hash>
```
- Revisar password
```
root@kali:~# john --show <archivo hash>
```

#### **WIRESHARK**
Analizar lo que pasa en la red permite entender lo que ocurre dentro de nuestra red, capturando los paquetes que se transmiten.
Una de las mejores herramientas que existe actualmente es Wireshark y simplemente hay que empezar a filtrar los parámetros. Todo filtro puede ser concatenado con &&. Para saber sobre otros filtros puede visitar <a href="https://www.wireshark.org/docs/wsug_html_chunked/ChWorkBuildDisplayFilterSection.html" target="_blank">https://www.wireshark.org/docs/wsug_html_chunked/ChWorkBuildDisplayFilterSection.html</a> 

- Buscar contraseñas
```
http.request.method == POST
http contains “<PALABRAS>”
```
>los id para claves más utilizados son pwd, pass, password.
- Detectar Sysflood
```
tcp.flags.syn == 1 and tcp.flags.ack == 0
```
   
#### **FUZZING (WFUZZ)**
La idea es buscar carpetas/archivos en paginas web
   
- Búsqueda simple
```
root@kali:~# wfuzz –hc <FILTROS PARA CÓDIGOS HTTP> -w <DICCIONARIO> <URL>
> EN LA URL SE DEBERÁ AGREGAR EL VALOR FUZZ PARA QUE ESTE SEA REMPLAZADO POR LA PALABRA EN EL DICIONARIO
```
- Búsqueda varias variables 
```
root@kali:~# wfuzz –hc <FILTROS PARA CÓDIGOS HTTP> -w <DICCIONARIO> -w <DICCIONARIO2> <URL>
> SIGUIENDO LA LOGICA DE LA BUSQUEDA SIMPLE SE DEBE AGRENAR FUZZ, FUZ2Z, FUZ3Z,…, FUZnZ Y AGREGAR TODOS LOS DICCIONARIOS NECESARIOS
```
- Mediante Post
```
root@kali:~# wfuzz –hc <FILTROS PARA CÓDIGOS HTTP> -w <DICCIONARIO> -w <DICCIONARIO 2> -d "uname=FUZZ&pass=FUZ2Z" <URL>
```
- Especificar una cookie
```
root@kali:~# wfuzz –hc <FILTROS PARA CÓDIGOS HTTP> -w <DICCIONARIO> -b cookie2=value2 <URL>
```
- Especificar una cookie
```
root@kali:~# wfuzz –hc <FILTROS PARA CÓDIGOS HTTP> -w <DICCIONARIO> -H "myheader: headervalue" -H "myheader2: headervalue2" <URL>
```

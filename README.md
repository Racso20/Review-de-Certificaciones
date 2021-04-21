# CEH Practical v 10

### **Antedecentes**
Esta certificación corresponde a la certificación practica del Ethical Hacking de EC-Counsil y consiste en 20 preguntas del tipo Challenge/CTF. Este examen dura 6 horas desde que se inicia y lo que busca es demostrar que una persona sabe los conceptos prácticos al realizar un Ethical Hacking (identificar vectores de ataque, escanear redes, detectar S.O. detectar vulnerabilidades, realizar Pentest Web, entre otras cosas).
Preparación
Esta prueba presenta una dificultad entre básica y media por lo que con estudio se podrá rendir y pasar fácilmente. Para prepararse para esta prueba, primero debes entender los conceptos teóricos del Ethical Hacking (vuelva a ver los apuntes del CEH si los tiene, vea webinar al respecto), esto le ayudará a la hora de entender los ataques que está realizando.
Por otro lado, háganse una cuenta en Hack The Box, y practiquen con los challenge y máquinas que presenta esta plataforma (si quieren pueden pagar por la cuenta VIP ya que pueden acceder a maquinas retiradas y revisar los WriteUp). También pueden hacerlo con Vulnhub, Tryhackme o Hackzone que son página con la misma temática. También puede entrar a las academias de Hack de Box donde te capacitan en diversos temas de ciberseguridad. 

### **Reglas del Examen**
#### Para rendir el Examen
1.	No apagar la cámara en ni un momento (El Proctor debe poder verte durante todo momento)
2.	Siempre debe estar el micrófono encendido.
3.	Debes estar solo en la habitación.
4.	El espacio de trabajo debe estar limpio (No se pueden tener papeles, apuntes etc.)
5.	No se permite el uso de audífonos
6.	No se puede levantar del asiento mientras dure el examen
7.	No puede tener dos o más monitores conectados
#### Del CEH-P
1.	Solo puede acceder a recursos web dentro de las máquinas entregadas
2.	Puede acceder a los apuntes entregado por EC-COUNSIL (están dentro de las máquinas atacantes)
3.	No se permite hablar con nadie, ya sea directa o indirectamente
4.	Si necesita pararse o estirarse, puede hacerlo, pero sin salir de área de la cámara
5.	Se permite 15 min de descanso
6.	Puede hacer clic en "Guardar y cerrar" utilizando el botón situado en la esquina superior derecha de la pantalla de su examen en caso de que nos desconectemos en cualquier momento. Su prueba se puede reanudar sin perder tiempo.

### **EL EXAMEN**
Dispone de 20 preguntas y se aprueba con un 70% de preguntas buenas (14 preguntas buenas). Para ello una persona tiene hasta 6 horas para completar los diferentes desafíos. La idea principal es demostrar que pueden dominar las técnicas, herramientas y vectores de ataque más importantes aprendidos en C | EH y, al mismo tiempo, demostrar sus habilidades para hacer frente a evaluaciones de vulnerabilidad de la vida real y escenarios de Ethical Hacking.

#### ***Maquinas***
Para rendir este examen te darán 2 máquinas atacantes (Kali y Windows Server) con diversas herramientas para poder rendir el examen, no es necesario usar otras herramientas, con las que te dan en las maquinas basta.
Por otro lado, hay 4 máquinas victimas (Linux y Windows) donde tendrás diferentes servicios corriendo y nos harán diferentes preguntas

#### **Habilidades mínimas**
- Esteganografía
- SQL injection
- Criptografía
- Escaneo de red (Sniffing)
- Escaneo de vulnerabilidades
- Enumeración
- CVE

### **HERRAMIENTAS**
Dentro de las herramientas que se utilizará para resolver este examen tenemos.

- Nmap
- Hydra
- Sqlmap
- Wpscan
- Nikto
- John the Ripper
- Hashcat
- Metasploit
- Responder LLMNR
- Wireshark or Tcpdump
- Steghide
- OpenStego
- QuickStego
- Dirb
- Searchsploit
- Crunch
- Cewl
- Veracrypt
- Hashcalc
- Rainbow Crack

#### **PASSWORD**
•	Saber el tipo de hash
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

•	Listar formato
```
root@kali:~# john –list=formats
```
•	Revisar hash en un diccionario
```
root@kali:~# john --format=<FORMATO HASH> --wordlist=<diccionario> <archivo hash>
```
•	Revisar password
```
root@kali:~# john --show <archivo hash>
```

#### **Enumeración**
La idea es encontrar puertos abiertos, sistemas operativos, servicios. Para ello se puede usar Nmap. La ventaja de Nmap es que se puede combinar las consultas realizadas, permitiendo agilizar el escaneo dentro de la red víctima. Si quieren guardar lo obtenido en los escaneo se puede utilizar `-oN <ARCHIVO SALIDA>`
   
•	Ver Sistema Operativo
```
root@kali:~# nmap -O <IP/RED>
```
•	Ver hosts con puerto abierto
```
root@kali:~# nmap -p <PUERTO> <RED>
```
•	Ver versión del servicio
```
root@kali:~# nmap -sV <IP/RED>
```
•	Enumerar mediante ICMP
```
root@kali:~# nmap -sC <IP/RED>
```

#### **Modificación de Archivos**
En varias ocasiones se han modificado archivos, una opción es revisar el hash de cada archivo y compararlo con los hashes que se tienen antes de que sean modificado. Para ello hay varias formas tanto por entorno grafico como para consola. Esta guía mostrará el uso del comando rhash

•	Listar hashes
```
root@kali:~# rhash -a --bsd <ARCHIVO>
```
> Si queremos buscar simplemente hay que agregar un grep con el hash a buscar.

#### **Base de datos**
Las bases de datos son importantes, ya que en ella los administradores alojan los datos que serán procesados por los sistemas.

•	Listar Base de datos
```
root@kali:~# sqlmap -u <URL CON VALUE GET> --dbs
```
•	Listar Tablas
```
root@kali:~# sqlmap -u <URL CON VALUE GET> -D <BASE DE DATO> --tables
```
•	Listar Columnas
```
root@kali:~# sqlmap -u <URL CON VALUE GET> -D <BASE DE DATO> -T <TABLA> --columns
```
•	Mostrar datos
```
root@kali:~# sqlmap -u <URL CON VALUE GET> -D <BASE DE DATO> -T <TABLA> -C <COLUMNAS SEPARADAS POR ,> --dump
```

#### **Wordpress**
Es un sistema de gestión de contenidos, enfocado a la creación de cualquier tipo de página web. Actualmente es utilizado para realizar contenido web dentro de usuarios y empresas.

•	Listar usuarios
```
root@kali:~# wpscan --url <URL > --enumerate u
```
•	Revisar password
```
root@kali:~# wpscan --url <URL > --passwords <ARCHIVO CLAVE> --usernames <USUARIO>
```


#### **Rainbow Attack**
La idea de este tipo de ataque es tener un gran archivo (indexado) con los hashes de las contraseñas, lo que permite al atacante comparar hashes y no encriptar buscar palabras y compararlas con los hashes optimizando el proceso.

•	Generar Listado Rainbow
```
root@kali:~# rtgen <TIPO HASH> <CARACTERES> <MIN LENGHT PASS> <MAX LENGHT PASS> <INDICE> <LOGITUD DE CADENA> <NUMERO DE CADENAS> <NUMERO DE PART>
```
•	Ordenar e Indexar archivo Rainbow
```
root@kali:~# rtsort <ARCHIVO>
```
•	Buscar password
```
root@kali:~# rcrack <ARCHVIO> -h <HASH>
root@kali:~# rcrack <ARCHVIO> -l <ARCHIVO CON HASHES>
```

#### **Fuerza Bruta**
La idea de este tipo de ataque es tener un probar (por la fuerza) una conexión valida a algún servicio.

•	Fuerza Bruta con usuario conocido
```
root@kali:~# hydra -t <NUMERO DE CONEXIÓN PARALELA> -l <USUARIO> -P <ARCHIVO CON PASS> -s <PUERTO> <URL> <SERVICIO>
```
•	Fuerza Bruta con lista de usuarios
```
root@kali:~# hydra -t <NUMERO DE CONEXIÓN PARALELA> -L <ARCHIVO CON USUARIO> -P <ARCHIVO CON PASS> -s <PUERTO> <URL> <SERVICIO>
```

#### **Generación de Diccionario**
Dentro de las herramientas que posee Kali, tenemos CEWL la que nos permite generar diccionarios a partir de algún sitio web (capturando las palabras únicas dentro del sitio) y se puede generar patrones de búsqueda.

•	Generar Diccionario genérico
```
root@kali:~# cewl <URL> -w <ARCHIVO A GUARDAR>
root@kali:~# cewl <URL> -w <ARCHIVO A GUARDAR> -m <LARGO DE LAS PALABRAS>
```
•	Diccionario con correos
```
root@kali:~# cewl <URL> -w <ARCHIVO A GUARDAR> -m -e
```

#### **Analizar paquetes de red**
Analizar lo que pasa en la red permite entender lo que ocurre dentro de nuestra red, capturando los paquetes que se transmiten.
Una de las mejores herramientas que existe actualmente es Wireshark y simplemente hay que empezar a filtrar los parámetros. Todo filtro puede ser concatenado con &&. Para saber sobre otros filtros puede visitar https://www.wireshark.org/docs/wsug_html_chunked/ChWorkBuildDisplayFilterSection.html

•	Buscar contraseñas
```
http.request.method == POST
http contains “<PALABRAS>”
```
>los id para claves más utilizados son pwd, pass, password.
•	Detectar Sysflood
```
tcp.flags.syn == 1 and tcp.flags.ack == 0
```

### **Videos relacionados**
•	[Partyhack | ¿Como rendir el CEH Practical y no morir en el intento?](https://www.youtube.com/watch?v=pjlV-n43sns)

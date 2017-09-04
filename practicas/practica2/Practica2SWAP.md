# Práctica 2 SWAP.
# Juan Anaya Ortiz.

En ésta práctica aprenderemos a copiar archivos mediante ssh y a clonar contenido entre máquinas, entre otras cosas.
Lo primero que debemos hacer es configurar una Red Nat para poder conectar las dos máquinas. Lo vemos en las siguientes imágenes:
Primero creamos la Red Nat en las preferencias de VB:
! [img1] 
Después, asignamos dicha red en el adaptador de nuestras 2 máquinas:
! [img2] 
Como podemos ver en la siguiente imagen, las dos máquinas están perfectamente conectadas al hacer ping la una a la otra y viceversa:

! [img3]

Ahora pasemos con la práctica en sí:
 
Primero de todo, instalamos la herramienta rsync con el siguiente comando:

```sh
$ sudo apt-get install rsync
```

Después de ello, para trabajar con rsync hacemos que el usuario sea el dueño de la carpeta donde residen los archivos que hay en el espacio web.En nuestro caso:

```sh
$ sudo chown jaochaos:jaochaos –R /var/www
```

Ahora, para hacer una prueba:
```sh
$ rsync -avz -e ssh ipmaquina1:/var/www/ /var/www/
```

La prueba es exitosa como comprobamos en la imagen.
! [img4]

Una vez que sabemos usar la herramienta rsync, pasamos al siguiente punto de la práctica; configurar ssh para acceder a la otra máquina sin contraseña.


Para ello, primero debemos generar una contraseña ssh en nuestra máquina principal:

```sh
$ ssh-keygen -b 4096 -t rsa
```

![img5]

Tras haber hecho ésto, nos aparecerán unas instrucciones que, personalmente, he dejado en blanco tal y como dice en el guión de la práctica.

Para acabar, debemos copiar la contraseña en nuestro servidor al que vamos a hacer las peticiones:

```sh
$ ssh-cpy-id 10.0.2.4
```
! [img6]
Tras ésto, probamos que todo haya salido bien:

! [img7]

Para acabar la práctica, vamos a programar una tarea con el administrador de procesos "cron":

Para ello, editamos el archivo /etc/crontab y lo dejamos tal que así:

! [img8]

[img1]: github.com/JaoChaos/SWAP/blob/master/practicas/practica2/captura1.jpg
[img2]: github.com/JaoChaos/SWAP/blob/master/practicas/practica2/captura2.jpg
[img3]: github.com/JaoChaos/SWAP/blob/master/practicas/practica2/captura3.jpg
[img4]: github.com/JaoChaos/SWAP/blob/master/practicas/practica2/captura4.jpg
[img5]: github.com/JaoChaos/SWAP/blob/master/practicas/practica2/captura5.jpg
[img6]: github.com/JaoChaos/SWAP/blob/master/practicas/practica2/captura6.jpg
[img7]: github.com/JaoChaos/SWAP/blob/master/practicas/practica2/captura7.jpg
[img8]: github.com/JaoChaos/SWAP/blob/master/practicas/practica2/captura8.jpg
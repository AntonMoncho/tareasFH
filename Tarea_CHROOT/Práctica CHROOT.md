Nesta práctica utilizarase una máquina Debian 12.10 na que se creará o usuario “administrador” con contraseña “abc123.”. Posteriormente, sobre esta máquina introduciremos e iniciaremos unha imaxe Live de Kali Linux, que se usará para montar os ficheiros raíz do Debian, por medio de “chroot”,  e “recuperarase” o contrasinal do usuario de Debian.  

# Instalación da máquina Debian  

![image1](images/image1.png)

![image2](images/image2.png)

![image3](images/image3.png)

Unha vez instalado o sistema Debian, apagaremos a máquina e insertarase como unha unidade óptica a ISO Live de Kali:  

![image4](images/image4.png)  

![image5](images/image5.png)  

![image6](images/image6.png)  

# Inicio con Kali  

Ahora volveremos a arrancar a máquina e, se non se inicia automáticamente o Kali, xusto cando se arranque a máquina virtual pulsaremos F12 e escolleremos a opción arrancar dende o CD-ROM.  

![image7](images/image7.png)  

![image8](images/image8.png)  

Iniciamos dende o instalador de Kali, xa que arranca un Live.  

Poñenos a distribución do teclado en castelán 

```bash
setxkbmap es
```

Iniciamos sesión como root “sudo su \-”  

Executamos “mount” ou “df \-Th” para ver que discos están conectados ao equipo.  

Facemos “ls /dev” para buscar os dispositivos conectados ao equipo e buscamos os “sdX”, que serán os discos nos que estaba instalado o Debian sobre o que estamos correndo o live de Kali, neste caso sabemos que está instalado no disco **sda**.  

![image9](images/image9.png)

Usaremos “CHROOT” para modificar o directorio raíz do live do kali para cargar o sistema de ficheiros do Debian (/dev/sda), e para eso imos crear unh directorio na ruta onde imos montar a información 

```bash
mkdir /mnt/recuperar && ls -ld /mnt/recuperar
```  

Despois montamos o disco dev/sda1 en /mnt/recuperar  

![image10](images/image10.png)  

![image11](images/image11.png)

Ahora vemos que temos a raíz do debian en /mnt/recuperar  

Para poder usar como raíz o directorio /recuperar, precisamos montar os directorios “**/proc**”, “**/sys**” e ”**/dev**” do Kali dentro da carpeta /recuperar. Facendo o proceso de montaxe.  

![image12](images/image12.png)  

Ahora usamos o comando  

```bash
chroot /mnt/recuperar /bin/bash
```

![image13](images/image13.png)  

Podemos comprobar que os ficheiros nos que estamos son os do Debian, vendo, por exemplo os usuarios do ficheiro /etc/passwd  
![image14](images/image14.png)  
Vendo que somos root en Debian, podendo cambiarlle a contraseña ao usuario do debian:  

antes “abc123.” e ahora “ABC123.”  

![image15](images/image15.png)  

Ahora volvemos a arrancar o Debian, quitando o disco do Kali para que arranque Debian.  

Ahora para iniciar sesión en debian teremos que poñer a contraseña que cambiamos dende o Kali.  

![image16](images/image16.png)

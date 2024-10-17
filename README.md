# Tarea 3 SXE

## 1.Descarga la imagen 'httpd' y comprueba que está en tu equipo.

Para descargar la imagen de httpd (Apache 2.4) en mi equipo utilicé:
```bash
docker pull httpd:2.4
```
Esto lo descargó de la librería y para comprobar que estaba en mi equipo: 
```bash
docker images
```

## 2.Crea un contenedor con el nombre 'dam_web1'.

Para crear un contenedor con el ese nombre se utiliza:
```bash
docker run -it --name dam_web1 httpd:2.4
```
Con este comando entra automáticamente también a la pseudo-terminal creada con el comando -it.

Si queremos verificar también que está bien creado:
```bash
docker ps -a
```
o si el contenedor está activo:
```bash
docker ps
```

## 3.Si quieres poder acceder desde el navegador de tu equipo, ¿que debes hacer? Utiliza bind mount para que el directorio del apache2 'htdocs' esté montado un directorio que tu elijas.

Para realizar esto tenemos que parar el contenedor actual y eliminarlo con
```bash
docker stop dam_web1
```
```bash
docker rm dam_web1
```
Una vez eliminado se tiene ejecutar el siguiente comando para hacer el bind mount en un directorio de nuestra máquina virtual
```bash
docker run -d --name dam_web1 -p 8080:80 -v /home/accesodatos/SXE/WebApache:/usr/local/apache2/htdocs httpd:2.4
```
De esta manera se puede acceder a mi servidor web desde el navegador y montar mi directorio local en el directorio de Apache

## 4.Realiza un 'hola mundo' en html y comprueba que accedes desde el navegador.

Se crea un archivo .html con un Hola mundo en el directorio en el que se hizo el bind mount con el siguiente comando:
```bash
echo "<html><body><h1>Hola Mundo</h1></body></html>" >/home/accesodatos/SXE/WebApache/index.html
```
En mi caso añadí mi web creada el año pasado para poder acceder a ella.

Y para poder acceder a ella se pone el siguinete enlace en nuestro navegador web:
```bash
http://localhost:8080
```

## 5.Crea otro contenedor 'dam_web2' con el mismo bind mount y a otro puerto, por ejemplo 9080.

Para crear otro contenedor, en el mismo bind mount y en otro puerto se ejecuta el comando usado anteriormente:

```bash
docker run -d --name dam_web2 -p 9080:80 -v /home/accesodatos/SXE/WebApache:/usr/local/apache2/htdocs httpd:2.4
```
## 6.Comprueba que los dos servidores 'sirven' la misma página, es decir, cuando consultamos en el navegador.

Cuando usamos ambos enlances en el navegador web:
```bash
http://localhost:8080
```
```bash
http://localhost:9080
```
Lo que ocurre es que con ambos se accede a la misma página.

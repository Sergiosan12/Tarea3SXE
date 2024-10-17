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

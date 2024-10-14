# Practica_Nginx

# Práctica: Configuración de Servidores Web con Nginx en Contenedores Docker

## 1. Título:
**Creación y Configuración de Contenedores Nginx para Servir Sitios Web Personalizados**

## 2. Tiempo de duración:
**120 minutos**

## 3. Fundamentos:

El uso de contenedores Docker y servidores web como Nginx es fundamental para el desarrollo moderno de aplicaciones. Docker permite crear ambientes aislados donde los desarrolladores pueden desplegar aplicaciones de manera rápida y eficiente. Nginx, un servidor web y proxy inverso, es ampliamente utilizado por su capacidad de servir contenido de manera eficiente y manejar grandes cantidades de conexiones concurrentes.

### Docker
Docker es una plataforma que permite a los desarrolladores empaquetar aplicaciones y sus dependencias en contenedores ligeros. Estos contenedores son entornos de ejecución aislados que incluyen todo lo necesario para que una aplicación funcione: código, bibliotecas, y configuraciones. Esto asegura que una aplicación funcione de manera consistente, independientemente del sistema operativo o de otras configuraciones del entorno.

### Nginx
Nginx es un servidor web de alto rendimiento que puede ser utilizado para servir contenido estático, balanceo de carga y proxy inverso. Es altamente eficiente en el manejo de múltiples solicitudes simultáneas, lo que lo convierte en una elección ideal para aplicaciones escalables.

### Imágenes Docker y Volúmenes
Una imagen de Docker es una plantilla inmutable que define cómo se debe crear un contenedor. Se puede configurar para incluir aplicaciones como Nginx y sus archivos de configuración. Los volúmenes de Docker permiten persistir datos fuera de los contenedores, de modo que la información importante (como archivos de configuración de Nginx o contenido del sitio web) no se pierda al eliminar el contenedor.

![Docker y Nginx](https://example.com/docker-nginx-image)  
_Figura 1-1: Arquitectura de Docker y Nginx_

## 4. Conocimientos previos:
Para realizar esta práctica el estudiante necesita tener conocimientos básicos en:
- **Comandos básicos de Docker**
- **Conceptos de redes y servidores web**
- **Manejo de navegadores para verificar los sitios web**

## 5. Objetivos a alcanzar:
- Implementar contenedores utilizando **Docker**.
- Configurar dos contenedores con **Nginx** para que sirvan diferentes sitios web.
- Manipular archivos de configuración de Nginx dentro de los contenedores.

## 6. Equipo necesario:
- Computadora con **Windows/Linux/MacOS**.
- **Docker** instalado (versión recomendada: 20.x o superior).
- Editor de texto para modificar archivos de configuración.
- Conexión a internet para descargar imágenes de Docker.

## 7. Material de apoyo:
- [Documentación oficial de Docker](https://docs.docker.com).
- Guía de la asignatura sobre contenedores.
- [Cheat sheet de comandos Linux](https://example.com/linux-cheatsheet).

## 8. Procedimiento:

### Paso 1: Instalación de Docker
Asegúrate de que Docker esté instalado en tu equipo siguiendo la documentación oficial según tu sistema operativo.

### Paso 2: Descargar la imagen de Nginx
Ejecuta el siguiente comando para descargar la imagen oficial de Nginx:
```
docker pull nginx
```
### Paso 3: Crear la estructura de los sitios web

Crea dos directorios locales para alojar los archivos HTML de cada sitio web:

```bash
mkdir -p ~/nginx-site1 ~/nginx-site2
```
En cada directorio, crea un archivo index.html con el contenido personalizado para cada sitio.

```bash
<html>
  <body>
    <h1>Bienvenido al sitio de Jonnathan</h1>
  </body>
</html>
```
### Paso 4: Configurar los contenedores Nginx
Crea un archivo de configuración para cada contenedor Nginx
```bash
server {
  listen 80;
  server_name localhost;
  root /usr/share/nginx/html;
  index index.html;
}
```
### Paso 5: Iniciar los contenedores
Utiliza los siguientes comandos para crear y ejecutar dos contenedores con los sitios web configurados:
```bash
- docker run --name site1 -v ~/nginx-site1:/usr/share/nginx/html:ro -p 8081:80 -d nginx
- docker run --name site2 -v ~/nginx-site2:/usr/share/nginx/html:ro -p 8082:80 -d nginx
```
### Paso 6: Verificar en el navegador
Abre un navegador web y visita los sitios:
```bash
- http://localhost:8081 mostrará el sitio 1.
- http://localhost:8082 mostrará el sitio 2.
```
### Resultados esperados
Al finalizar la práctica, deberías tener dos contenedores Nginx ejecutándose en tu máquina, 
cada uno sirviendo un sitio web personalizado. Deberías poder acceder a cada sitio web desde el
navegador mediante los puertos correspondientes.

### Bibliografia

- Apellido, N. (2023). *Guía de Docker y Nginx*. Editorial de Tecnología.
- Docker Inc. (2023). Documentación oficial de Docker. Recuperado de [https://docs.docker.com](https://docs.docker.com).

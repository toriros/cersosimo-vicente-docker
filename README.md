# TP Docker — MySQL + Java App Server
## Datos del alumno
- Toribio Martin Rosendi
## 1. ¿Qué es Docker?
  Docker es una plataforma que permite crear y ejecutar aplicaciones dentro de contenedores, asegurando que funcionen igual en cualquier entorno. Su principal ventaja es el aislamiento, la portabilidad y el bajo consumo de recursos frente a una máquina virtual.
## 2. Volúmenes en Docker
  Los volúmenes permiten guardar datos de forma persistente aunque el contenedor se elimine o reinicie. Son fundamentales para bases de datos porque evitan la pérdida de información.
## 3. Redes en Docker
  Las redes permiten que los contenedores se comuniquen entre sí usando nombres internos como mysql o payara. Esto facilita la conexión entre servicios de manera segura y organizada.
## 4. ¿Por qué Payara Server?
  Payara Server se utiliza porque es un servidor compatible con Jakarta EE y está optimizado para aplicaciones empresariales Java. Además, se integra fácilmente con Docker y permite desplegar aplicaciones .war de forma sencilla.
## 5. Explicación del docker-compose.yml
  El archivo docker-compose.yml define y configura los contenedores necesarios para la aplicación, como MySQL y Payara. También permite configurar puertos, redes, volúmenes y dependencias entre servicios.
## 6. Explicación del init.sql
  El archivo init.sql contiene instrucciones SQL que crean tablas e insertan datos iniciales automáticamente al iniciar MySQL. Esto ayuda a preparar la base de datos sin configuraciones manuales.
## 7. Dificultades y soluciones
  Uno de los principales problemas fue la conexión entre Payara y MySQL, solucionado usando el nombre del contenedor como host en la URL JDBC. También hubo problemas de persistencia y puertos ocupados, resueltos mediante volúmenes Docker y cambios en los puertos configurados.


# Capturas de Pantalla Obligatorias

## **Parte 1 — Infraestructura Docker (5 capturas)**

## 1. Salida de docker --version y docker info en la terminal
![Versión de Docker](capturas/01-docker-version.png)
## 2. Salida de docker network ls mostrando la red java-net
![Red creada](capturas/02-red-creada.png)
## 3. Salida de docker volume inspect mysql-data
![Volumen MySQL](capturas/03-volumen-creado.png)
## 4. Salida de docker ps con ambos contenedores activos
![Contenedores activos](capturas/04-contenedores-corriendo.png)
## 5. docker network inspect java-net con ambos contenedores en la red
![Inspección de red](capturas/05-network-inspect.png)

## **Parte 2 — MySQL (3 capturas)**
## 6. Logs de MySQL mostrando: ready for connections
![Logs de MySQL](capturas/06-mysql-logs.png)
## 7. Salida de SHOW DATABASES; mostrando la base appdb
![Bases de datos](capturas/07-mysql-databases.png)
## 8. Salida de SELECT * FROM usuarios; con los datos del init.sql
![Datos de usuarios](08-mysql-tabla.png)

## **Parte 3 — Payara Admin Console / GUI (5 capturas)**
## 9. Pantalla de login de Admin Console en http://localhost:4848
![Login de Admin Console](capturas/09-payara-login.png)
## 10. Dashboard principal de Payara tras iniciar sesión
![Dashboard de Payara](capturas/10-payara-dashboard.png)
## 11. Pantalla del Connection Pool MySQLPool creado
![Connection Pool MySQLPool](capturas/11-connection-pool.png)
## 12. Resultado del botón Ping mostrando conexión exitosa a MySQL
![Ping a MySQL](capturas/12-ping-exitoso.png)
## 13. JDBC Resource jdbc/MySQLDS visible en la consola
![JDBC Resource](capturas/13-jdbc-resource.png)

## Parte 4 — Conectividad entre contenedores (1 captura)
## 14. Salida del ping de Payara hacia mysql-container desde la terminal
![Ping de Payara a MySQL](capturas/14-ping-contenedores.png)



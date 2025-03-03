# Práctica de despliegue con Docker

## Punto de partida

- Usa la máquina: "Practicas Docker Ubuntu"
- Borra todos los contenedores e imágenes:

  ```bash
  docker rm -f $(docker ps -aq)
  docker rmi -f $(docker images -aq)
  ```
![alt text](1.png)
## Objetivo

- Debes desplegar las siguientes aplicaciones:
  - https://github.com/rafacabeza/demoapinode
  - https://github.com/rafacabeza/demoappphp
- Debes usar un contenedor con un proxy.
- Debes usar un contenedor por cada aplicación y dos contenedores de bases de datos.
- Opcionalmente puedes usar contenedores para phpmyadmin
- Las aplicaciones serán app1.local y app2.local.

## Desarrollo de la práctica

- Para hacerlo debes usar un único fichero docker-compose.yml teniendo en cuenta lo siguiente:
  - Inicia el proceso clonando el repositorio entornods(https://github.com/rafacabeza/entornods)
  ![alt text](2.png)
  - Elimina el servicio web1
  ![alt text](3.png)
  - Comprueba que funciona correnctamente el sitio web2.com (deberas editar el fichero hosts)
  ![alt text](4.png)
  ***
  ![alt text](5.png)
  ***
  ![alt text](6.png)
  - Deja una única red (network) en todos los contenedores. Llámale como consideres.
  ![alt text](7.png)

### Sitio app1.local

- Añade un servicio db1 (puedes renombrar el servicio db como db1)
  - El volumen de datos debe llamarse volumen1 y debe gestionarlo docker
  - Debes usar una base de datos llamda dbapp1 
  - Debes usar un usuario user1 y contraseña secret
  ![alt text](8.png)
  ***
  ![alt text](20.png)
  - Carga el sql correspondiente. Puedes hacerlo con phpmyadmin o mediante consola (docker exec -it <contenedor> mysql ....).
  ![alt text](9.png)
- Añade un servicio app1 para que sirva la aplicación "demoapinode". 
![alt text](19.png)
  - Descarga la aplicación en "entornods/demoapinode".
  ![alt text](10.png)
  - Fíjate en el docker-compose.yml que hay en el repositiro, te ayudará a definir el servicio en tu docker-compose pero deberás modificar algunas cosas.
  - Deberás añadir en variable de entorno "VIRTUAL_HOST", fíjate en web2
  - Revisa el resto de parámetros
- Comprueba que funciona la ruta: http://app1.local/api/deseos
![alt text](18.png)

### Sitio app2.local

- Añade un servicio db2 para la base de datos de "demoappphp"
  - El volumen de datos debe llamarse volumen2 y debe gestionarlo docker
  - Debes usar una base de datos llamda dbapp2 
  - Debes usar un usuario user2 y contraseña secret
  - Carga el sql correspondiente. De nuevo, puedes usar phpmyadmin o la consola.
  ![alt text](12.png)
  ***
  ![alt text](13.png)
  ***
  ![alt text](16.png)
- Añade un servicio app2 que sirva la aplicación "demoappphp"
  - Descarga la aplicación en "entornods/demoappphp".
  ![alt text](14.png)
  - Fíjate en el docker-compose.yml que ha en repositorio, te ayudará a definir el servicio en tu docker-compose pero deberás modificar algunas cosas.
  - Deberás añadir en variable de entorno "VIRTUAL_HOST", fíjate en web2
- Comprueba que funciona la ruta: http://app2.local
![alt text](15.png)
***
![alt text](17.png)

### Un poco más de documentación. 

- Si te da tiempo, como tarea extra:
  - Muestra una lista de todos las redes y volúmenes  

    ```
    docker volume ls
    docker network ls
    ```

- Identifica la red y volúmenes utilizados y captura los datos de los mismos:

    ```
    docker inspect <nombre-volumen>
    docker inspect <nombre-red>
    ```

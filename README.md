# Despliegue de proyecto en Docker.

## Procedimiento

Para poder comenzar a deplegar el nuestro proyecto en el docker necesitaremos descargar el docker y docer-compose.
En mi caso tengo sistema operativo window 10, no necesito descargarme el docker compose porque Docker Desktop lo tiene preinstalado el plugin.

![](https://github.com/ZhijunLin7/Despliegue-de-proyecto-en-Docker./blob/main/Camera%20Roll/1.1.PNG)

Para nuestro proyecto es necesario 3 contenedores uno mysql para almacenar informacion, phpmyadmin para poder acceder al base de datos, tomcat para ejecutar aplicacion web.

Para poder levantar estos 3 contenedores y relacionar entre ellos, necesitamos crear un documento .yml .

![](https://github.com/ZhijunLin7/Despliegue-de-proyecto-en-Docker./blob/main/Camera%20Roll/1.2.PNG)

He creado este .yml dentro de carpeta de nuestro proyecto con los siguientes servicios:

Base de datos: bd que utiliza un imagen mysql habra un volumen para los datos en el contenedor y el puerto lo puse en 3308.
Phpmyadmin depende de bd en el puerto 8081 la contraseña de root es root para acceder al base de datos con interfaz grafica.
tomcat donde instalara el nuestro web app tambien depende de bd y esta en el puerto 8082 ademas necesitamos indicar donde esta el .war de nuestro proyecto para que lo meta dentro de contenedor.

![](https://github.com/ZhijunLin7/Despliegue-de-proyecto-en-Docker./blob/main/Camera%20Roll/1.3.PNG)


Al tener todo esto podemos utilizar comando para ejecutar docker-compose situando en la carpeta donde esta el .yml.
~~~
docker-compose up -d
~~~

![](https://github.com/ZhijunLin7/Despliegue-de-proyecto-en-Docker./blob/main/Camera%20Roll/1.4.PNG)

Y ahora podemos ir en el navegador al localhost:8081 para acceder al phpmyadmin y al localhost:8082 para el web.

![](https://github.com/ZhijunLin7/Despliegue-de-proyecto-en-Docker./blob/main/Camera%20Roll/1.5.PNG)
![](https://github.com/ZhijunLin7/Despliegue-de-proyecto-en-Docker./blob/main/Camera%20Roll/1.6.PNG)

Si el tomcat sale esto error 404 no encontrado lo que podemos hacer es añadir nombre del .war para llegar al proyecto.
El URL sera http://localhost:8082/demo/ (el nuestro .war se llama demo).

![](https://github.com/ZhijunLin7/Despliegue-de-proyecto-en-Docker./blob/main/Camera%20Roll/1.7.PNG)

Para poder hacer imagen con el docker compose necesitaremos dockerfile


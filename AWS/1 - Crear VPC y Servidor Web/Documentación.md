Desplegar un *servidor web* puede ser una de las acciones que más se realiza para levantar *páginas web*. 
En **AWS** es necesaria cierta infraestructura para poder tener una *página web* la que consta de:
1. Virtual Private Cloud (VPC): Para aislar los recursos a utilizar.
2. Subredes: Para dividir el entorno de acceso publico al de acceso privado.
3. Internet Gateway: Para crear una conexión a internet.
4. Tablas de Enrutamiento: Para administrar el tráfico de red.
5. Grupos de Seguridad: Firewall que protege a las instancias.
6. Instancia Elastic Compute Cloud (EC2): En donde se alojara el servidor web.

![00EsquemaVPCServidorWeb]()

# Crear una VPC
La creación de VPC requiere de comprender como se realiza la [segmentación de red], que puede ser un tanto complejo de entender.
En este caso se utilizara la `IP 10.0.0.0` y el bloque `CIDR /16`.

![01CrearVPC](https://github.com/Coalacanth/Portafolio/blob/main/Recursos/1%20-%20Im%C3%A1genes/01-Creaci%C3%B3n%20VPC.png)

# Crear Subred
Para la creación de la subred se necesita saber en que VPC se va a crear. 

![02.1Creación subred](https://github.com/Coalacanth/Portafolio/blob/main/Recursos/1%20-%20Im%C3%A1genes/02.1-Creaci%C3%B3n%20subred.png)

Es importante saber que la instancia EC2 al alojar un servidor web, debe estar en una subred pública.

![02.2Creación subred](https://github.com/Coalacanth/Portafolio/blob/main/Recursos/1%20-%20Im%C3%A1genes/02.2-Creaci%C3%B3n%20subred.png)

# Crear Internet Gateway
No requiere de configuración, pero es un componente necesario para tener acceso a internet y que los usuarios tengan acceso a la página web.

![03Creación Internet gateway](https://github.com/Coalacanth/Portafolio/blob/main/Recursos/1%20-%20Im%C3%A1genes/03-Creaci%C3%B3n%20Internet%20gateway.png)

Se tiene que conectar con la VPC, no olvidar.

![04ConectarIGWconVPC](https://github.com/Coalacanth/Portafolio/blob/main/Recursos/1%20-%20Im%C3%A1genes/04-Conectar%20Internet%20gateway%20con%20VPC.png)

# Crear Tablas de Enrutamiento
Se requiere de una VPC y es un componente que ayudara administrando el tráfico de red.

![05CrearTablaEnrutamiento](https://github.com/Coalacanth/Portafolio/blob/main/Recursos/1%20-%20Im%C3%A1genes/05-Creaci%C3%B3n%20Tabla%20de%20Enrutamiento.png)

# Configurar la Tabla de Enrutamiento
Se procede a asociar la tabla con la VPC.

![06EnrutarIGWVPC](https://github.com/Coalacanth/Portafolio/blob/main/Recursos/1%20-%20Im%C3%A1genes/06-EnrutarIGWyVPC.png)

Luego asociar la tabla con la subred.

![07EnrutarTablaSubred](https://github.com/Coalacanth/Portafolio/blob/main/Recursos/1%20-%20Im%C3%A1genes/07-AsociarTablaconSubred.png)

# Crear Grupo de Seguridad
El Grupo de Seguridad es un firewall que protege a las instancias EC2 que estén dentro, permitiendo o denegando el acceso a los puertos. Recordar que deniega todo por defecto.

![08CrearGrupoSeguridad](https://github.com/Coalacanth/Portafolio/blob/main/Recursos/1%20-%20Im%C3%A1genes/08-CrearGrupodeSeguridad.png)

Así mismo, debemos dar acceso a la instancia para que acepte tráfico de los puertos asociados a HTTP(80) y a HTTPS(443). Habilitare el puerto SSH(22) para que solo mi computador se conecte en caso de que sea necesario.

![09ReglasGrupoSeguridad](https://github.com/Coalacanth/Portafolio/blob/main/Recursos/1%20-%20Im%C3%A1genes/09-ReglasGrupodeSeguridad.png)

# Crear Instancia EC2
Utilizando la consola podemos configurar paso a paso la instancia EC2 a utilizar.

![10.1NombreEC2](https://github.com/Coalacanth/Portafolio/blob/main/Recursos/1%20-%20Im%C3%A1genes/10.1-NombreEC2.png)
![10.2AMI](https://github.com/Coalacanth/Portafolio/blob/main/Recursos/1%20-%20Im%C3%A1genes/10.2-AMIEC2.png)
![10.3Tipo](https://github.com/Coalacanth/Portafolio/blob/main/Recursos/1%20-%20Im%C3%A1genes/10.3-TipoEC2.png)
![10.4Llaves](https://github.com/Coalacanth/Portafolio/blob/main/Recursos/1%20-%20Im%C3%A1genes/10.4-CrearLlaves.png)
![10.5Llaves](https://github.com/Coalacanth/Portafolio/blob/main/Recursos/1%20-%20Im%C3%A1genes/10.5-AsociarLlaves.png)
![10.6VPCSubredGrupoSeguridad](https://github.com/Coalacanth/Portafolio/blob/main/Recursos/1%20-%20Im%C3%A1genes/10.6-AsociarVPCSubredGrupoSeguridad.png)
![10.7Alamcenamiento](https://github.com/Coalacanth/Portafolio/blob/main/Recursos/1%20-%20Im%C3%A1genes/10.7-Almacenamiento.png)

En los datos de usuario agregaremos un script bash para que configure el servidor web de prueba.

![10.8DatosdeUsuario](https://github.com/Coalacanth/Portafolio/blob/main/Recursos/1%20-%20Im%C3%A1genes/10.8-DatosUsuario.png)

# Pagina Web en Instancia EC2

![11Paginaweb](https://github.com/Coalacanth/Portafolio/blob/main/Recursos/1%20-%20Im%C3%A1genes/11-PaginaWeb.png)

# Conclusión
Es importante entender la arquitectura que tiene AWS para poder utilizar otros servicios como:
- CloudFormation, que requiere de este conocimiento para el lanzamiento de la pila.
- AWS CLI, otra forma de crear recursos en AWS.

Tambien es notable destacar que con Amazon S3 se puede albergar una página web en un bucket.

Otros servicios que pueden ayudar son:
- ACL, para mayor control de accesos a la red.
- Amazon Route 53, que nos permite utilizar un nombre de dominio (DNS) para que los usuarios no tengan que aprenderse la IP del sitio web.
- Amazon CloudFront, para entregar contenido rápidamente utilizando políticas de entrega de contenido.
- Elastic Load Balancer y AWS Auto scaling, útiles para crear alta disponibilidad de aplicaciones web más complejas.

Encuentro que es bueno saber este tipo de cosas que algunos pueden catalogar de básicas u obvias, pero para mi ese pensamiento es algo obtuso por el hecho de que nada es tan simple y siempre es bueno tener un buen fundamento de las bases con las que se trabaja en la nube.

[segmentación de red]: https://github.com/Coalacanth/Portafolio/blob/main/AWS/1%20-%20Crear%20VPC%20y%20Servidor%20Web/Segmentaci%C3%B3n%20de%20red.md
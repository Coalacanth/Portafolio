Desplegar un *servidor web* puede ser una de las acciones que más se realiza para levantar *páginas web*. 
En **AWS** es necesaria cierta infraestructura para poder tener una *página web* la que consta de:
1. Virtual Private Cloud (VPC): Para aislar los recursos a utilizar.
2. Subredes: Para dividir el entorno de acceso publico al de acceso privado.
3. Internet Gateway: Para crear una conexión a internet.
4. Tablas de Enrutamiento: Para administrar el tráfico de red.
5. Grupos de Seguridad: Firewall que protege a las instancias.
6. Instancia Elastic Compute Cloud (EC2): En donde se alojara el servidor web.

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

![06EnrutarIGWVPC]()

Luego asociar la tabla con la subred.

![07EnrutarTablaSubred]()

Con todo esto, tenemos configurada la red que se utilizara.

# Crear Grupo de Seguridad
El Grupo de Seguridad es un firewall que protege a las instancias EC2 que estén dentro, permitiendo o denegando el acceso a los puertos. Recordar que deniega todo por defecto.

!

# Crear Instancia EC2

# Conclusión

[segmentación de red]: https://github.com/Coalacanth/Portafolio/blob/main/AWS/1%20-%20Crear%20VPC%20y%20Servidor%20Web/Segmentaci%C3%B3n%20de%20red.md
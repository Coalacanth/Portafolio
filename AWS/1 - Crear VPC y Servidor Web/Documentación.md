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
![CrearVPC](https://github.com/Coalacanth/Portafolio/blob/main/Recursos/1%20-%20Im%C3%A1genes/01-Creaci%C3%B3n%20VPC.png)

# Crear Subred
Para la creación de la subred se necesita saber en que VPC se va a crear. 
![2.1Creación subred.png](https://github.com/Coalacanth/Portafolio/blob/main/Recursos/1%20-%20Im%C3%A1genes/02.1-Creaci%C3%B3n%20subred.png)
Es importante saber que la instancia EC2 al alojar un servidor web, debe estar en una subred pública.
![02.2-Creación subred.png](https://github.com/Coalacanth/Portafolio/blob/main/Recursos/1%20-%20Im%C3%A1genes/02.2-Creaci%C3%B3n%20subred.png)

# Crear Internet Gateway

![[03-Creación Internet gateway.png]]

# Crear Tablas de Enrutamiento



# Configurar la Tabla de Enrutamiento



# Crear Grupo de Seguridad



# Crear Instancia EC2


[segmentación de red]: https://github.com/Coalacanth/Portafolio/blob/main/AWS/1%20-%20Crear%20VPC%20y%20Servidor%20Web/Segmentaci%C3%B3n%20de%20red.md
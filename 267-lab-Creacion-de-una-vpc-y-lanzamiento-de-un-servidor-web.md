# Laboratorio 267: Creación de una VPC y lanzamiento de un servidor web

> **Descripción del Laboratorio:** > Este laboratorio práctico te guiará en la construcción desde cero de una infraestructura de red personalizada en AWS para un cliente de la lista Fortune 100, con el objetivo de desplegar un servidor web altamente disponible.
---

## 🎯 Objetivos

* Crear una nube privada virtual (VPC).
* Crear subredes.
* Configurar un grupo de seguridad (Security Group).
* Lanzar una instancia de Amazon Elastic Compute Cloud (Amazon EC2) dentro de una VPC.

---
## Contexto del caso

En este laboratorio, utilizarás Amazon Virtual Private Cloud (VPC) para crear tu propia VPC y añadir componentes adicionales con el fin de producir una red personalizada para un cliente de la lista Fortune 100. También crearás grupos de seguridad para tu instancia EC2. Posteriormente, configurarás y personalizarás una instancia EC2 para que funcione como servidor web y la lanzarás dentro de la VPC, la cual se verá como el siguiente diagrama del cliente:

Diagrama del cliente
Figura: El cliente solicita la construcción de esta arquitectura para lanzar su servidor web con éxito.

![Arquitectura cliente](267-Lab-Creacion-de-una-VPC-y-lanzamiento-de-un-servidor-web\Arquitectura-cliente.png)
Figura 0.

---

## 🛠️ Desarrollo Paso a Paso

### Inicio laboratorio: 
1. Se da por iniciado el laboratorio al iniciar el conteo. 


![Laboratorio Iniciado](267-Lab-Creacion-de-una-VPC-y-lanzamiento-de-un-servidor-web\1.png)
Figura 1.


### Crear tu VPC 1: 
1. Se configura la VPC, sin autogenerar los nombres, con los siguientes datos; IPv4 CIDR block:10.0.0.0/16 y Bloque de CIDR IPv6: sin bloque.
   
![Crear tu VPC 1](267-Lab-Creacion-de-una-VPC-y-lanzamiento-de-un-servidor-web\2.png)
Figura 2.

### Crear tu VPC 2: 
1. Se configura la zona de disponibilidad; Number of Availability Zones (AZs): 1, Number of public subnets: 1, Number of private subnets: 1, Public subnet en us-west-2a: 10.0.0.0/24 y Private subnet en us-west-2a: 10.0.1.0/24.

![Crear tu VPC 2](267-Lab-Creacion-de-una-VPC-y-lanzamiento-de-un-servidor-web\3.png)
Figura 3.

### Crear tu VPC 3: 
1. Las puertas de enlace NAT se selecciona *Zonal*, NAT gateways: En 1 AZ y VPC endpoints: Ninguna.
2. Se le asignan los nombres a; VPC: Lab VPC, Subred pública: Public Subnet 1, Subred privada: Private Subnet 1,Tabla de enrutamiento pública: Public Route Table y Tabla de enrutamiento privada: Private Route Table.

![Crear tu VPC 3](267-Lab-Creacion-de-una-VPC-y-lanzamiento-de-un-servidor-web\4.png)
Figura 4.

### Crear tu VPC 4: 
1.  Confirmación de la creación de la VPC.

![Crear tu VPC 4](267-Lab-Creacion-de-una-VPC-y-lanzamiento-de-un-servidor-web\5.png)
Figura 5.

### Crear las subredes de Alta Disponibilidad: 
1.  Se ingresa a Subredes desde ver todas las VPC, luego crear las nuevas Subredes. Se configuran las subredes con los siguientes datos;
   * Crear subred pública; VPC ID: Lab VPC, subred nombre: Public Subnet 2, Availability Zone: No preference y IPv4 CIDR block: 10.0.2.0/24.
   * Crear subred privada; VPC ID: Lab VPC, subred nombre: Private Subnet 2, Availability Zone: No preference y IPv4 CIDR block: 10.0.3.0/24.
  
    En la imagen se puede apreciar que fueron creadas y se asociaron a la VPC creada.


![Crear las subredes de Alta Disponibilidad](267-Lab-Creacion-de-una-VPC-y-lanzamiento-de-un-servidor-web\6.png)
Figura 6.


### Asociar las nuevas subredes a sus Tablas de Enrutamiento: 
1.  Se ingresa a las tablas de enrutamiento desde ver todas las VPC. Para asociar las nuevas subredes a las tablas de enrutamiento correspondientes, se siguio el procedimiento;
    * Se selecciona *Public Route Table*, luego en subredes asociadas, sin asociación explicita, se selecciona la nueva subred *Public Subnet 2* y al final guardar asociaciones.
    * Se selecciona *Private Route Table*, luego en subredes asociadas, sin asociación explicita, se selecciona la nueva subred *Private Subnet 2* y al final guardar asociaciones.
    
    En la imagen se puede apreciar que fueron asociadas a las tablas de enrutamiento de la VPC creada.

![Asociar las nuevas subredes a sus Tablas de Enrutamiento 1](267-Lab-Creacion-de-una-VPC-y-lanzamiento-de-un-servidor-web\7.png)
Figura 7.
![Asociar las nuevas subredes a sus Tablas de Enrutamiento 1.1](267-Lab-Creacion-de-una-VPC-y-lanzamiento-de-un-servidor-web\8.png)
Figura 8.

### Crear el Grupo de Seguridad: 
1.  Se ingresa a los grupos de seguridad desde ver todas las VPC > seguridad. Para crear el grupo de seguridad se configura de la siguiente forma; Security group name: Web Security Group, Description: Enable HTTP access, VPC: Lab VPC, reglas de entrada; Type: HTTP, Source: Anywhere-IPv4 (0.0.0.0/0) y Description: Permit web requests.

![Crear el Grupo de Seguridad](267-Lab-Creacion-de-una-VPC-y-lanzamiento-de-un-servidor-web\9.png)
Figura 9.

### Lanzar el Servidor Web EC2: 
1.  Se configura la instancia de EC2 de la siguiente forma; Name: Web Server 1, Amazon Machine Image (AMI): Amazon Linux,menú: Amazon Linux 2 AMI (HVM), Instance type: t3.micro, Key pair (login): vockey, Network settings; VPC: Lab VPC, Subnet: Public Subnet 2, Auto-assign public IP: Enable, Firewall (security groups): Select existing security group,
security groups: Web Security Group.
2.  En Advanced details, User data se ingresa el script entregado en laboratorio.

![Lanzar el Servidor Web EC2](267-Lab-Creacion-de-una-VPC-y-lanzamiento-de-un-servidor-web\10.png)
Figura 10.

### Lanzamiento de la instancia: 
1.  Se confirma la creación de la instancia de EC2 con alta disponibilidad asociada a Lab VPC.

![Lanzamiento de la instancia](267-Lab-Creacion-de-una-VPC-y-lanzamiento-de-un-servidor-web\11.png)
Figura 11.

### Submit: 
1. Cargado a **submit** el laboratorio y entregado. 

![Submit](267-Lab-Creacion-de-una-VPC-y-lanzamiento-de-un-servidor-web\12.png)
Figura 12.

### Finalización del laboratorio: 
1. Con el laboratorio terminado se procede a finalizar correctamente.

![Finalización del laboratorio](267-Lab-Creacion-de-una-VPC-y-lanzamiento-de-un-servidor-web\13.png)
Figura 13.

### Respuesta Técnica para el cliente:

Se informa que la construcción y el despliegue de la infraestructura de red personalizada en AWS se han completado con total éxito de acuerdo con los requerimientos de alta disponibilidad solicitados. Se ha diseñado una arquitectura segmentada mediante una nube privada virtual principal (Lab VPC), compuesta por subredes públicas y privadas distribuidas estratégicamente en múltiples Zonas de Disponibilidad para asegurar la tolerancia a fallos y el aislamiento eficiente del tráfico de red. Asimismo, se implementó un firewall perimetral mediante un Grupo de Seguridad configurado de manera estricta para permitir únicamente peticiones web legítimas a través del puerto HTTP 80. Finalmente, mediante la automatización de scripts en el arranque (User data), se aprovisionó e inicializó correctamente el servidor web Apache junto con sus dependencias en la instancia Web Server 1. La plataforma ya se encuentra completamente operativa, estable y accesible de forma segura desde internet a través de la dirección DNS pública correspondiente.
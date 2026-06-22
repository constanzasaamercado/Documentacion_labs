# Laboratorio 264: Recursos de red para una VPC

> **Descripción del Laboratorio:** > Este laboratorio práctico simula el rol de un Ingeniero de Soporte de Cloud en AWS para resolver un problema de conectividad de red de una startup, guiando paso a paso en la construcción desde cero de una arquitectura enrutable en Amazon VPC mediante el enfoque Top-Down (de arriba hacia abajo).
---

## 🎯 Objetivos

* Resumir el escenario del cliente.

* Crear una VPC, una puerta de enlace a Internet (Internet Gateway), una tabla de ruteo (Route Table), un grupo de seguridad (Security Group), una lista de acceso a la red (Network Access List / NACL) y una instancia EC2 para construir una red con enrutamiento dentro de la VPC.

* Familiarizarse con la consola de administración.

* Desarrollar una solución al problema del cliente presentado en este laboratorio.

* El laboratorio se considera completado una vez que pueda utilizar con éxito el comando ping hacia el exterior de la VPC.

---
## Contexto del caso

Su rol es el de un Ingeniero de Soporte de Cloud (Cloud Support Engineer) en Amazon Web Services (AWS). Durante su turno, un cliente de una empresa emergente (startup) solicita asistencia con respecto a un problema de red dentro de su infraestructura de AWS. A continuación se presenta el correo electrónico y un archivo adjunto de su arquitectura.

**Correo electrónico del cliente**
¡Hola Soporte de Cloud!
Previamente me comuniqué con ustedes para solicitar ayuda en la configuración de mi VPC. Pensé que sabía cómo conectar todos los recursos para establecer una conexión a Internet, pero ni siquiera puedo hacer ping fuera de la VPC. ¡Todo lo que necesito hacer es un ping! ¿Podrían por favor ayudarme a configurar mi VPC para que tenga conectividad de red y pueda hacer ping? La arquitectura se encuentra abajo. ¡Gracias!
— Brock, dueño de la startup.


## 🛠️ Desarrollo Paso a Paso

### Inicio laboratorio: 
1. Se da por iniciado el laboratorio al iniciar el conteo. 


![Laboratorio Iniciado](264-Lab-Recursos-de-red-para-una-VPC\1.png)
Figura 1.

### Crear la VPC: 
1. Se crea la VPC con el nombre de "Test VPC" y IPv4 CIDR block; 192.168.0.0/18.
   
![Crear la VPC](264-Lab-Recursos-de-red-para-una-VPC\2.png)
Figura 2.

### Configuración subnet: 
1. IPv4 CIDR block; 192.168.1.0/26.
   
![Configuración subnet](264-Lab-Recursos-de-red-para-una-VPC\3.png)
Figura 3.

### VPC flujo de trabajo: 
1.  La VPC fue creada.

![VPC flujo de trabajo](264-Lab-Recursos-de-red-para-una-VPC\4.png)
Figura 4.

### Tabla de Ruteo: 
1.  Detalles de la tabla de ruteo.

![Tabla de Ruteo](264-Lab-Recursos-de-red-para-una-VPC\5.png)
Figura 5.

### Creación de ACL de red: 
1. La configuración de ACL se define con el nombre *"Public Subnet NACL"*, se asocia a Test VPC y se crea.

![Creación de ACL de red](264-Lab-Recursos-de-red-para-una-VPC\6.png)
Figura 6.
![Confirmación de ACL de red](264-Lab-Recursos-de-red-para-una-VPC\8.png)
Figura 8.

### Edición de reglas de entrada: 
1. Se procede a añadir la regla; Rule #: 100 y Tipo: All traffic.

![Edición de reglas de entrada](264-Lab-Recursos-de-red-para-una-VPC\7.png)
Figura 7.

### Edición de reglas de salida: 
1. Se procede a añadir la regla; Rule #: 100 y Tipo: All traffic.

![Edición de reglas de salida](264-Lab-Recursos-de-red-para-una-VPC\9.png)
Figura 9.

### Asociación de subredes: 
1. Se procede a asociar la subred a la ACL.

![Asociación de subredes](264-Lab-Recursos-de-red-para-una-VPC\10.png)
Figura 10.

### Confirmación de asociación de subredes: 
1. La subred se ha asociado correctamente.

![Confirmación de asociación de subredes](264-Lab-Recursos-de-red-para-una-VPC\11.png)
Figura 11.

### Configurar el Security Group: 
1. Se configura el grupo de seguridad con los siguientes datos; Nombre: public security group, Descripción: permitir tráfico web y SSH y VPC: Test VPC. 
2. Reglas de entrada: se añade reglas para permitir SSH, HTTP y HTTPS desde el origen Anywhere-IPv4 (0.0.0.0/0).
   Reglas de salida: se deja por defecto.

![Configurar el Security Group](264-Lab-Recursos-de-red-para-una-VPC\12.png)
Figura 12.

### Security Group: 
1. Se crea el grupo de seguridad.
2. Las reglas se añadieron correctamente.
   

![Security Group](264-Lab-Recursos-de-red-para-una-VPC\13.png)
Figura 13.

### Lanzar la Instancia EC2 y Conectarse: 
1. Se configura la instancia con los siguientes datos; AMI: Amazon Linux (Amazon Linux 2023 AMI), tipo: t3.micro, Key pair: vockey.
    Configuración de red; VPC: Test VPC, Subnet: Public Subnet, Auto-assign public IP: Habilitar, Grupo de seguridad: seleccionar un grupo de seguridad existente y luego public security group.
   

![Lanzar la Instancia EC2 y Conectarse](264-Lab-Recursos-de-red-para-una-VPC\14.png)
Figura 14.

### Confirmación de instancia EC2: 
1. Instancia de EC2 creada correctamente.
   

![Confirmación de instancia EC2](264-Lab-Recursos-de-red-para-una-VPC\15.png)
Figura 15.

### Credenciales: 
1. Se descarga el archivo **PPK**. Se copia el **IPPublico**.  

![Credenciales](264-Lab-Recursos-de-red-para-una-VPC\16.png)
Figura 16.

### Conexión por SSH y Prueba del "Ping": 
1. Se inicia correctamente la sesion en la terminal bash de **PuTTY** con el sistema Linux. Se ejecuta el comando **ping google.com** generandose respuestas continuas sin pérdida de paquetes.

![Conexión por SSH y Prueba del "Ping"](264-Lab-Recursos-de-red-para-una-VPC\17.png)
Figura 17.

### Submit: 
1. Cargado a **submit** el laboratorio y entregado. 

![Submit](264-Lab-Recursos-de-red-para-una-VPC\18.png)
Figura 18.

### Finalización del laboratorio: 
1. Con el laboratorio terminado se procede a finalizar correctamente.

![Finalización del laboratorio](264-Lab-Recursos-de-red-para-una-VPC\19.png)
Figura 19.


### Respuesta Técnica para el cliente:

Estimado Brock,

Un placer saludarte. Se ha investigado a fondo el inconveniente de conectividad en tu infraestructura y se informa que se ha restablecido el direccionamiento de red con éxito, permitiendo que tus instancias EC2 tengan salida y respuesta hacia internet (ping y tráfico bidireccional completamente operativos).

Tras realizar una auditoría de los recursos bajo la metodología Top-Down (de arriba hacia abajo), se identifico que la causa raíz del aislamiento de la red se debía a una desconexión en la cadena de enrutamiento y políticas restrictivas en las capas perimetrales de seguridad. Para solucionarlo, se implemento las siguientes acciones técnicas en tu entorno:

* Enrutamiento Perimetral: se creo e interconecto un Internet Gateway (IGW) a tu Test VPC y se actualizo la tabla de ruteo pública (Public Route Table), asociándola explícitamente a tu subred de cara al público (192.168.1.0/26). Se agrego una ruta estática con destino 0.0.0.0/0 apuntando al IGW como objetivo (target), lo que permite que cualquier tráfico externo sea correctamente direccionado hacia la red pública.

* Políticas de Seguridad Stateless (Capa de Subred): se diseño una nueva Network ACL (NACL) personalizada y se vinculo a tu subred pública. Se reemplazo las restricciones previas configurando la regla número 100 tanto para tráfico entrante (Inbound) como saliente (Outbound), permitiendo explícitamente All Traffic para asegurar el libre tránsito de los paquetes ICMP requeridos por el comando ping.

* Políticas de Seguridad Stateful (Capa de Instancia): se desplego un Security Group optimizado (public security group) asignado directamente a tu interfaz de red de EC2. Este permite el ingreso de conexiones esenciales (SSH puerto 22, HTTP puerto 80 y HTTPS puerto 443) desde cualquier origen (0.0.0.0/0) y mantiene por defecto la directiva de salida libre para las peticiones de la instancia.

Finalmente, se realizo pruebas de diagnóstico de conectividad WAN desde la consola de la instancia (Amazon Linux 2023) mediante el envío de paquetes ICMP hacia los DNS públicos de Google, confirmando estabilidad absoluta en los tiempos de respuesta y un 0% de pérdida de paquetes (0% packet loss). La topología ya es completamente ruteable y segura.
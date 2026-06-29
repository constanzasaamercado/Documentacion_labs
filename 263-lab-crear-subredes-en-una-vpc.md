# Laboratorio 263: Crear subredes en una VPC

> **Descripción del Laboratorio:** > Este laboratorio práctico consiste en asumir el rol de un Ingeniero de Soporte en la Nube de AWS para resolver un requerimiento de red de un cliente, lo que implica diseñar y desplegar una Amazon Virtual Private Cloud (Amazon VPC) personalizada utilizando rangos de direccionamiento privado bajo el estándar RFC 1918.

---

## 🎯 Objetivos

* Resumir el escenario del cliente.
* Crear una Amazon Virtual Private Cloud (Amazon VPC) y comprender cómo crear subredes y asignar direcciones IP.
* Familiarizarse con la consola de administración de Amazon Web Services (AWS).
* Desarrollar una solución para el problema del cliente en este laboratorio.
* Resumir y describir los hallazgos.

---
## Contexto del caso

Su rol es el de un ingeniero de soporte en la nube (Cloud Support Engineer) en AWS. Durante su turno, un cliente de una empresa emergente (startup) solicita asistencia con respecto a un problema de redes dentro de su infraestructura de AWS. El siguiente es el correo electrónico y un archivo adjunto sobre su arquitectura:

**Ticket de su cliente**
Hola, ¡Soporte en la Nube!

Soy nuevo en AWS y necesito ayuda para configurar una VPC. ¿Podrían ayudarme con el proceso de configuración? Me gustaría construir solo la parte de la VPC y quisiera que se viera algo parecido a la siguiente imagen. ¿Pueden ayudarme a asegurarme de tener alrededor de 15,000 direcciones IP privadas disponibles en esta VPC? También me gustaría que el bloque CIDR IPv4 de la VPC fuera un 192.x.x.x. Aunque no recuerdo cuál es el rango privado. ¿Podrían confirmarme eso? También me gustaría asignar al menos 50 direcciones IP para la subred pública.

¡Gracias!

Paulo Santos > Dueño de Startup

---

## 🛠️ Desarrollo Paso a Paso

### Inicio laboratorio: 
1. Se da por iniciado el laboratorio al iniciar el conteo. 


![Laboratorio Iniciado](263-Lab-Crear-subredes-en-una-VPC\1.png)
Figura 1.

### Configurar el Asistente de VPC: 
1. Se configura la VPC con el nombre de "First VPC", IPv4 CIDR block; 192.168.0.0/18, IPv6 CIDR block; No IPv6 CIDR block (Sin bloque CIDR IPv6).
   
![Configurar el Asistente de VPC](263-Lab-Crear-subredes-en-una-VPC\2.png)
Figura 2.

### Zonas de disponibilidad: 
1. Se procede a seleccionar 1 zona, con la que viene por defecto. La subred es 1 también con el Public subnet's IPv4 CIDR; 192.168.1.0/26.
   
![Zonas de disponibilidad](263-Lab-Crear-subredes-en-una-VPC\3.png)
Figura 3.

### Crear VPC: 
1.  Puertas de enlance nat se dejan seleccionadas en ninguna. Se procede a crear la VPC.

![Crear VPC](263-Lab-Crear-subredes-en-una-VPC\4.png)
Figura 4.

![Vista previa](263-Lab-Crear-subredes-en-una-VPC\5.png)
Figura 5.

### Confirmación de la creación: 
1. Se crea correctamente la VPC.

![Confirmación de la creación](263-Lab-Crear-subredes-en-una-VPC\6.png)
Figura 6.

### First VPC-pvc: 
1. VPC creada.

![First VPC-pvc](263-Lab-Crear-subredes-en-una-VPC\7.png)
Figura 7.

### Detalles First VPC-pvc: 
1. Detalles de la VPC creada, se pueden observar que la configuración seleccionada coincide.

![Detalles First VPC-pvc](263-Lab-Crear-subredes-en-una-VPC\8.png)
Figura 8.

### Submit: 
1. Cargado a **submit** el laboratorio y entregado.

![Submit](263-Lab-Crear-subredes-en-una-VPC\9.png)
Figura 9.

### Finalización del laboratorio: 
1. Con el laboratorio terminado se procede a finalizar correctamente.

![Finalización del laboratorio](263-Lab-Crear-subredes-en-una-VPC\10.png)
Figura 10.


### Respuesta Técnica para el cliente:

* Confirmación de Red Privada: Se confirmó que el rango 192.168.0.0 pertenece al estándar RFC 1918 para redes privadas locales, cumpliendo con la restricción del cliente.

* Direccionamiento de la VPC: Se asignó el bloque 192.168.0.0/18, lo que proporciona un total de 16,384 direcciones IP virtuales, superando las 15,000 solicitadas para la sede de Seattle.

* Direccionamiento de la Subred: Se aisló la subred pública mediante el bloque 192.168.1.0/26, entregando 64 direcciones IP totales para el departamento de operaciones, cumpliendo con el mínimo de 50 requerido.
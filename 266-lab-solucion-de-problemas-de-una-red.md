# Laboratorio 266: Solución de problemas de una red

> **Descripción del Laboratorio:** > Este laboratorio práctico te sitúa en el rol de un Ingeniero de Soporte en la Nube de AWS con la misión de resolver un problema de conectividad reportado por un cliente, quien no puede acceder a su servidor web Apache a través del navegador ni por medio de comandos de red.
---

## 🎯 Objetivos

* Analizar el escenario del cliente.
* Resolver el problema de red (troubleshooting).
---
## Contexto del caso

Tu rol es el de un ingeniero de soporte en la nube (Cloud Support Engineer) en Amazon Web Services (AWS). Durante tu turno, una empresa de consultoría presenta un problema de red dentro de su infraestructura de AWS. A continuación, se muestra el correo electrónico y un archivo adjunto con su arquitectura:

Correo electrónico del cliente
¡Hola, Soporte de Cloud!
Cuando creo un servidor Apache a través de la línea de comandos, no puedo hacerle ping. También me da un error cuando introduzco la dirección IP en el navegador. ¿Podrían por favor ayudarme a descubrir qué está bloqueando mi conexión?
¡Gracias!
AnaContractor

---

## 🛠️ Desarrollo Paso a Paso

### Inicio laboratorio: 
1. Se da por iniciado el laboratorio al iniciar el conteo. 


![Laboratorio Iniciado](266-Lab-Solucion-de-problemas-de-una-red\1.png)
Figura 1.

### Credenciales: 
1. Se descarga el archivo **PPK**.
2. Se copia el **IPPublico**.

![Credenciales](266-Lab-Solucion-de-problemas-de-una-red\2.png)
Figura 2.

### Levantar el servicio Apache (httpd): 
1. Con el comando **sudo systemctl status httpd.service** se revisa el estado del servicio, el cual se encuentra *inactivo*.
2. Se ejecuta el comando **sudo systemctl start httpd.service** para activar el servicio. Se vuelve a ejecutar el comando **sudo systemctl status httpd.service** comprobando que el estado cambio a *activo*.
   
![Levantar el servicio Apache (httpd) 1](266-Lab-Solucion-de-problemas-de-una-red\3.png)
Figura 3.

### Levantar el servicio Apache (httpd) 2: 
1. Se prueba cargar el sitio en web pero no se puede acceder. 

![Levantar el servicio Apache (httpd) 2](266-Lab-Solucion-de-problemas-de-una-red\4.png)
Figura 4.

### Investigar la VPC y reparar el bloqueo de red 1: 
1.  Detalles de la VPC del servicio.

![Investigar la VPC y reparar el bloqueo de red 1](266-Lab-Solucion-de-problemas-de-una-red\5.png)
Figura 5.

### Investigar la VPC y reparar el bloqueo de red 2: 
1.  Detalle del grupo de seguridad.
2.  Se muestra que solo permite el *SSH* por lo que se pudo ingresar a la instancia por PuTTy, pero no al sitio web.


![Investigar la VPC y reparar el bloqueo de red 2](266-Lab-Solucion-de-problemas-de-una-red\6.png)
Figura 6.


### Investigar la VPC y reparar el bloqueo de red 4: 
1.  Se agrega la regla de entrada con el tipo *HTTP* al grupo de seguridad de la VPC asociada a la instancia.


![Investigar la VPC y reparar el bloqueo de red 4](266-Lab-Solucion-de-problemas-de-una-red\7.png)
Figura 7.

### Confirmación del éxito y cierre: 
1.  Se carga el sitio web de la instancia y se puede acceder a esta.


![Confirmación del éxito y cierre](266-Lab-Solucion-de-problemas-de-una-red\8.png)
Figura 8.

### Submit: 
1. Cargado a **submit** el laboratorio y entregado. 

![Submit](266-Lab-Solucion-de-problemas-de-una-red\9.png)
Figura 9.

### Finalización del laboratorio: 
1. Con el laboratorio terminado se procede a finalizar correctamente.

![Finalización del laboratorio](266-Lab-Solucion-de-problemas-de-una-red\10.png)
Figura 10.

### Respuesta Técnica para el cliente:

Tras realizarse las pruebas pertinentes en las distintas capas del modelo OSI, se detecto dos factores que impedían el correcto funcionamiento y visualización del sitio:  

1. Estado del Servicio Local (Capa de Aplicación): Al ingresar a la instancia, se identifico que el servicio de Apache (httpd) se encontraba instalado pero en estado inactivo (inactive/dead). Se procedio a iniciarlo de forma manual mediante el comando **sudo systemctl start httpd.service**, dejándolo en ejecución de manera correcta.  
2. Restricción en el Grupo de Seguridad (Capa de Transporte): Aunque la VPC cuenta con salida hacia internet a través de su Internet Gateway, el Grupo de Seguridad (Security Group) asociado a la instancia EC2 solo permitía tráfico entrante para el puerto 22 (SSH). Esto bloqueaba por completo cualquier petición externa dirigida a los puertos web estándar.  

Acciones realizadas para solucionar el problema:
* Se activa el servidor HTTP Apache dentro de la instancia Linux.  
* Se actualizan las reglas de entrada (Inbound rules) de el Grupo de Seguridad, habilitando el protocolo HTTP en el puerto 80 para permitir el tráfico desde cualquier origen (0.0.0.0/0). 
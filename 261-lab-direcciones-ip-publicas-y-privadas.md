# Laboratorio 261: Direcciones IP públicas y privadas

> **Descripción del Laboratorio:** > Este laboratorio práctico simula un caso de soporte técnico en AWS para identificar problemas de conectividad en una VPC con rango **10.0.0.0/16**, demostrando de forma empírica la diferencia operativa entre direccionamientos IP.
---

## 🎯 Objetivos

* Resumir e investigar el escenario del cliente.
* Analizar la diferencia entre una dirección IP privada y una pública.
* Desarrollar una solución al problema del cliente en este laboratorio.

---
## Contexto del caso

Su rol es el de un ingeniero de soporte en la nube en Amazon Web Services (AWS). Durante su turno, un cliente de una empresa Fortune 500 solicita asistencia con respecto a un problema de redes dentro de su infraestructura de AWS. A continuación se muestra el correo electrónico y un archivo adjunto sobre su arquitectura:

**Ticket de su cliente**
Hola, ¡Soporte de la Nube!

Actualmente tenemos una nube privada virtual (VPC) con un rango CIDR de 10.0.0.0/16. En esta VPC, tenemos dos instancias de Amazon Elastic Compute Cloud (Amazon EC2): la instancia A y la instancia B. A pesar de que ambas están en la misma subred y tienen las mismas configuraciones con los recursos de AWS, la instancia A no puede comunicarse con internet y la instancia B sí puede. Creo que tiene algo que ver con las instancias EC2, pero no estoy segura.

También tenía una pregunta sobre el uso de un rango público de direcciones IP como 12.0.0.0/16 para una VPC que me gustaría lanzar. ¿Causaría eso algún problema? Adjunto nuestra arquitectura como referencia.

¡Gracias!

Jess - Administradora de la Nube

---

## 🛠️ Desarrollo Paso a Paso

### Inicio laboratorio: 
1. Se da por iniciado el laboratorio al iniciar el conteo. 


![Laboratorio Iniciado](261-Lab-Direcciones-IP-publicas-y-privadas\1.png)
Figura 1.

### Investigar el entorno del cliente 1: 
1. Se visualizan las instancias A y B en EC2, que estan en ejecución.
   
![Investigar el entorno del cliente 1](261-Lab-Direcciones-IP-publicas-y-privadas\2.png)
Figura 2.

### Investigar el entorno del cliente 2 (Instancia A): 
1. Resumen de la instancia A.
2. Se observa que la Instancia A no tiene una dirección IP pública asignada.
   
![Investigar el entorno del cliente 2](261-Lab-Direcciones-IP-publicas-y-privadas\3.png)
Figura 3.

### Investigar el entorno del cliente 3 (Instancia A): 
1.  Ip privada **10.0.10.212**.
2.  Al intentar acceder a la ip privada, no se puede.

![Investigar el entorno del cliente 3](261-Lab-Direcciones-IP-publicas-y-privadas\4.png)
Figura 4.

### Investigar el entorno del cliente 4 (Instancia B): 
1.  Resumen de la instancia B.
2.  Se observa que tiene tanto una IP privada como IP pública.

![Investigar el entorno del cliente 4](261-Lab-Direcciones-IP-publicas-y-privadas\5.png)
Figura 5.

### Credenciales: 
1. Se descarga el archivo **PPK**.
2. Se copia el **IPPublico**.

![Credenciales](261-Lab-Direcciones-IP-publicas-y-privadas\6.png)
Figura 6.

### Conexión por SSH y Responder las preguntas: 
1. e inicia correctamente la sesion en la terminal bash de **PuTTY** con el sistema Linux. **pwd** Valida que se encuentre en la carpeta de inicio (home) del usuario actual escribiendo.
2. **ip route show** con este comando se visualizo la ip de la instancia B.

### ¿Te pudiste conectar a ambas instancias?

No. Solo se puede conectar a la Instancia *B* porque tiene una IP pública que es accesible desde la computadora. La Instancia *A* falla en la conexión (da Timeout) porque la computadora está en internet y la Instancia *A* solo tiene IP privada.
![Conexión por SSH y Responder las preguntas](261-Lab-Direcciones-IP-publicas-y-privadas\7.png)
Figura 7.

### Submit: 
1. Cargado a **submit** el laboratorio y entregado.

![Submit](261-Lab-Direcciones-IP-publicas-y-privadas\8.png)
Figura 8.

### Finalización del laboratorio: 
1. Con el laboratorio terminado se procede a finalizar correctamente.

![Finalización del laboratorio](261-Lab-Direcciones-IP-publicas-y-privadas\9.png)
Figura 9.


### Respuesta Técnica para el cliente:

1. *Sobre el problema actual (Instancia A vs Instancia B):*
Tras revisar la infraestructura, se encontro que ambas instancias comparten la misma subred y tablas de enrutamiento hacia el Internet Gateway. Sin embargo, la Instancia A no tiene asignada una dirección IPv4 pública, solo una IP privada. En AWS, para que un recurso se comunique bidireccionalmente con internet, requiere obligatoriamente una IP pública o pasar a través de un NAT Gateway. La Instancia B funciona correctamente porque sí posee una IP pública.
*Solución:* Para arreglarlo, puede asignarle una dirección Elastic IP (IP estática pública) a la Instancia A.

2. *Sobre la propuesta del rango 12.0.0.0/16:*
No se recomienda utilizar el rango 12.0.0.0/16 para la nueva VPC. Este bloque es un rango de direcciones IP públicas registrado en internet. Utilizarlo de forma privada causará solapamientos de red (overlapping), impidiendo que sus servidores puedan comunicarse con los servidores reales en internet que utilicen ese segmento. Se suguiere utilizar rangos estándar privados bajo la norma RFC 1918, como por ejemplo 10.1.0.0/16 o 172.16.0.0/16.
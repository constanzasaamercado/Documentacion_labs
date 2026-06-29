# Laboratorio 262: Direcciones IP Estáticas y Dinámicas

> **Descripción del Laboratorio:** > Este laboratorio práctico introduce los conceptos fundamentales de direccionamiento de red en AWS mediante la resolución de un problema real de infraestructura para un cliente corporativo.
---

## 🎯 Objetivos

* Resumir el escenario del cliente.
* Analizar la diferencia entre direcciones IP asignadas de forma estática y dinámica utilizando instancias EC2.
* Asignar una IP persistente (estática) a una instancia EC2.
* Desarrollar una solución al problema del cliente encontrado dentro de este laboratorio; después de desarrollar la solución, resumir y describir tus hallazgos.
* Resumir y describir los hallazgos.

---
## Contexto del caso

**Ticket de tu cliente**

Hola Soporte en la Nube!

Estamos teniendo problemas con una de nuestras instancias EC2. La IP cambia cada vez que iniciamos y detenemos esta instancia llamada Public Instance. Esto hace que todo se rompa ya que necesita una dirección IP estática. No estamos seguros de por qué la IP cambia a una IP aleatoria cada vez en esta instancia. ¿Podrían investigar, por favor? Adjunto está nuestra arquitectura. Por favor, háganme saber si tienen alguna pregunta.
¡Gracias! — Bob, Administrador de la Nube

---

## 🛠️ Desarrollo Paso a Paso

### Inicio laboratorio: 
1. Se da por iniciado el laboratorio al iniciar el conteo. 


![Laboratorio Iniciado](262-Lab-Direcciones-IP-y-estaticas-y-dinámicas\1.png)
Figura 1.

### Replicar el Problema del Cliente: 
1. Se nombra la instancia como **test instance**. Se configura AMI; Amazon Linux 2 AMI (HVM), Tipo; t3.micro, Red; Lab VPC, Auto-assign Public IP: Habilitar y grupo de seguridad; Linux Instance SG. 
   
![Replicar el Problema del Cliente](262-Lab-Direcciones-IP-y-estaticas-y-dinámicas\2.png)
Figura 2.

### Lanzamiento de la instancia: 
1. Se inicia correctamente el lanzamiento de la instancia.
   
![Lanzamiento de la instancia](262-Lab-Direcciones-IP-y-estaticas-y-dinámicas\3.png)
Figura 3.

### Detalle de instacia: 
1.  Instancia creada ya se encuentra en ejecución.
2.  Las IPs iniciciales son; Dirección IPv4 Pública(35.88.160.75) y Dirección IPv4 Privada(10.0.10.115).

![Detalle de instacia](262-Lab-Direcciones-IP-y-estaticas-y-dinámicas\4.png)
Figura 4.

### Analizar el Comportamiento de las IPs 1: 
1.  Se detiene la instancia para probar el cambio del numero de IP pública.

![Analizar el Comportamiento de las IPs 1](262-Lab-Direcciones-IP-y-estaticas-y-dinámicas\5.png)
Figura 5.

### Analizar el Comportamiento de las IPs 2: 
1. Se observa que la IP pública ha desaparecido, mientras que la IP privada se mantiene.

![Analizar el Comportamiento de las IPs 2](262-Lab-Direcciones-IP-y-estaticas-y-dinámicas\6.png)
Figura 6.

### Iniciar la instancia: 
1. Ya se encuentra en ejecución.
2. Lo que observa despues de volver a iniciar la instancia es que la IP pública cambió a una completamente nueva. Dirección IPv4 Pública(35.84.211.197).

![Iniciar la instancia](262-Lab-Direcciones-IP-y-estaticas-y-dinámicas\7.png)
Figura 7.

### Implementar la Solución (Elastic IP): 
1. Se asigna una Elastic IP dejando todo por defecto.

![Implementar la Solución (Elastic IP)](262-Lab-Direcciones-IP-y-estaticas-y-dinámicas\8.png)
Figura 8.

### Asignar una Elastic IP: 
1. Se asignó correctamente la IP elástica(16.147.177.58) y IP privada(10.0.10.115).

![Asignar una Elastic IP](262-Lab-Direcciones-IP-y-estaticas-y-dinámicas\9.png)
Figura 9.

### Asociar la IP a la Instancia 1: 
1. Se procede a asociar la ip a la instancia EC2 *"test instance"*.

![Asociar la IP a la Instancia 1](262-Lab-Direcciones-IP-y-estaticas-y-dinámicas\10.png)
Figura 10.

### Asociar la IP a la Instancia 2: 
1. Se asoció correctamente.

![Asociar la IP a la Instancia 2](262-Lab-Direcciones-IP-y-estaticas-y-dinámicas\11.png)
Figura 11.

### Nuevo detalle de la instancia: 
1. Se muestra que los números de IP pública(16.147.177.58) y privada(10.0.10.115) coinciden con los creados en la IP elástica.

![Nuevo detalle de la instancia](262-Lab-Direcciones-IP-y-estaticas-y-dinámicas\12.png)
Figura 12.

### Verificación de IP elástica 1: 
1. Se detiene la instancia.
2. Se observa que la IP pública se mantiene idéntica.

![Verificación de IP elástica 1](262-Lab-Direcciones-IP-y-estaticas-y-dinámicas\13.png)
Figura 13.

### Verificación de IP elástica 2: 
1. Se vuelve a iniciar la instancia.
2. Sigue sin modificarse la IP pública por lo que se soluciona el problema de esta forma.

![Verificación de IP elástica 2](262-Lab-Direcciones-IP-y-estaticas-y-dinámicas\14.png)
Figura 14.

### Submit: 
1. Cargado a **submit** el laboratorio y entregado.

![Submit](262-Lab-Direcciones-IP-y-estaticas-y-dinámicas\15.png)
Figura 15.

### Finalización del laboratorio: 
1. Con el laboratorio terminado se procede a finalizar correctamente.

![Finalización del laboratorio](262-Lab-Direcciones-IP-y-estaticas-y-dinámicas\16.png)
Figura 16.

### 📝 Respuestas a las Preguntas del Laboratorio

*¿Qué tipo de IP asignó Bob originalmente?* 
Asignó una IP pública dinámica (proporcionada por el pool público general de AWS al encender la máquina).

*¿Qué notaste al apagar y encender la instancia?* 
La IP pública cambió por completo, mientras que la IP privada permaneció estática (las IPs privadas dentro de una VPC no cambian durante el ciclo de vida de parada/inicio de la instancia).

*¿Es la Elastic IP estática o dinámica?*
Es Estática. Permanece asignada a tu cuenta de AWS y vinculada a tu instancia sin importar cuántas veces se reinicie, apague o encienda.

### Respuesta Técnica para el cliente:

"Hola Bob, he investigado el problema con tu Public Instance.

El comportamiento que experimentas es el comportamiento por defecto en AWS: cuando utilizas la opción de Auto-assign Public IP, AWS te asigna una dirección IP pública dinámica. Cada vez que la instancia se detiene, esa IP se libera de vuelta al pool de AWS, y al encenderla de nuevo, se te asigna una IP aleatoria diferente.

La Solución: Para resolver esto, se ha implementado una Elastic IP (EIP) en tu infraestructura. Una Elastic IP es una dirección IPv4 estática diseñada para la computación en la nube. Ya la hemos asignado y asociado a tu instancia. A partir de ahora, aunque apagues la instancia para ahorrar costos y la vuelvas a encender, la dirección IP pública se mantendrá fija, evitando que tus aplicaciones y recursos conectados se rompan."
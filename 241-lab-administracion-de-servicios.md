# Laboratorio 241: Administración de servicios

> **Descripción del Laboratorio:** > Este laboratorio práctico se centra en la administración básica de servicios del sistema y el monitoreo de recursos en un entorno Linux (Amazon Linux 2) alojado en AWS (Amazon EC2).

---

## 🎯 Objetivos

* Verificar el estado del servicio httpd para asegurarte de que está en ejecución y que puedes realizar una conexión HTTP a la dirección IP del host local (localhost).
* Aprender a monitorear la instancia EC2 de Amazon Linux 2 utilizando:
    * El comando top de Linux.
    * AWS CloudWatch.

---

## 🛠️ Desarrollo Paso a Paso

### Inicio laboratorio: 
1. Se da por iniciado el laboratorio al iniciar el conteo. 


![Laboratorio Iniciado](241-Lab-Servicios-administrativos\1.png)
Figura 1.

### Credenciales: 
1. Se descarga el archivo **PPK**.
2. Se copia el **IPPublico**.

![Credenciales](241-Lab-Servicios-administrativos\2.png)
Figura 2.

### Verificar el estado del servicio httpd: 
1. Se inicia correctamente la sesion en la terminal bash de **PuTTY** con el sistema Linux. Se verifica el estado del servicio httpd utilizando los comandos **sudo systemctl status httpd.service**, el resultado indica que la sección del servicio httpd está inactiva, esto indica que el servicio httpd está cargado, lo que significa que está instalado y listo para funcionar pero está inactivo.
   **sudo systemctl start httpd.service** Con estos comandos se da inicio el servicio httpd. Se verifica de nuevo el estado del servicio httpd utilizando los comandos **sudo systemctl status httpd.service**, el resultado indica que la sección del servicio httpd está activa/en ejecución.
2. Se prueba que la pagina esta funcionando en **http://44.243.212.22**. Se procede a detener el servicio con los comandos **sudo systemctl stop httpd.service**.
   
![Verificar el estado del servicio httpd](241-Lab-Servicios-administrativos\3.png)
Figura 3.

### Monitoreo de una instancia EC2 de Linux 1: 
1. Con **top** se muestra la lista de procesos en ejecución. 

![Monitoreo de una instancia EC2 de Linux 1](241-Lab-Servicios-administrativos\4.png)
Figura 4.

### Monitoreo de una instancia EC2 de Linux 2: 
1.  Para simular una carga de trabajo en la CPU de nla instancia EC2, se ejecutan los comandos **./stress.sh & top**. Luego se revisa nuevamente la lista de procesos con **top**, mostrando un alto uso de CPU.

![Monitoreo de una instancia EC2 de Linux 2](241-Lab-Servicios-administrativos\5.png)
Figura 5.

### Monitoreo de una instancia EC2 de Linux 3:
1. En la imagen se muestra el tablero de CloudWatch para la instancia de EC2, son varias metricas, entre ellas las del CPU, que indica un pico en la utilización de la CPU que coincide con el momento en que se inicio el script de estres.


![Monitoreo de una instancia EC2 de Linux 3](241-Lab-Servicios-administrativos\6.png)
Figura 6.

### Monitoreo de una instancia EC2 de Linux 4: 
1.  Luego de 5 minutos se puede observar que el script de estres termino y el uso de la CPU disminuye drasticamente.

![Monitoreo de una instancia EC2 de Linux 4](241-Lab-Servicios-administrativos\7.png)
Figura 7.

### Submit: 
1. Cargado a **submit** el laboratorio y entregado.

![Submit](241-Lab-Servicios-administrativos\8.png)
Figura 8.

### Finalización del laboratorio: 
1. Con el laboratorio terminado se procede a finalizar correctamente.

![Finalización del laboratorio](241-Lab-Servicios-administrativos\9.png)
Figura 9.

## 💡 Conclusión y Comentarios Personales

La realización de este laboratorio permitió adquirir competencias críticas en la gestión de servicios web y en la supervisión avanzada de infraestructura en la nube utilizando el entorno de AWS. El uso combinado de comandos como **sudo systemctl start httpd.service** y el análisis en tiempo real mediante top demostraron ser fundamentales para la administración operativa de Linux. Estas herramientas facultan al administrador para controlar los ciclos de vida de aplicaciones esenciales, supervisar de forma inmediata el consumo de recursos de los usuarios e identificar qué procesos específicos están sobrecargando el rendimiento del servidor en un momento determinado.  

Por otro lado, la práctica consolidó el valor estratégico de la telemetría y el monitoreo centralizado a través de herramientas globales de computación en la nube. La ejecución en segundo plano del script de simulación de carga **./stress.sh & top** sirvió como un valioso caso de estudio sobre el comportamiento de la infraestructura bajo demanda, permitiendo experimentar de primera mano cómo un incremento drástico en la CPU afecta los tiempos de procesamiento del host. Validar finalmente este comportamiento mediante las métricas visuales en los tableros automáticos de AWS CloudWatch —observando con precisión el pico de utilización y su posterior estabilización tras 5 minutos— ratifica que el éxito de la administración de sistemas modernos depende tanto de la capacidad de operar en la terminal de comandos de PuTTY como de la habilidad para interpretar dashboards en la nube para mantener un control de calidad riguroso en tiempo real. 
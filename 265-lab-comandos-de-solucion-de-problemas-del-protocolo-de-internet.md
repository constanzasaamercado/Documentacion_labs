# Laboratorio 265: Comandos de solución de problemas del protocolo de Internet

> **Descripción del Laboratorio:** > Este laboratorio práctico está diseñado para que te desempeñes como administrador de redes en AWS, permitiéndote practicar la resolución de problemas (troubleshooting) mediante el uso de comandos clave mapeados en el modelo OSI.
---

## 🎯 Objetivos

* Practicar con comandos de resolución de problemas (troubleshooting).
* Identificar cómo se puede utilizar estos comandos en escenarios reales con clientes.

---
## Contexto del caso

Nuevo administrador de redes que se encuentra resolviendo problemas de los clientes.

## 🛠️ Desarrollo Paso a Paso

### Inicio laboratorio: 
1. Se da por iniciado el laboratorio al iniciar el conteo. 


![Laboratorio Iniciado](265-Lab-Comandos-de-solucion-de-problemas-del-protocolo-de-Internet\1.png)
Figura 1.

### Credenciales: 
1. Se descarga el archivo **PPK**.
2. Se copia el **IPPublico**.

![Credenciales](265-Lab-Comandos-de-solucion-de-problemas-del-protocolo-de-Internet\2.png)
Figura 2.

### Practicar comandos de Capa 3 (Red): 
1. El comando **ping 8.8.8.8 -c 5** sirve para verificar si el servidor tiene salida a internet y si responde el destino. Envía paquetes ICMP. Si al final en el resumen el *packet loss* es 0%, la conectividad básica de red está perfecta.
2. El comando **traceroute 8.8.8.8** sirve para ver el camino que toma el paquete desde el servidor AWS hasta el destino final. Hay una lista enumerada cada número es un salto, si se ven asteriscos (***) significa que ese router intermedio tiene bloqueado el protocolo o falló, lo cual ayuda a diagnosticar en qué parte de la red global se traba una conexión.
   
![Practicar comandos de Capa 3 (Red)](265-Lab-Comandos-de-solucion-de-problemas-del-protocolo-de-Internet\3.png)
Figura 3.

### Practicar comandos de Capa 4 (Transporte): 
1.  El comando **netstat -tp** permite ver qué programas dentro del servidor están "escuchando" conexiones en ese momento. Se observan las conexiones TCP activas y una conexión establecida (ESTABLISHED) en el puerto 22, que es la sesión de SSH con la se que esta controlando el servidor.
2.  **sudo yum install telnet -y** Con este comando se instala la herramienta en la instancia para verificar si un puerto específico en un servidor remoto está abierto o cerrado.
3.  Con el comando **telnet www.google.com 80** se prueba si el puerto web estándar (puerto 80) de Google está accesible. Mostrando que esta conectado a *www.google.com*, ningún firewall o grupo de seguridad está bloqueando la salida hacia ese puerto. 

![Practicar comandos de Capa 4 (Transporte)](265-Lab-Comandos-de-solucion-de-problemas-del-protocolo-de-Internet\4.png)
Figura 4.

### Practicar comandos de Capa 7 (Aplicación): 
1.  Se ejecuta el siguiente comando **curl -vLo /dev/null https://aws.com** para analizar de forma detallada la conexión a AWS y descartar el diseño visual enviándolo a */dev/null*.

![Practicar comandos de Capa 7 (Aplicación)1](265-Lab-Comandos-de-solucion-de-problemas-del-protocolo-de-Internet\5.png)
Figura 5.
![Practicar comandos de Capa 7 (Aplicación)2](265-Lab-Comandos-de-solucion-de-problemas-del-protocolo-de-Internet\6.png)
Figura 6.

### Submit: 
1. Cargado a **submit** el laboratorio y entregado. 

![Submit](265-Lab-Comandos-de-solucion-de-problemas-del-protocolo-de-Internet\7.png)
Figura 7.

### Finalización del laboratorio: 
1. Con el laboratorio terminado se procede a finalizar correctamente.

![Finalización del laboratorio](265-Lab-Comandos-de-solucion-de-problemas-del-protocolo-de-Internet\8.png)
Figura 8.

## 💡 Conclusión y Comentarios Personales

La realización de este laboratorio permitió adquirir competencias críticas en el diagnóstico y la resolución de problemas de red estructurados dentro de entornos Linux hospedados en Amazon EC2. El uso de comandos como **ping 8.8.8.8 -c 5** junto con la definición analítica de variables de conectividad demostró ser fundamental para mitigar riesgos operacionales y evaluar dinámicamente el estado de la red en la Capa 3; por otra parte, la incorporación de herramientas como **traceroute**, **netstat -tp** y **telnet** sirvió como un valioso caso de estudio sobre el flujo lógico del modelo OSI, permitiendo identificar saltos fallidos, auditar puertos en escucha y verificar la apertura de sockets de transporte de forma precisa. Validar finalmente la correcta respuesta de la Capa 7 mediante el uso de **curl -vLo /dev/null https://aws.com** y confirmar la obtención de códigos exitosos ratifica que el éxito en la administración moderna de TI depende tanto de garantizar la accesibilidad y seguridad de los servicios locales como de asegurar un monitoreo técnico riguroso para la gobernanza eficiente de recursos en la nube.
# Laboratorio 243: Administración del software

> **Descripción del Laboratorio:** > Este laboratorio práctico se divide en dos grandes etapas: administración del sistema operativo Linux a nivel local y conexión de la terminal con los servicios de la nube de AWS.

---

## 🎯 Objetivos

* Actualizar la máquina Linux utilizando el gestor de paquetes.
* Revertir (roll back) o degradar (downgrade) un paquete previamente actualizado a través del gestor de paquetes.
* Instalar la interfaz de línea de comandos de AWS (AWS CLI).

---

## 🛠️ Desarrollo Paso a Paso

### Inicio laboratorio: 
1. Se da por iniciado el laboratorio al iniciar el conteo. 


![Laboratorio Iniciado](243-Lab-Administración-del-software\1.png)
Figura 1.

### Credenciales: 
1. Se descargar el archivo **PPK**.
2. Se copia el **IPPublico**.

![Credenciales](243-Lab-Administración-del-software\2.png)
Figura 2.

### Actualizar tu máquina Linux 1: 
1. Se inicia correctamente la sesion en la terminal bash de **PuTTY** con el sistema Linux. **pwd** Valida que se encuentre en la carpeta de inicio (home) del usuario actual escribiendo. **cd companyA** se ingresa a la terminal para trabajar en ese directorio. **sudo yum -y check-update** Se utiliza este comando para consultar en los repositorios las actualizaciones disponibles. Para aplicar las actualizaciones relacionadas con seguridad se utilizan los comandos **sudo yum update --security**. **sudo yum -y upgrade** se usa con el fin de actualizar los paquetes.
   

![Actualizar tu máquina Linux 1](243-Lab-Administración-del-software\3.png)
Figura 3.

### Actualizar tu máquina Linux 2: 
1. Con **sudo yum install httpd -y** se instala httpd y se ve el historial de actualizaciones previas. 

![Actualizar tu máquina Linux 2](243-Lab-Administración-del-software\4.png)
Figura 4.

### Revertir un paquete (Roll back) 1: 
1.  **sudo yum history list** Para ver el historial de actualizaciones. Se toma nota del número debajo de EC2, que es "1".

![Revertir un paquete (Roll back) 1](243-Lab-Administración-del-software\5.png)
Figura 5.

### Revertir un paquete (Roll back) 2:
1. Para deshacer la transacción se utilizan los comandos **sudo yum -y history undo 1** con el número anotado anteriormente.


![Revertir un paquete (Roll back) 2](243-Lab-Administración-del-software\6.png)
Figura 6.

### Instalar AWS CLI en Red Hat Linux 1: 
1.  Para instalar AWS CLI se reviso que python estuviera instalado con el comando **python3 --version**, el cual si estaba instalado, luego para ver si el gestor de paquetes pip ya estaba instalado se ejecuto **pip3 --version** el cual tambien estaba instalado. A continuación se uso el comando **curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"** para descargar el archivo de instalación indicando el nombre del archivo descargado. Se descomprime el instalador con el comando **unzip awscliv2.zip** creando una carpeta llamada "aws" en el directorio. Se ejecuta el programa de instalación **sudo ./aws/install**.
    **aws help** Se ejecuta este comando para verificar que AWS CLI funciona correctamente.

![Instalar AWS CLI en Red Hat Linux 1](243-Lab-Administración-del-software\7.png)
Figura 7.

### Instalar AWS CLI en Red Hat Linux 2: 
1.  Se selecciona "show" al lado de "AWS CLI" para mostrar las credenciales, incluyendo el *aws_access_key_id* y el *aws_secret_access_key*, copiado a un block de notas.

![Instalar AWS CLI en Red Hat Linux 2](243-Lab-Administración-del-software\8.png)
Figura 8.

### Configurar AWS CLI para conectarse a tu cuenta de AWS 1: 
1.  Se introduce el comando **aws configure** para configurar las credenciales, al intentar la primera vez cometi el error de ingresar donde no correspondian los datos, por lo que, se prodece a eliminar lo ingresado con el comando **rm -f ~/.aws/credentials**, para luego volver a ingresar **aws configure**, configurando de forma correcta, con los primeros dos datos vacios, para "Default region name" la región "us-west-2" y para "Default output format" el formato "json".
   **sudo nano ~/.aws/credentials** con este comando se abre el archivo de credenciales para editarlo.

![Configurar AWS CLI para conectarse a tu cuenta de AWS 1](243-Lab-Administración-del-software\9.png)
Figura 9.

### Configurar AWS CLI para conectarse a tu cuenta de AWS 2: 
1.  Se procede a insertar el texto copiado de las credenciales de "AWS CLI". Se guarda y cierra.

![Configurar AWS CLI para conectarse a tu cuenta de AWS 2](243-Lab-Administración-del-software\10.png)
Figura 10.

### Configurar AWS CLI para conectarse a tu cuenta de AWS 3: 
1.  Se abre EC2 para encontrar y copiar la ID de la instancia.

![Configurar AWS CLI para conectarse a tu cuenta de AWS 3](243-Lab-Administración-del-software\11.png)
Figura 11.

### Configurar AWS CLI para conectarse a tu cuenta de AWS 4: 
1.  **aws ec2 describe-instance-attribute --instance-id i-0ab888afaa088e740 --attribute instanceType**. Mostrando con exito la información del tipo de instancia.

![Configurar AWS CLI para conectarse a tu cuenta de AWS 4](243-Lab-Administración-del-software\12.png)
Figura 12.

### Submit: 
1. Cargado a **submit** el laboratorio y entregado.

![Submit](243-Lab-Administración-del-software\13.png)
Figura 13.

### Finalización del laboratorio: 
1. Con el laboratorio terminado se procede a finalizar correctamente.

![Finalización del laboratorio](243-Lab-Administración-del-software\14.png)
Figura 14.

## 💡 Conclusión y Comentarios Personales

La realización de este laboratorio permitió adquirir competencias críticas en el mantenimiento del sistema operativo mediante el gestor de paquetes **Yum** y en el despliegue integrado de herramientas de nube con AWS CLI. El uso de comandos como **sudo yum -y upgrade** junto con auditorías de reversión como **sudo yum -y history undo 1** demostró ser fundamental para mitigar riesgos operacionales ante actualizaciones incompatibles; por otra parte, la resolución del incidente surgido durante el comando **aws configure** sirvió como un valioso caso de estudio sobre la rectificación de entornos mediante **rm -f ~/.aws/credentials** e inserción manual en *sudo nano*. Validar finalmente la conexión exitosa mediante la consulta de metadatos remotos con **aws ec2 describe-instance-attribute** ratifica que el éxito en la administración moderna de TI depende tanto de garantizar la estabilidad de los paquetes locales como de asegurar una comunicación precisa con la consola de AWS para la gobernanza de recursos en tiempo real.  
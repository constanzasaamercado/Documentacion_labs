# Laboratorio 235: Trabajo con archivos

> **Descripción del Laboratorio:** > Este laboratorio práctico se enfoca en la automatización de respaldos, la generación de registros (logs) y la transferencia de datos en un entorno Linux (Amazon EC2) mediante la línea de comandos.

---

## 🎯 Objetivos

* Crear un archivo de respaldo (backup) de una estructura completa de carpetas utilizando **tar**.
* Registrar la creación del respaldo en un archivo que incluya la fecha, la hora y el nombre del archivo de respaldo.
* Transferir el archivo de respaldo a otra carpeta.

---

## 🛠️ Desarrollo Paso a Paso

### Inicio laboratorio: 
1. Se da por iniciado el laboratorio al iniciar el conteo.

![Laboratorio Iniciado](235-Lab-Trabajo-con-archivos\1.png)
Figura 1.

### Credenciales: 
1. Se descarga el archivo **PPK**.
2. Se copia el **IPPublico**.

![Credenciales](235-Lab-Trabajo-con-archivos\2.png)
Figura 2.

### Terminal Bash inicio: 
1. Se inicia correctamente la sesion en la terminal bash de **PuTTY** con el sistema Linux. **pwd** Valida que se encuentre en la carpeta de inicio (home) del usuario actual escribiendo. Para validar que la carpeta "CompanyA" existe, se introduce el comando en la terminal **ls -R CompanyA**.

![Terminal Bash inicio](235-Lab-Trabajo-con-archivos\3.png)
Figura 3.

### Crear y Registrar un respaldo: 
1. **tar -csvpzf backup.CompanyA.tar.gz CompanyA** Este comando se utiliza para crear respaldos de la estructura de carpetas, en el resultado muestra que se realizo. 
2. **cd /home/ec2-user/CompanyA** para navegar hacia la carpeta *CompanyA*, se introduce el comando en la terminal. Luego para crear un archivo de registro vacío llamado *backups.csv*, se digita el comando **touch SharedFolders/backups.csv**. **echo "25 Aug 25 2021, 16:59, backup.CompanyA.tar.gz" | sudo tee SharedFolders/backups.csv** con este comando se añade la fecha, la hora y el nombre del archivo al archivo.
3. Con el fin de mostrar el contenido del archivo y verificar que se guardó, se utiliza el comando **cat SharedFolders/backups.csv**

![Crear y Registrar un respaldo](235-Lab-Trabajo-con-archivos\4.png)
Figura 4.

### Mover el archivo de respaldo: 
1. Para validar que se encuentra dentro de la carpeta *CompanyA* en la terminal, se introduce **pwd**. Para transferir el archivo de respaldo al directorio del equipo de IA, introduce **mv ../backup.CompanyA.tar.gz IA/** a la terminal, como resultado indica que no se encuentra el respaldo, por lo que ingrese el comando **sudo find / -name "'CompanyA'"** aun seguia sin mostrarse, procedi a cambiar la busqueda a **sudo find / -name "'.tar.gz'"**, por este medio lo encontro, conclui que al digitar el nombre del backup tuve un error al no ingresar el nombre que correspondia al respaldo, asi que, no se pudo mover. Trate de volver a abrir la sesión en la terminal pero aprendí que en el mismo laboratorio las acciones se respaldan. Por lo que decidí seguir con el nombre que le coloque, para continuar con las instrucciones del laboratorio.
**mv /home/ec2-user/backup.tar.gz IA/** usando el comando de esa manera se movio tal como indicaba la instrucción, confirmado con el comando **ls . IA**.

![Mover el archivo de respaldo](235-Lab-Trabajo-con-archivos\5.png)
Figura 5.

### Submit: 
1. Cargado a **submit** el laboratorio y entregado.

![Submit](235-Lab-Trabajo-con-archivos\6.png)
Figura 6.

### Finalización del laboratorio: 
1. Con el laboratorio terminado se procede a finalizar correctamente.

![Finalización del laboratorio](235-Lab-Trabajo-con-archivos\7.png)
Figura 7.

## 💡 Conclusión y Comentarios Personales

La ejecución de este laboratorio permitió adquirir competencias clave en materia de seguridad, integridad de datos y continuidad operativa dentro de un entorno Linux. La utilización de la herramienta **tar** con los parámetros **-csvpzf** demostró ser un método altamente eficiente para empaquetar y comprimir estructuras completas de datos organizacionales (como *CompanyA*), reduciendo el uso de espacio en disco y facilitando su distribución. Asimismo, el uso combinado de **touch**, **echo** y **tee** sirvió para comprender la importancia de mantener una bitácora de auditoría centralizada (*backups.csv*), registrando de forma estricta la fecha, hora y nombre de cada respaldo para garantizar la trazabilidad de la información.

Un hito fundamental de la práctica fue la resolución de problemas en la línea de comandos durante la transferencia del archivo. Al enfrentarse a un error de localización debido a una discrepancia en el nombre original del respaldo, el laboratorio se convirtió en un excelente caso de estudio de diagnóstico de fallas: el uso de búsquedas indexadas con privilegios elevados (**sudo find / -name ".tar.gz"**) permitió rastrear con éxito la ubicación exacta del elemento. Comprender que en los entornos de laboratorios las acciones previas se mantienen persistentes facilitó adaptar la estrategia y concretar la reubicación del archivo hacia el directorio de destino (*IA/*) mediante el comando **mv**. En conclusión, la experiencia validó que la atención al detalle y el dominio de herramientas de búsqueda son aptitudes indispensables para mantener la resiliencia en la gestión de infraestructuras tecnológicas.
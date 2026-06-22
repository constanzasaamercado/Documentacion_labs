# Laboratorio 239: Procesos administrativos

> **Descripción del Laboratorio:** > Este laboratorio práctico se enfoca en la administración de procesos del sistema y la automatización de tareas repetitivas en un entorno Linux (Amazon EC2) mediante la línea de comandos.

---

## 🎯 Objetivos

* Crear un nuevo archivo de registro (log) para listados de procesos.
* Utilizar el comando top.
* Establecer una tarea repetitiva (cron job) que ejecute los comandos de auditoría anteriores una vez al día.

---

## 🛠️ Desarrollo Paso a Paso

### Inicio laboratorio: 
1. Se da por iniciado el laboratorio al iniciar el conteo.

![Laboratorio Iniciado](239-Lab-Procesos-administrativos\1.png)
Figura 1.

### Credenciales: 
1. Se descarga el archivo **PPK**.
2. Se copia el **IPPublico**.

![Credenciales](239-Lab-Procesos-administrativos\2.png)
Figura 2.

### Crear una lista de procesos: 
1. Se inicia correctamente la sesion en la terminal bash de **PuTTY** con el sistema Linux. **pwd** Valida que se encuentre en la carpeta de inicio (home) del usuario actual escribiendo. **cd companyA** se ingresa a la terminal para trabajar en ese directorio.
   Visualiza todos los procesos que se ejecutan en la máquina y filtra la palabra root **sudo ps -aux | grep -v root | sudo tee SharedFolders/processes.csv**
2. Se valida el comando anterior con **cat SharedFolders/processes.csv**.
   
![Crear una lista de procesos](239-Lab-Procesos-administrativos\3.png)
Figura 3.

### Ejercicio - Listar los procesos usando el comando **top**: 
1. Ejecuta el comando **top** para mostrar los procesos y subprocesos (threads) activos en el sistema. Las tareas en top pueden tener un estado de ejecución, inactiva, detenida o zombi. ¿Cuántas tareas en ejecución se ven? Se ve una tarea en ejecución. Para salir de **top**, se presiona la tecla **q**.

La salida del comando top muestra el rendimiento del sistema y proporciona la siguiente información: número total de tareas, cuántas están en ejecución (running), cuántas inactivas (sleeping), cuántas detenidas (stopped) y en estado zombi. Proporciona el porcentaje de CPU utilizado, la memoria KiB utilizada y el espacio swap en KiB.

![Ejercicio - Listar los procesos usando el comando **top**](239-Lab-Procesos-administrativos\4.png)
Figura 4.

### Ejercicio - Crear una tarea cron (Cron Job) 1: 
1. Para crear una tarea cron que genere el archivo de auditoría con "#####" para cubrir todos los archivos ".csv", se introduce el comando **sudo crontab -e** en la terminal. 

![Ejercicio - Crear una tarea cron (Cron Job)](239-Lab-Procesos-administrativos\5.png)
Figura 5.

### Ejercicio - Crear una tarea cron (Cron Job) 2: 
1. Se presiona la tecla **i** para entrar en el modo de inserción (insert mode) y se procede a digitar el texto en orden, en la primera línea, se introduce *SHELL=/bin/bash* y presiona **Enter**. En la segunda línea, se digita *PATH=/usr/bin:/bin:/usr/local/bin* y presiona **Enter**. En la tercera línea, introduce *MAILTO=root* y presiona **Enter**. En la última línea, se introduce: *" 0**** ls -la $(find .) | sed -e 's/..csv/#####.csv/g' > /home/ec2-user/companyA/SharedFolders/filteredAudit.csv"*.
2. Luego para cerrar y guardar *ESC*, a continuación *:wq*.


![Ejercicio - Crear una tarea cron (Cron Job) 2](239-Lab-Procesos-administrativos\6.png)
Figura 6.

### Error de digitación: 
1.  Error debido a la falta de los espacios entre el cero y cada asterisco que representan el comando; Minuto, Hora, Día del mes, Mes, Día de la semana. Se edita el archivo al ingresar *y*.

![Error de digitación](239-Lab-Procesos-administrativos\7.png)
Figura 7.

### Correción del texto: 
1. Se presiona la tecla **i** para entrar en el modo de inserción (insert mode) y se procede a editar el texto **"0 * * * * ls -la $(find .) | sed -e 's/..csv/#####.csv/g' > /home/ec2-user/companyA/SharedFolders/filteredAudit.csv"**. Luego para cerrar y guardar *ESC*, a continuación *:wq*.

![Correción del texto](239-Lab-Procesos-administrativos\8.png)
Figura 8.

### Validar archivo crontab: 
1. Para validar que se realizo correctamente el archivo, se digita en la terminal el comando **sudo crontab -l**. Tal como muestra la imagen se corrobora que funciono.


![Validar archivo crontab](239-Lab-Procesos-administrativos\9.png)
Figura 9.

### Submit: 
1. Cargado a **submit** el laboratorio y entregado.

![Submit](239-Lab-Procesos-administrativos\10.png)
Figura 10.

### Finalización del laboratorio: 
1. Con el laboratorio terminado se procede a finalizar correctamente.

![Finalización del laboratorio](239-Lab-Procesos-administrativos\11.png)
Figura 11.

## 💡 Conclusión y Comentarios Personales

La realización de este laboratorio permitió adquirir competencias críticas en la gestión de procesos y en la automatización del mantenimiento de sistemas operativos Linux. El uso combinado de comandos como **sudo ps -aux | grep -v root | sudo tee SharedFolders/processes.csv** y el análisis en tiempo real mediante **top** demostraron ser fundamentales para la auditoría de rendimiento. Estas herramientas facultan al administrador para supervisar el consumo de recursos, identificar qué usuarios o aplicaciones sobrecargan el servidor y exportar dichos estados de forma estructurada para auditorías de TI internas en la organización.

Por otro lado, la práctica consolidó el valor estratégico de la automatización industrial mediante **Cron**. El incidente documentado al configurar el archivo **crontab** sirvió como un valioso caso de estudio sobre la rigidez sintáctica de Linux: identificar que la falta de espacios entre el indicador de minutos ("0") y los asteriscos ("* * * *") truncaba la instrucción, obligó a aplicar un flujo de rectificación inmediato reingresando al modo de inserción de Vim (**i**) para estructurar la regla correctamente. Validar finalmente la persistencia de la tarea automatizada de filtrado (**filteredAudit.csv**) con el comando **sudo crontab -l** ratifica que el éxito operativo en la nube depende tanto de delegar tareas repetitivas al sistema como de mantener un control de calidad riguroso en la consola de comandos.
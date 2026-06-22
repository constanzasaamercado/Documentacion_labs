# Laboratorio 251: Scripts del Shell Bash

> **Descripción del Laboratorio:** > Este laboratorio práctico tiene como objetivo enseñar la creación y automatización de tareas en Linux mediante el desarrollo de scripts de shell en Bash. A través de ejercicios prácticos en una instancia de Amazon EC2, aprenderás a estructurar un script utilizando la línea shebang.

---

## 🎯 Objetivos

* Crear un script de Bash que automatizará el respaldo (backup) de una carpeta.

---

## 🛠️ Desarrollo Paso a Paso

### Inicio laboratorio: 
1. Se da por iniciado el laboratorio al iniciar el conteo. 


![Laboratorio Iniciado](251-Lab-Scripts-del-shell-Bash\1.png)
Figura 1.

### Credenciales: 
1. Se descarga el archivo **PPK**.
2. Se copia el **IPPublico**.

![Credenciales](251-Lab-Scripts-del-shell-Bash\2.png)
Figura 2.

### Escribir un script de shell 1: 
1. Se inicia correctamente la sesion en la terminal bash de **PuTTY** con el sistema Linux. **pwd** Valida que se encuentre en la carpeta de inicio (home) del usuario actual escribiendo. Para crear un script de shell genérico llamado *backup.sh* se ingresa el comando **touch backup.sh**.
2. Con el comando **sudo chmod 755 backup.sh** se cambian los privilegios del archivo y se hace ejecutable.
3. Utilizar el comando **vi backup.sh** para abrir el archivo y editarlo.
   
![Escribir un script de shell 1](251-Lab-Scripts-del-shell-Bash\3.png)
Figura 3.

### Escribir un script de shell 2: 
1.  Se activa el modo de inserción del editor de texto vi con "i". La primera linea **#!/bin/bash** es la secuencia que identifica que es un ejecutable de script, luego para la siguiente linea se crea la variable para la fecha actual **DAY="$ (date+%Y_%m_%d_%T_%H_%M) "**, en la tercera linea se ingresa **BACKUP="/home/$USER/backups/$DAY-backup-CompanyA.tar.gz"** para crear una variable para el archivo de respaldo del día y en la ultima linea **tar -csvpzf $BACKUP /home/$USER/CompanyA**. Para finalizar guardar el script y salir del archivo.

![Escribir un script de shell 2](251-Lab-Scripts-del-shell-Bash\4.png)
Figura 4.

### Ejecutar un script de shell: 
1.  **./backup.sh** se ingresa el comando para ejecutar el script, resultando en un respaldo de archivo comprimido, comprobado con **ls backups/**.

![Ejecutar un script de shell](251-Lab-Scripts-del-shell-Bash\5.png)
Figura 5.

### Submit: 
1. Cargado a **submit** el laboratorio y entregado.

![Submit](251-Lab-Scripts-del-shell-Bash\6.png)
Figura 6.

### Finalización del laboratorio: 
1. Con el laboratorio terminado se procede a finalizar correctamente.

![Finalización del laboratorio](251-Lab-Scripts-del-shell-Bash\7.png)
Figura 7.

## 💡 Conclusión y Comentarios Personales

La realización de este laboratorio permitió adquirir competencias críticas en la automatización de tareas y la administración del sistema operativo mediante el desarrollo de scripts de shell en Bash. El uso de directivas esenciales como la línea shebang **#!/bin/bash** junto con la declaración de variables dinámicas basadas en comandos del sistema demostró ser fundamental para estructurar flujos de trabajo eficientes y mitigar riesgos operacionales en la gestión de archivos; por otra parte, la configuración de privilegios mediante **sudo chmod 755 backup.sh** y el empaquetamiento seguro utilizando **tar -csvpzf** sirvieron como un valioso caso de estudio sobre el aprovisionamiento de permisos adecuados y la compresión de directorios críticos de forma automatizada. Validar finalmente la correcta ejecución mediante **./backup.sh** junto con la verificación del archivo empaquetado en la ruta **ls backups/** ratifica que el éxito en la administración moderna de TI depende tanto de garantizar el resguardo de la información local como de asegurar la continuidad del negocio mediante estrategias ágiles de respaldo en entornos en la nube.
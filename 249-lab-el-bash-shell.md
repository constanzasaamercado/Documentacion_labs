# Laboratorio 249: El Bash Shell

> **Descripción del Laboratorio:** > Este laboratorio práctico tiene como objetivo enseñar la personalización y optimización del entorno de línea de comandos en Linux mediante la configuración de alias y la gestión de variables de entorno en la shell Bash.

---

## 🎯 Objetivos

* Creará y trabajará con un alias para respaldar (backup) una carpeta completa.
* Trabajará con la variable PATH y le añadirá una nueva carpeta.

---

## 🛠️ Desarrollo Paso a Paso

### Inicio laboratorio: 
1. Se da por iniciado el laboratorio al iniciar el conteo. 


![Laboratorio Iniciado](249-Lab-El-Bash-Shell\1.png)
Figura 1.

### Credenciales: 
1. Se descarga el archivo **PPK**.
2. Se copia el **IPPublico**.

![Credenciales](249-Lab-El-Bash-Shell\2.png)
Figura 2.

### Crear un alias para una operación de respaldo (Backup): 
1. Se inicia correctamente la sesion en la terminal bash de **PuTTY** con el sistema Linux. **pwd** Valida que se encuentre en la carpeta de inicio (home) del usuario actual escribiendo. Para crear un alias llamado *backup* se utiliza el comando **alias backup='tar -cvzf '**.
   **backup backup_companyA.tar.gz CompanyA** Se utiliza este comando para crear un respaldo. Debido a un error de digitación el respaldo no quedo bien.
2. Se procede a eliminar el respaldo erroneo con **rm backup_companyA.tar.gz**. Se comprueba con **ls** que fue eliminado.
3. Se vuelve a ingresar el comando, realizandose de forma exitosa el respaldo con el alias *backup*.
   
![Crear un alias para una operación de respaldo (Backup)](249-Lab-El-Bash-Shell\3.png)
Figura 3.

### Explorar y actualizar la variable de entorno PATH: 
1.  Para navegar a la carpeta bin dentro del directorio home de CompanyA, se ingresa el comando **cd /home/ec2-user/CompanyA/bin**. Con el comando **./hello.sh** se ejecuta el script de saludo al usuario.
   Para navegar a la carpeta padre, se ingresa el siguiente comando **cd /home/ec2-user/CompanyA**. Se ejecuta **./bin/hello.sh** resulando en el saludo nuevamente.
2. Al ejecutar **hello.sh** por si solo, no se puede ejecutar el comando.
3. Para mostrar el valor actual de la variable *PATH*, se ingresa el siguiente comando **echo $PATH**. Siendo esta una lista de carpetas donde el sistema busca ejecutables, se añade la carpeta */home/ec2-user/CompanyA/bin* a la variable *PATH* con el comando **PATH=$PATH:/home/ec2-user/CompanyA/bin**. Se ejcuta nuevamente **hello.sh** y resulta exitoso como muestra la imagen.

![Explorar y actualizar la variable de entorno PATH](249-Lab-El-Bash-Shell\4.png)
Figura 4.

### Submit: 
1. Cargado a **submit** el laboratorio y entregado.

![Submit](249-Lab-El-Bash-Shell\5.png)
Figura 5.

### Finalización del laboratorio: 
1. Con el laboratorio terminado se procede a finalizar correctamente.

![Finalización del laboratorio](249-Lab-El-Bash-Shell\6.png)
Figura 6.

## 💡 Conclusión y Comentarios Personales

La realización de este laboratorio permitió adquirir competencias críticas en la personalización y optimización de la interfaz de línea de comandos mediante la configuración de alias y la gestión de variables de entorno en la shell Bash. El uso de comandos como **alias backup='tar -cvzf '** junto con el empaquetamiento del directorio CompanyA demostró ser fundamental para automatizar tareas rutinarias de respaldo y compresión de archivos de forma eficiente; por otra parte, la resolución del incidente surgido debido a un error de digitación durante el primer respaldo sirvió como un valioso caso de estudio sobre la rectificación ágil de entornos mediante **rm** y la verificación inmediata con **ls**. Validar finalmente la ejecución global del script **hello.sh** desde cualquier ubicación tras expandir la ruta del sistema mediante **PATH=$PATH:/home/ec2-user/CompanyA/bin** ratifica que el éxito en la administración moderna de TI depende tanto de simplificar los flujos de trabajo locales como de asegurar una configuración precisa de las variables del entorno para la gobernanza y ejecución de recursos en tiempo real.
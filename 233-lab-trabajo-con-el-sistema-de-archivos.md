# Laboratorio 233: Trabajo con el sistema de archivos

> **Descripción del Laboratorio:** > Este laboratorio práctico enseña a administrar archivos y directorios en un servidor Linux (Amazon EC2) a través de la línea de comandos.

---

## 🎯 Objetivos

* Crear una estructura de carpetas provista por este laboratorio.
* Crear archivos.
* Copiar y mover archivos y directorios.
* Eliminar archivos y directorios.

---

## 🛠️ Desarrollo Paso a Paso

### Inicio laboratorio: 
1. Se da por iniciado el laboratorio al iniciar el conteo.

![Laboratorio Iniciado](233-Lab-Trabajo-con-el-sistema-de-archivos\1.png)
Figura 1.

### Credenciales: 
1. Se descarga el archivo **PPK**.
2. Se copia el **IPPublico**.

![Credenciales](233-Lab-Trabajo-con-el-sistema-de-archivos\2.png)
Figura 2.

### Terminal Bash inicio: 
1. Se inicia correctamente la sesion en la terminal bash de **PuTTY** con el sistema Linux. **pwd** Valida que se encuentre en la carpeta de inicio (home) del usuario actual escribiendo.

![Terminal Bash inicio](233-Lab-Trabajo-con-el-sistema-de-archivos\3.png)
Figura 3.

### Crear una estructura de carpetas 1: 
1. **mkdir CompanyA** Este comando se utiliza para crear carpetas. Luego se debe usar el comando **cd CompanyA** para posicionarse en la carpeta "CompanyA".

![Crear una estructura de carpetas 1](233-Lab-Trabajo-con-el-sistema-de-archivos\4.png)
Figura 4.

### Crear una estructura de carpetas 2: 
1. **mkdir Finance HR Management** Se crean las sub carpetas dentro de **CompanyA**, se usa el comando **ls** para verificar la creación y resulta correcto.
2. Con el comando **cd HR** se posiciona dentro del directorio **HR**, luego con el comando **touch Assessments.csv TrialPeriod.csv** para crear los archivos vacíos dentro de la carpeta HR. Con **ls** para verificar la creación y resulta correcto.
3. Despues de probar varias formas de cambiar de directorio, el comando que resulto fue **cd /home/ec2-user/CompanyA/Finance**, se debia especificar bien la dirección, ya que se encontraba posicionado en una carpeta dentro de **HR**.
4. **touch Salary.csv ProfitAndLossStatements.csv** Con este comando se crean los archivos dentro de la carpeta de Finance y con **ls** se valida.
5. Con **cd** se vuelve a al directorio de origen **/home/ec2-user**, con **cd CompanyA** se ingresa a ese directorio, desde de aqui se digita el comando **touch Management/Managers.csv Management/Schedule.csv** para crear los nuevos archivos vacíos en la carpeta Management desde afuera. Al ingresar **ls Management** se valida la correcta creación de los archivos.

![Crear una estructura de carpetas 2](233-Lab-Trabajo-con-el-sistema-de-archivos\5.png)
Figura 5.

### Validación de creación de carpetas: 
1. **ls -laR** Con este comando se valida que todos las carpetas y archivos han sido creados correctamente.


![Validación de creación de carpetas](233-Lab-Trabajo-con-el-sistema-de-archivos\6.png)
Figura 6.

### Eliminar y reorganizar carpetas: 
1.  Primero hay que asegurarse de estar en el directorio correcto con **pwd**, estando en **CompanyA** se procede a digitar el comando **cp -r Finance HR** para copiar la carpeta Finance y todo su contenido.
2. **ls HR/Finance** para verificar que la carpeta y el contenido se hayan copiado correctamente, lo cual se confirma en la imagen.
3. **rmdir Finance** para eliminar la carpeta Finance de la estructura original de **CompanyA**, pero como funciona únicamente en directorios vacíos, se debe eliminar los archivos dentro de la carpeta primeor y luego eliminar la carpeta Finance. Con **rm Finance/ProfitAndLossStatements.csv Finance/Salary.csv** se eliminan los archivos dentro de la carpeta pero la primera vez por error de digitación no funciono se repite el proceso. Se verifica que la carpeta esta vacia con **ls Finance**, por lo que se procede a volver a repetir el comando **rmdir Finance** para esta vez eliminar con exito la carpeta comprobado con el comando **ls**.


![Eliminar y reorganizar carpetas](233-Lab-Trabajo-con-el-sistema-de-archivos\7.png)
Figura 7.

### Mover carpetas: 
1. Para mover la carpeta Management dentro de la carpeta HR, se introduce **mv Management HR** y se verifica que se realizo correctamente con el comando **ls . HR/Management**.

![Mover carpetas](233-Lab-Trabajo-con-el-sistema-de-archivos\8.png)
Figura 8.

### Mover archivos: 
1. Para crear la carpeta Employees, introduce **mkdir Employees**. Se procede a a verificar la creación de la carpeta con **ls**.
2. Para mover los archivos a esta nueva carpeta, se debe digitar **mv Assessments.csv TrialPeriod.csv Employees**, pero me da error por una equivocación al digitar "Employees", ingrese erroneamente "Employess", por lo que no permitio mover los archivos. Luego de que buscara con el comando **ls . Employees** me percate del error y debi eliminar la carpeta con **rmdir Employess**, para a continuación crear de forma correcta la carpeta con **mkdir Employees**. Se procedio a volver a colocar el comando **mv Assessments.csv TrialPeriod.csv Employees**, corroborando con **ls . Employees** que se movieron los archivos a la carpeta "Employees" correctamente.

![Mover archivos](233-Lab-Trabajo-con-el-sistema-de-archivos\9.png)
Figura 9.

### Submit: 
1. Cargado a **submit** el laboratorio y entregado.

![Submit](233-Lab-Trabajo-con-el-sistema-de-archivos\10.png)
Figura 10.

### Finalización del laboratorio: 
1. Con el laboratorio terminado se procede a finalizar correctamente.

![Finalización del laboratorio](233-Lab-Trabajo-con-el-sistema-de-archivos\11.png)
Figura 11.

## 💡 Conclusión y Comentarios Personales

La realización de este laboratorio proporcionó un aprendizaje crucial sobre la administración, estructuración y mantenimiento del sistema de archivos en Linux mediante la línea de comandos. La creación de la estructura corporativa *CompanyA* y sus subcarpetas departamentales (*HR*, *Finance*, *Management*) demostró cómo un administrador puede maquetar de forma lógica el entorno de almacenamiento de una organización utilizando comandos esenciales como **mkdir** y **touch**. Un hito técnico importante de la práctica fue la navegación entre directorios; experimentar dificultades para cambiar de ruta estando dentro de *HR* reforzó la necesidad de especificar correctamente las rutas absolutas **cd /home/ec2-user/CompanyA/Finance** para asegurar un desplazamiento preciso dentro del árbol de directorios.

Asimismo, las tareas de reorganización y eliminación de datos pusieron de manifiesto reglas de seguridad operativas fundamentales en entornos UNIX. Utilizar el comando **rmdir** expuso de manera práctica que el sistema protege los directorios con contenido, obligando al operador a vaciar primero los archivos **rm** antes de poder suprimir la carpeta de origen. Por último, la resolución del percance con la carpeta *Employees* (donde un error de digitación obligó a auditar con **ls**, destruir con **rmdir** y reconstruir correctamente) subraya que la atención al detalle y la verificación constante mediante comandos de control como **ls -laR** son competencias indispensables para cualquier profesional de TI encargado de gestionar la integridad de la información empresarial.
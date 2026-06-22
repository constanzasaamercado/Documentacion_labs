# Laboratorio 237: Administración de los permisos de archivos

> **Descripción del Laboratorio:** > Este laboratorio práctico se enfoca en la seguridad del sistema de archivos mediante la administración de propietarios (chown) y permisos de acceso (chmod) en Linux a través de la terminal.

---

## 🎯 Objetivos

* Cambiar todos los permisos de carpetas y archivos para que coincidan con la estructura de grupos adecuada.
* Modificar los permisos de archivos para un usuario específico.
* Actualizar la estructura de carpetas de la empresa.

---

## 🛠️ Desarrollo Paso a Paso

### Inicio laboratorio: 
1. Se da por iniciado el laboratorio al iniciar el conteo.

![Laboratorio Iniciado](237-Lab-Administracion-de-los-permisos-de-archivos\1.png)
Figura 1.

### Credenciales: 
1. Se descarga el archivo **PPK**.
2. Se copia el **IPPublico**.

![Credenciales](237-Lab-Administracion-de-los-permisos-de-archivos\2.png)
Figura 2.

### Terminal Bash inicio y Cambiar la propiedad de archivos, y carpetas: 
1. Se inicia correctamente la sesión en la terminal bash de **PuTTY** con el sistema Linux. **pwd** Valida que se encuentre en la carpeta de inicio (home) del usuario actual escribiendo. Para ingresar  a la carpeta "CompanyA", se introduce el comando en la terminal **cd companyA**, para esto se debio cambiar la "C" mayuscula por una minuscula.
2. Para cambiar la propiedad de toda la estructura de la carpeta *companyA* al CEO (*mjackson*) y el grupo a *Personnel*, se introduce el comando **sudo chown -R mjackson:Personnel /home/ec2-user/companyA**, luego para cambiar la propiedad de la carpeta *HR* al gerente de Recursos Humanos (*ljuan*) el comando **sudo chown -R ljuan:HR HR**, por ultimo para cambiar la propiedad de la carpeta *HR/Finance* al gerente de finanzas (*mmajor*) se usa el comando **sudo chown -R mmajor:Finance HR/Finance**. Para validar se utiliza la función recursiva del comando de listado **ls -laR**.

![Terminal Bash inicio y Cambiar la propiedad de archivos, y carpetas](237-Lab-Administracion-de-los-permisos-de-archivos\3.png)
Figura 3.

### Visualización de resultados de **ls -laR**: 
1. Se ve el detalle del resultado del comando.

![Visualización de resultados de **ls -laR** 1](237-Lab-Administracion-de-los-permisos-de-archivos\4.png)
Figura 4.


![Visualización de resultados de **ls -laR** 2](237-Lab-Administracion-de-los-permisos-de-archivos\5.png)
Figura 5.

### Cambiar los modos de permisos y Asignar permisos: 
1. Se utiliza *Vim* para crear un archivo llamado "symbolic_mode_file". Para crear este archivo, se introduce **sudo vi symbolic_mode_file** en la terminal, luego esc y **:wq** para guardar y cerrar.
   Para utilizar el modo simbólico de chmod y modificar los permisos del archivo, se introduce el comando **sudo chmod g+w symbolic_mode_file** (Se otorga permisos de escritura (w) al grupo propietario (g) sobre el archivo symbolic_mode_file.)
2. Se utiliza Vim para crear otro archivo llamado "absolute_mode_file". Para crearlo, se digita en la terminal **sudo vi absolute_mode_file**, luego esc y **:wq** para guardar y cerrar.Para utilizar el modo absoluto (numérico) de *chmod* y cambiar los permisos, se introduce el comando **sudo chmod 764 absolute_mode_file** (El código 764 significa que el usuario propietario tiene permisos de lectura, escritura y ejecución (7); el grupo tiene permisos de lectura y escritura (6); y los otros usuarios tienen solo permiso de lectura (4) sobre el archivo "absolute_mode_file").
   Para confirmar las acciones realizadas, se introduce el comando **ls -l**.
 
3. Para validar que se esta en la carpeta /home/ec2-user/companyA, el comando **pwd**. Para cambiar la propiedad de la carpeta "Shipping" a "eowusu" (el gerente de envíos actual) y el grupo a Shipping, se digita el comando **sudo chown -R eowusu:Shipping Shipping** y para cambiar la propiedad de la carpeta "Sales" a "nwolf" (el gerente de ventas actual) y el grupo a Sales, introduce el siguiente comando **sudo chown -R nwolf:Sales Sales**.
   Para validar que los comandos funcionaron, se utiliza **ls** en las carpetas que se modificaron.

![Cambiar los modos de permisos y Asignar permisos](237-Lab-Administracion-de-los-permisos-de-archivos\6.png)
Figura 6.

### Submit: 
1. Cargado a **submit** el laboratorio y entregado.

![Submit](237-Lab-Administracion-de-los-permisos-de-archivos\7.png)
Figura 7.

### Finalización del laboratorio: 
1. Con el laboratorio terminado se procede a finalizar correctamente.

![Finalización del laboratorio](237-Lab-Administracion-de-los-permisos-de-archivos\8.png)
Figura 8.

## 💡 Conclusión y Comentarios Personales

La realización de este laboratorio fue de gran valor práctico, ya que permitió comprender cómo se implementan los controles de seguridad y la gobernanza de accesos dentro de un sistema operativo empresarial Linux. A través del uso de comandos de asignación de propiedad como **sudo chown -R**, se simuló un escenario real de delegación corporativa, transfiriendo de manera estricta la responsabilidad de los directorios departamentales a sus respectivos líderes (el gerente *eowusu* para la carpeta *Shipping* y el gerente *nwolf* para la carpeta *Sales*). Esta acción demuestra cómo los sistemas de TI reflejan de forma segura el organigrama y los roles de una compañía.

Asimismo, la práctica consolidó el dominio sobre las dos metodologías esenciales de gestión de accesos con **chmod**. Experimentar con el *modo simbólico* (**u+x**) sirvió para comprender cómo añadir atributos específicos a un usuario sin alterar los existentes, mientras que la configuración en *modo absoluto* (**664**) evidenció la precisión matemática de los valores octales para definir simultáneamente los derechos de lectura y escritura del propietario, el grupo y el resto de los usuarios sobre archivos críticos como "absolute_mode_file". En conclusión, saber balancear la propiedad de archivos y sus permisos de ejecución constituye una competencia indispensable para asegurar los activos digitales de una organización y evitar filtraciones o modificaciones no autorizadas.
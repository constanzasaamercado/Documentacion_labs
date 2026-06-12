# Laboratorio 229: Usuarios y grupos

> **Descripción del Laboratorio:** > En esta práctica de laboratorio, .

---

## 🎯 Objetivos

* Crear nuevos usuarios con una contraseña predeterminada.
* Crear grupos y asignar los usuarios correspondientes.
* Iniciar sesión como diferentes usuarios.

---

## 🛠️ Desarrollo Paso a Paso

### Inicio laboratorio: 
1. Se da por iniciado el laboratorio al iniciar el conteo.

![Laboratorio Iniciado](229-Lab-Usuarios-y-grupos\1.png)
Figura 1.

### Credenciales: 
1. Se descargar el archivo **PPK**.
2. Se copia el **IPPublico**.

![Credenciales](229-Lab-Usuarios-y-grupos\2.png)
Figura 2.

### Terminal Bash inicio: 
1. Se inicia correctamente la sesion en la terminal bash de **PuTTY** con el sistema Linux. **pwd** Valida que se encuentre en la carpeta de inicio (home) del usuario actual escribiendo.

![Terminal Bash inicio](229-Lab-Usuarios-y-grupos\3.png)
Figura 3.

### Crear usuarios 1: 
1. Para agregar a un usuario se utiliza el comando **sudo useradd arosalez**. arosalez es el usuario creado. **sudo passwd arosalez** para agregar una contraseña, se pide ingresar una contraseña y reitararla para corroborar.
2. Para validar que los usuarios han sido creados, se introduce el comando **sudo cat /etc/passwd | cut -d: -f1**. 
3. Al final de la lista se puede confirmar que el usuario ha sido creado.

![Crear usuarios 1](229-Lab-Usuarios-y-grupos\4.png)
Figura 4.

### Crear usuarios 2: 
1. Se crea el usuario jdoe.
2. Se crea el usuario ljuan.
3. Se crea el usuario mmajor.
4. Se crea el usuario mjackson.
5. Se crea el usuario nwolf.
6. Se crea el usuario psantos.
7. Se crea el usuario smartinez.
8. Se crea el usuario ssarkar.

Se utilizan los comandos **sudo useradd < ID de Usuario >** y **sudo passwd < ID de Usuario >** para crear cada usuario de forma independiente.

![Crear usuarios 2](229-Lab-Usuarios-y-grupos\5.png)
Figura 5.

### Validación de creación de usuarios: 
1. **sudo cat /etc/passwd | cut -d: -f1** Con este comando se valida que todos los usuarios han sido creados correctamente.


![Validación de creación de usuarios](229-Lab-Usuarios-y-grupos\6.png)
Figura 6.

### Crear grupos: 
1. **sudo groupadd < nombre de grupo >** Con este comando se añaden los grupos. **cat /etc/group** con este comando se ha verificado que todos los grupos fueron agregados.

Los grupos creados:
* Sales (Ventas)
* HR (Recursos Humanos)
* Finance (Finanzas)
* Shipping (Envíos)
* Managers (Gerentes)
* CEO (Director Ejecutivo)

![Crear grupos](229-Lab-Usuarios-y-grupos\7.png)
Figura 7.

### Asignar usuarios a grupos: 
1. **sudo usermod -a -G < Nombre del Grupo > < ID de Usuario >** Con este comando se agregan los usuarios a sus grupos correspondientes. El comando no encontrado fue error de digitación en ves de escribir "usermod", se escribio "usermmod", se corrige.
2. El comando no encontrado fue error de digitación en ves de escribir "sudo", se escribio "suod", se corrige. Se continuan agregando usuarios restantes a su grupo correspondiente.
3. Usuarios agregados a sus grupos
4. Para comprobar la membresía de los grupos se introduce **sudo cat /etc/group**.

![Asignar usuarios a grupos](229-Lab-Usuarios-y-grupos\8.png)
Figura 8.

### Validación de usuarios a grupos: 
1. Se verifica que todos los usuarios fueron agregados a sus grupos correctamente.

![Validación de usuarios a grupos](229-Lab-Usuarios-y-grupos\9.png)
Figura 9.

### Iniciar sesión usando los nuevos usuarios: 
1. Se introduce **su arosalez**, se ingresa la contraseña y Ahora se inicio sesión como arosalez.
2. Con **pwd** se asegura que se encuentra en el directorio **/home/ec2-user**. Se digita **touch miArchivo.txt**, recibiendo el mensaje de error (Permiso denegado) porque el usuario arosalez no cuenta con permisos de escritura en la carpeta de inicio de ec2-user.
3. Se intenta realizar la acción como administrador usando el comando **sudo touch miArchivo.txt**, se ingresa la contraseña y se recibe este mensaje porque el usuario arosalez no está incluido en la lista del archivo de sudoers. Los sudoers son usuarios que tienen derechos especiales para ejecutar comandos que requieren privilegios de root. Solo unos pocos usuarios seleccionados deben recibir este permiso.
   
Se introduce **exit** para salir.

![Iniciar sesión usando los nuevos usuarios](229-Lab-Usuarios-y-grupos\10.png)
Figura 10.

### Visualización de archivo de seguridad: 
1. Ahora Se introduce el comando **sudo cat /var/log/secure** para visualizar el contenido del archivo de seguridad. Al final del archivo se puede observar cómo una acción de sudo no permitida quedó registrada de manera estricta dentro del archivo.

![Visualización de archivo de seguridad](229-Lab-Usuarios-y-grupos\11.png)
Figura 11.

### Submit: 
1. Cargado a **submit** el laboratorio y entregado.

![Submit](229-Lab-Usuarios-y-grupos\12.png)
Figura 12.

### Finalización del laboratorio: 
1. Con el laboratorio terminado se procede a finalizar correctamente.

![Finalización del laboratorio](229-Lab-Usuarios-y-grupos\13.png)
Figura 13.

## 💡 Conclusión y Comentarios Personales

La realización de este laboratorio fue de gran valor práctico, ya que permitió conectar la gestión de estructuras organizacionales con la administración técnica de sistemas operativos Linux. El ejercicio de dar de alta cuentas individuales "useradd" y establecer contraseñas seguras "passwd" para colaboradores como *arosalez* o *jdoe*, sumado a la creación de departamentos clave de la empresa; *Sales*, *HR*, *Finance*, *Shipping*, *Managers* y *CEO*, mediante "groupadd", representa la base operativa para modelar el organigrama y los roles de una compañía en un entorno de TI seguro.

Por otra parte, la fase experimental de inicio de sesión "su" puso de manifiesto principios críticos de ciberseguridad y auditoría interna. El error de "Permiso denegado" al intentar escribir en directorios ajenos y el bloqueo del comando "sudo" reflejan el correcto funcionamiento del principio de menor privilegio, demostrando que los usuarios no pertenecientes al archivo de *sudoers* no pueden comprometer el sistema. Finalmente, validar que cada uno de estos intentos de infracción quedó estrictamente registrado con fecha y hora dentro del archivo de seguridad **/var/log/secure** consolida la importancia de la trazabilidad y la auditoría informática para resguardar la confidencialidad y los activos de la organización.
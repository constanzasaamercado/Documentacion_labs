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
1. Se inicia correctamente la sesion en la terminal bash de **PuTTY** con el sistema Linux. **pwd** Te muestra en 

![Terminal Bash inicio](229-Lab-Usuarios-y-grupos\3.png)
Figura 3.

### Crear usuarios: 
1. Para mostrar el nombre de usuario actual se utiliza el comando **whoami**.
2. Para mostrar una versión abreviada del nombre de host del equipo se utiliza el comando **hostname -s**.
3. Para mostrar el tiempo que el sistema lleva encendido en un formato de fácil lectura se utiliza el comando **uptime -p**.
4. Para mostrar información detallada sobre los usuarios que han iniciado sesión se utiliza el comando **who -H -a**.


![Crear usuarios](229-Lab-Usuarios-y-grupos\4.png)
Figura 4.

### Ejecutar comandos familiares 2: 
1. **TZ=America/New_York date** Estos comandos identifican la fecha y hora de ubicaciones alternativas en el mundo.
2. **TZ=America/Los_Angeles date** Estos comandos identifican la fecha y hora de ubicaciones alternativas en el mundo.
3. Para ver las fechas julianas del mes actual se utiliza el comando **cal -j**.
4. Para para mostrar vistas alternativas del calendario se utiliza el comando **cal -m**.
5. Para para mostrar vistas alternativas del calendario **cal -s**.
6. Para ver el ID único e información de los grupos a los que pertenece el usuario específico se utiliza el comando **id ec2-user**.

El resultado de id ec2-user muestra el ID de usuario, el ID de grupo y los grupos de los que forma parte el usuario.

![Ejecutar comandos familiares 2](227-Lab-Linea-de-comandos-de-Linux\4.png)
Figura 4.

### Mejorar el flujo de trabajo mediante el historial y la búsqueda: 
1. **history** Este comando muestra la lista de comando usados. Mostrando que si coinciden con los comandos usados anteriormente.
2. Al presionar **CTRL+R** y escrbir "TZ" y con la flecha hacia arriba aparecera **TZ=America/New_York date**. Este paso traerá un uso antiguo del comando `date` que se puede editar. Usando las teclas de flecha, ahora se puede editar el comando en la misma línea.
3. Al escribir **date** en la terminal y presionar enter.
4. Luego se escribe **!!**, el paso permite volver a ejecutar el comando más reciente..

![Mejorar el flujo de trabajo mediante el historial y la búsqueda](227-Lab-Linea-de-comandos-de-Linux\5.png)
Figura 5.

### Submit: 
1. Cargado a **submit** el laboratorio y entregado.

![Submit](229-Lab-Usuarios-y-grupos\12.png)
Figura 12.

### Finalización del laboratorio: 
1. Con el laboratorio terminado se porcede a finalizar correctamente.

![Finalización del laboratorio](229-Lab-Usuarios-y-grupos\13.png)
Figura 13.
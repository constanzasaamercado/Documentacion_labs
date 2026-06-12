# Laboratorio 227: Linea de comandos de Linux

> **Descripción del Laboratorio:** > En este entorno de laboratorio, el acceso a los servicios de AWS y a sus acciones puede estar restringido a aquellos que necesitas para completar las instrucciones del laboratorio. Es posible que encuentres errores si intentas acceder a otros servicios o realizar acciones más allá de las descritas en este laboratorio.

---

## 🎯 Objetivos

* Ejecutar comandos para obtener información sobre tu sistema actual y la sesión activa.
* Buscar y ejecutar comandos de Bash anteriores.

---

## 🛠️ Desarrollo Paso a Paso

### Inicio laboratorio: 
1. Se da por iniciado el laboratorio al iniciar el conteo.

![Laboratorio Iniciado](227-Lab-Linea-de-comandos-de-Linux\1.png)
Figura 1.

### Terminal Bash inicio: 
1. Se inicia correctamente la sesion en la terminal bash de **PuTTY** con el sistema Linux.

![Terminal Bash inicio](227-Lab-Linea-de-comandos-de-Linux\2.png)
Figura 2.

### Ejecutar comandos familiares 1: 
1. Para mostrar el nombre de usuario actual se utiliza el comando **whoami**.
2. Para mostrar una versión abreviada del nombre de host del equipo se utiliza el comando **hostname -s**.
3. Para mostrar el tiempo que el sistema lleva encendido en un formato de fácil lectura se utiliza el comando **uptime -p**.
4. Para mostrar información detallada sobre los usuarios que han iniciado sesión se utiliza el comando **who -H -a**.

Los comandos whoami, hostname y uptime brindan información básica sobre el sistema que estás usando. Esto es útil si necesitas encontrar el usuario, la dirección IP o cuánto tiempo ha estado funcionando el sistema para resolver problemas.

El comando who -H -a muestra información del usuario como el nombre, la línea de conexión, la hora en que ocurrió el evento, el tiempo de inactividad, el Identificador de Proceso (PID), comentarios y la hora de salida.

![Ejecutar comandos familiares 1](227-Lab-Linea-de-comandos-de-Linux\3.png)
Figura 3.

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

![Submit](227-Lab-Linea-de-comandos-de-Linux\6.png)
Figura 6.

### Finalización del laboratorio: 
1. Con el laboratorio terminado se porcede a finalizar correctamente.

![Finalización del laboratorio](227-Lab-Linea-de-comandos-de-Linux\7.png)
Figura 7.

## 💡 Conclusión y Comentarios Personales

La realización de este laboratorio permitió adquirir competencias esenciales en la administración de sistemas Linux a través de la línea de comandos de Bash. El uso de comandos de diagnóstico como `whoami`, `hostname -s`, `uptime -p`, `who -H -a` e `id ec2-user` demostró ser fundamental para la auditoría y el reconocimiento inicial de cualquier servidor. Estas herramientas proporcionan información crítica sobre la identidad del usuario activo, los privilegios de grupo, los tiempos de actividad de la máquina y los detalles de las sesiones concurrentes, elementos indispensables para resolver problemas en entornos de producción[cite: 4].

Por otro lado, la práctica validó que dominar el historial de la terminal es clave para optimizar el flujo de trabajo diario. Herramientas de automatización nativas como el comando `history`, la búsqueda inversa con `CTRL+R` y el atajo de repetición inmediata `!!` comprueban que un administrador de sistemas puede reutilizar y editar instrucciones complejas previas de manera ágil[cite: 4]. Esta capacidad disminuye los tiempos de ejecución y reduce drásticamente los errores de digitación en la consola, logrando una gestión de TI mucho más eficiente y profesional.
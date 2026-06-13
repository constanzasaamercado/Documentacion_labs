# Laboratorio 231: Edición de archivos

> **Descripción del Laboratorio:** > Esta práctica de laboratorio se enfoca en el uso y configuración de los editores de texto nativos de Linux, Vim y Nano, en un servidor Amazon EC2. El ejercicio comprende el aprendizaje de la navegación y comandos modales mediante **vimtutor**, la creación de archivos de texto (*helloworld* y *cloudworld*) y la correcta gestión de atajos de teclado para insertar datos, guardar cambios y cerrar sesiones de edición de forma segura en la consola de comandos.

---

## 🎯 Objetivos

* Utilizar el ejecutable vimtutor para realizar las tareas 1 a 4.
* Copiar contenido del archivo /var/log/secure y editarlo con nano.
  
---

## 🛠️ Desarrollo Paso a Paso

### Inicio laboratorio: 
1. Se da por iniciado el laboratorio al iniciar el conteo.

![Laboratorio Iniciado](231-Lab-Edicion-de-archivos\1.png)
Figura 1.

### Terminal Bash inicio: 
1. Se inicia correctamente la sesion en la terminal bash de **PuTTY** con el sistema Linux.

![Terminal Bash inicio](231-Lab-Edicion-de-archivos\2.png)
Figura 2.

### Ejercicio - Ejecutar el tutorial de Vim 1: 
1. **vimtutor** Este comando consiste en tutoriales que enseñan al usuario cómo utilizar Vim.

![Ejercicio - Ejecutar el tutorial de Vim 1](231-Lab-Edicion-de-archivos\3.png)
Figura 3.

### Ejercicio - Ejecutar el tutorial de Vim 2: 
1. **vimtutor** Este indica por ejemplo como moverse dentro del programa con las flechas del teclado, entre otros detalles, se prueba dentro de este mismo manual esas indicaciones. **:q!** con este comando se cierra el tutorial.

![Ejercicio - Ejecutar el tutorial de Vim 2](231-Lab-Edicion-de-archivos\4.png)
Figura 4.

### Ejercicio - Editar un archivo en Vim 1: 
1. Ahora estando dentro del archivo creado llamado "helloworld", utiliza Vim para insertar unas pocas líneas de texto.
2. Presionando la tecla i para activar el modo de inserción (insert mode) e introducir el texto. Una vez terminado, se presiona la tecla ESC para salir del modo de inserción, se guardan los cambios del archivo y cierra el editor introduciendo el comando **:wq** seguido de Enter.


![Ejercicio - Editar un archivo en Vim 1](231-Lab-Edicion-de-archivos\5.png)
Figura 5.

### Ejercicio - Editar un archivo en Vim 2: 
1. **vim helloworld** Con este comando se uso Vim para crear un archivo llamado helloworld, y este archivo se abrio al presionar Enter.

![Ejercicio - Editar un archivo en Vim 2](231-Lab-Edicion-de-archivos\6.png)
Figura 6.

### Ejercicio - Editar un archivo en Vim 3: 
1. Agrega la siguiente línea en el editor con **I**, esc y luego **:wq**. Se inserta nuevo texto al archivo.


![Ejercicio - Editar un archivo en Vim 3](231-Lab-Edicion-de-archivos\7.png)
Figura 7.

### Ejercicio - Editar un archivo en nano 1: 
1. Este es un programa editor de línea de comandos alternativo llamado nano. Utiliza nano para crear y editar un archivo de texto, a diferencia de Vim, no se tiene que ingresar a un modo de inserción. En su lugar, se puede empezar a escribir directamente. Para guardar los cambios en el archivo, se presiona la combinación CTRL + O. Presionar Enter para confirmar el nombre del archivo una vez que se guarde. Se presiona CTRL + X para salir del editor nano.
2. Tiene las opciones para edición en pantalla que hace que sea mas facil de utilizar.

![Ejercicio - Editar un archivo en nano 1](231-Lab-Edicion-de-archivos\8.png)
Figura 8.

### Ejercicio - Editar un archivo en nano 2: 
1. Con el comando **nano cloudworld**, se creo un archivo y con enter se abrio para editar.

![Iniciar sesión usando los nuevos usuarios 2](231-Lab-Edicion-de-archivos\9.png)
Figura 9.

### Submit y Finalización del laboratorio: 
1. Cargado a **submit** al entorno y entregado, con el laboratorio terminado se procede a finalizar correctamente.

![Submit](231-Lab-Edicion-de-archivos\10.png)
Figura 10.

## 💡 Conclusión y Comentarios Personales

La realización de este laboratorio permitió adquirir destrezas fundamentales en la manipulación y edición de archivos de configuración y texto directamente desde la interfaz de línea de comandos de Linux[cite: 6]. A través de la interacción con el tutorial interactivo **vimtutor**, se comprendió la lógica operativa de **Vim**, un editor altamente eficiente pero exigente que se basa en el intercambio estricto de entornos de trabajo; la práctica consolidó el uso del modo de inserción mediante la tecla **i** para agregar contenido al archivo *helloworld*, y el dominio de los comandos en modo de comandos como **:wq** para guardar y salir de forma segura, o **:q!** para abortar ediciones[cite: 6].

Por otra parte, la experiencia con el editor **Nano** para la creación del archivo *cloudworld* ofreció un contraste técnico valioso[cite: 6]. Al permitir la escritura directa sin modos previos y contar con un menú de opciones visible en pantalla (como **CTRL + O** para guardar y **CTRL + X** para salir), Nano demostró ser una alternativa mucho más accesible e intuitiva para intervenciones rápidas[cite: 6]. En conclusión, dominar herramientas de edición tanto modales como directas le otorga al administrador de sistemas la flexibilidad necesaria para gestionar scripts, modificar registros de seguridad y configurar servicios en entornos de servidores donde no se dispone de una interfaz gráfica de usuario.
# Laboratorio 253: Desafío Scripting del Shell Bash

> **Descripción del Laboratorio:** > Este laboratorio de desafío tiene como objetivo poner a prueba tus habilidades avanzadas de automatización en Linux mediante el diseño y desarrollo de un script de shell en Bash en una instancia de Amazon EC2.
---

## 🎯 Objetivos

* Crear un directorio.

---

## 🛠️ Desarrollo Paso a Paso

### Inicio laboratorio: 
1. Se da por iniciado el laboratorio al iniciar el conteo. 


![Laboratorio Iniciado](253-Lab-[Desafío]-Scripting-del-shell-Bash\1.png)
Figura 1.

### Credenciales: 
1. Se descarga el archivo **PPK**.
2. Se copia el **IPPublico**.

![Credenciales](253-Lab-[Desafío]-Scripting-del-shell-Bash\2.png)
Figura 2.

### Creación de archivo: 
1. Se inicia correctamente la sesion en la terminal bash de **PuTTY** con el sistema Linux. **pwd** Valida que se encuentre en la carpeta de inicio (home) del usuario actual escribiendo. Se crea el archivo con el comando **nano crear_archivos.sh**.
   
![Creación de archivo](253-Lab-[Desafío]-Scripting-del-shell-Bash\3.png)
Figura 3.

### Edición del código: 
1.  La primera linea **#!/bin/bash** es la secuencia que identifica que es un ejecutable de script. Se define el nombre con el *PREFIJO=*.
2.  Se agrega codigo para buscar el último número que ya existe en la carpeta.
3.  Se define con *ULTIMO_NUM* que si la carpeta está vacía, se empieza desde el 0 y si ya existen, se empieza en el numero siguiente. Se crean carpetas hasta llegar a la cantidad de 25.
4.  Mensaje para indicar que se estan creando los archivos.
5.  Con este bucle se crean los 25 archivos vacíos usando **touch**.
6.  Mensaje de confirmación.

![Edición del código](253-Lab-[Desafío]-Scripting-del-shell-Bash\4.png)
Figura 4.

### Permisos y ejecución del archivo: 
1.  Se utiliza **chmod +x crear_archivos.sh** para darle el permiso de ejecución al script.
2.  Se ejecuta por primera vez**./crear_archivos.sh** para dar inicio a la creación del directorio con mi nombre y el número de archivo. Indica que se crearon 25 archivos, ya que no existian otros antes. Se ejecuta por segunda vez para comprobar la automatización. 
   **"ls -l ConstanzaSaa*"** Para buscar en especifico las carpetas creadas con mi nombre. Corroborandose exitosamente.

![Permiso y ejecución del archivo](253-Lab-[Desafío]-Scripting-del-shell-Bash\5.png)
Figura 5.

### Submit: 
1. Cargado a **submit** el laboratorio y entregado.

![Submit](253-Lab-[Desafío]-Scripting-del-shell-Bash\6.png)
Figura 6.

### Finalización del laboratorio: 
1. Con el laboratorio terminado se procede a finalizar correctamente.

![Finalización del laboratorio](253-Lab-[Desafío]-Scripting-del-shell-Bash\7.png)
Figura 7.

## 💡 Conclusión y Comentarios Personales

La realización de este laboratorio permitió adquirir competencias críticas en la automatización avanzada y la programación de lógica de scripts dentro de entornos Linux hospedados en Amazon EC2. El uso de comandos como **nano crear_archivos.sh** junto con la definición analítica de variables como *PREFIJO* y *ULTIMO_NUM* demostró ser fundamental para mitigar riesgos operacionales y evitar valores fijos (hardcoding) al evaluar dinámicamente el estado del directorio; por otra parte, la incorporación de un bucle condicional iterativo sirvió como un valioso caso de estudio sobre el despliegue ordenado de elementos y la creación secuencial masiva de archivos vacíos mediante la instrucción **touch**. Validar finalmente la correcta ejecución incremental de las tandas tras otorgar permisos con **chmod +x** y confirmar los resultados específicos mediante **"ls -l ConstanzaSaa*"** ratifica que el éxito en la administración moderna de TI depende tanto de garantizar la flexibilidad y escalabilidad de los scripts locales como de asegurar una automatización precisa para la gobernanza eficiente de recursos en tiempo real.
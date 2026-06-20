# Laboratorio 247: Trabajo con comandos

> **Descripción del Laboratorio:** > Este laboratorio práctico tiene como objetivo enseñar el uso y la combinación de comandos fundamentales en la terminal de Linux para la manipulación y procesamiento de texto en un entorno hospedado en Amazon EC2.

---

## 🎯 Objetivos

* Utilizar el comando tee para dirigir la salida a un archivo.
* Utilizar el comando sort para reorganizar el contenido de un archivo .csv.
* Utilizar el comando cut para editar el contenido de un archivo.
* Utilizar el comando sed.
* Utilizar el operador de tubería (pipe).

---

## 🛠️ Desarrollo Paso a Paso

### Inicio laboratorio: 
1. Se da por iniciado el laboratorio al iniciar el conteo. 


![Laboratorio Iniciado](247-Lab-Trabajo-con-comandos\1.png)
Figura 1.

### Credenciales: 
1. Se descargar el archivo **PPK**.
2. Se copia el **IPPublico**.

![Credenciales](247-Lab-Trabajo-con-comandos\2.png)
Figura 2.

### Usar el comando tee: 
1. Se inicia correctamente la sesion en la terminal bash de **PuTTY** con el sistema Linux. **pwd** Valida que se encuentre en la carpeta de inicio (home) del usuario actual escribiendo. **hostname | tee file1.txt** este comando se utiliza para crear el archivo, se comprueba la creación con **ls**.
   
![Usar el comando tee](247-Lab-Trabajo-con-comandos\3.png)
Figura 3.

### Usar el comando sort y el operador de tubería (pipe): 
1.  Se digita el comando **cat > test.csv** para agregar texto al archivo y luego *enter*. Se agrega el texto de cada linea. Para guardar y salir apretar *CTRL+D*. Se confirma la correcta creación con **ls**.
2.  Use el comando **sort test.csv** para reordenar la lista, de forma alfabética.
3.  **find | grep Paris test.csv** busca y enumera el contenido del archivo y redirige los resultados al comando grep, donde este busca el patrón "Paris".

![Usar el comando sort y el operador de tubería (pipe)](247-Lab-Trabajo-con-comandos\4.png)
Figura 4.

### Usar el comando cut: 
1. Se digita el comando **cat > cities.csv** para agregar texto al archivo y luego *enter*. Se agrega el texto de cada linea. Para guardar y salir apretar *CTRL+D*. Se confirma la correcta creación con **ls**.
2. **cut -d ',' -f 1 cities.csv** para cortar secciones de líneas de texto por caracteres. Se utiliza la opción **-d** (delimitador), la opción de la coma **","** y la opción **-f** (campo / field). El comando combinado junto con sus opciones extraerá el primer campo de cada registro.
3. **sed 's/,/./' cities.csv test.csv** se utiliza el comando **sed** para reemplazar la primera coma **","** por un punto **"."** en ambos archivos. En el primer ingreso del comando falto un slash por lo que no resulto, pero al segundo intento si.

![Usar el comando cut](247-Lab-Trabajo-con-comandos\5.png)
Figura 5.

### Submit: 
1. Cargado a **submit** el laboratorio y entregado.

![Submit](247-Lab-Trabajo-con-comandos\6.png)
Figura 6.

### Finalización del laboratorio: 
1. Con el laboratorio terminado se procede a finalizar correctamente.

![Finalización del laboratorio](247-Lab-Trabajo-con-comandos\7.png)
Figura 7.

## 💡 Conclusión y Comentarios Personales

La realización de este laboratorio permitió adquirir competencias críticas en la manipulación de flujos de datos y el procesamiento avanzado de texto mediante la consola de Linux en entornos de nube. El uso integrado del operador de tubería *pipe* junto con comandos como **hostname | tee file1.txt** demostró la utilidad de capturar y duplicar salidas estándar en tiempo real hacia archivos físicos, optimizando la trazabilidad del sistema; por otra parte, la estructuración y filtrado de datos mediante **sort** y **cut -d ',' -f 1** evidenció cómo segmentar información estructurada de manera eficiente basándose en delimitadores específicos. Asimismo, la resolución de la sustitución de caracteres con el editor de flujo mediante **sed 's/,/./'** sirvió como un valioso caso de estudio sobre la importancia de la precisión sintáctica en la automatización de scripts, donde la omisión de un solo carácter puede alterar el resultado esperado. Validar finalmente la transformación masiva de registros en múltiples archivos CSV ratifica que la eficiencia en la administración moderna de TI y la gestión de infraestructuras cloud depende directamente del dominio de herramientas de filtrado nativas para la gobernanza y análisis ágil de datos.
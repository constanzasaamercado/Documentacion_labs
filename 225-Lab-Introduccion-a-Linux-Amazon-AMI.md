# Laboratorio 225: Introducción a Linux Amazon AMI

> **Descripción del Laboratorio:** > En esta práctica de laboratorio, se utilizara Secure Shell (SSH) para acceder a una Amazon Machine Image **AMI** de Amazon Linux dentro de los laboratorios de Vocareum. A continuación, se utilizara el comando man para acceder a las páginas de manual **man pages**.

---

## 🎯 Objetivos

* Utilizar SSH para acceder a una AMI de Amazon Linux dentro de los laboratorios de Vocareum.
* Comprender el propósito del comando man.
* Demostrar el uso de la función de búsqueda en las páginas de man.
* Examinar los encabezados de las páginas de man.

---

## 🛠️ Desarrollo Paso a Paso

### Inicio laboratorio: 
1. Se da por iniciado el laboratorio al iniciar el conteo.

![Laboratorio Iniciado](225-Lab-Introduccion-a-Linux-Amazon-AMI\1.png)
Figura 1.

### Credenciales: 
1. Se descargar el archivo **PPK**.
2. Se copia el **IPPublico**.

![Credenciales](225-Lab-Introduccion-a-Linux-Amazon-AMI\2.png)
Figura 2.

### Configuración PuTTY 1: 
1. Se pega el **IPPublico** en el **HostName**, asegurandose que **Port** sea "22".
2. Se selecciona **Connection**, luego **SSHH** y despues **Auth**, por ultimo **Credentials**.

![Configuración PuTTY 1](225-Lab-Introduccion-a-Linux-Amazon-AMI\3.png)
Figura 3.

### Configuración PuTTY 2: 
1. Se carga en **Private key file for authentication** el archivo **labsuser.ppk**.
2. Sellecionar **open** para abrir la consola.

![Configuración PuTTY 2](225-Lab-Introduccion-a-Linux-Amazon-AMI\4.png)
Figura 4.

### Error en usuario: 
1. Solicita un usuario debido a que en el paso **Configuración PuTTY 1** no se coloco correctamente el nombre de host, se procede a modificar colocando **ec2-user@< IPPublica >**.

![Error en usuario](225-Lab-Introduccion-a-Linux-Amazon-AMI\5.png)
Figura 5.

### Terminal Bash inicio: 
1. Se inicia correctamente la sesion en la terminal bash de **PuTTY** con el sistema Linux.

![Terminal Bash inicio](225-Lab-Introduccion-a-Linux-Amazon-AMI\6.png)
Figura 6.

### Manual del programa **man**: 
1. En la terminal se digita el comando **man** que procede a abrir el manual de uso del programa.
2. Descripción del manual.

Los siguientes son algunos de los encabezados más importantes de las páginas del manual:
* NAME (Nombre)
* SYNOPSIS (Sinopsis / Sintaxis)
* DESCRIPTION (Descripción)
* OVERVIEW (Resumen / Visión general)
* EXAMPLES (Ejemplos)
* FILES (Archivos)
* OPTIONS (Opciones)

![Manual del programa **man**](225-Lab-Introduccion-a-Linux-Amazon-AMI\7.png)
Figura 7.

### Block de notas con **man**: 
1. Se pega en un block de notas el manual.

![Block de notas con **man**](225-Lab-Introduccion-a-Linux-Amazon-AMI\8.png)
Figura 8.

### Submit: 
1. Cargado a **submit** el laboratorio y entregado.

![Submit](225-Lab-Introduccion-a-Linux-Amazon-AMI\9.png)
Figura 9.

### Finalización del laboratorio: 
1. Con el laboratorio terminado se procede a finalizar correctamente.

![Finalización del laboratorio](225-Lab-Introduccion-a-Linux-Amazon-AMI\10.png)
Figura 10.

## 💡 Conclusión y Comentarios Personales

La ejecución de este laboratorio permitió asimilar los fundamentos de la administración remota de servidores basados en Linux utilizando la herramienta **PuTTY**. Un aspecto clave del desarrollo fue la identificación y resolución del error de autenticación: la práctica demostró que no basta con ingresar la dirección IP pública y la clave privada **.ppk**, sino que es mandatorio declarar explícitamente el usuario correcto de la AMI **ec2-user@< IPPublica >** para que el protocolo **SSH** pueda validar y abrir la terminal Bash con éxito.

Por otra parte, el laboratorio sirvió para comprender el valor práctico del comando **man** dentro de los sistemas operativos UNIX/Linux. Experimentar directamente con las páginas de manual evidenció que la documentación nativa es la herramienta más eficiente para que un administrador de sistemas aprenda a operar comandos, comprender su sintaxis y navegar por sus opciones sin depender de recursos externos. Guardar y analizar esta información consolidó las habilidades necesarias para interactuar de forma segura y autónoma con servidores en la nube.
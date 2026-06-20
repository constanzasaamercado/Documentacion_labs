# Laboratorio 245: Administración de archivos de registro

> **Descripción del Laboratorio:** > Este laboratorio práctico tiene como objetivo enseñar la administración y revisión de archivos de registro (log files) en un entorno Linux hospedado en Amazon EC2.

---

## 🎯 Objetivos

* Revisar las salidas de los registros lastlog y secure de la máquina Linux

---

## 🛠️ Desarrollo Paso a Paso

### Inicio laboratorio: 
1. Se da por iniciado el laboratorio al iniciar el conteo. 


![Laboratorio Iniciado](245-Lab-Administración-de-archivos-de-registro\1.png)
Figura 1.

### Credenciales: 
1. Se descargar el archivo **PPK**.
2. Se copia el **IPPublico**.

![Credenciales](245-Lab-Administración-de-archivos-de-registro\2.png)
Figura 2.

### Revisar los archivos de registro de seguridad (Secure Logs) 1: 
1. Se inicia correctamente la sesion en la terminal bash de **PuTTY** con el sistema Linux. **pwd** Valida que se encuentre en la carpeta de inicio (home) del usuario actual escribiendo. **cd companyA** se ingresa a la terminal para trabajar en ese directorio. 
   Se utiliza este comando **sudo less /tmp/log/secure** para usar el archivo de registro seguro como prueba, se muestra la lista de errores y fallos que incluyen la información de desde dónde se intentaba acceder al usuario, si falló la autenticación y por qué puerto.
   
![Revisar los archivos de registro de seguridad (Secure Logs) 1](245-Lab-Administración-de-archivos-de-registro\3.png)
Figura 3.

### Revisar los archivos de registro de seguridad (Secure Logs) 2: 
1.  Para ver las horas del último inicio de sesión de todos los usuarios en la máquina, se utiliza el comando **sudo lastlog**.

![Revisar los archivos de registro de seguridad (Secure Logs) 2](245-Lab-Administración-de-archivos-de-registro\4.png)
Figura 4.

### Submit: 
1. Cargado a **submit** el laboratorio y entregado.

![Submit](245-Lab-Administración-de-archivos-de-registro\5.png)
Figura 5.

### Finalización del laboratorio: 
1. Con el laboratorio terminado se procede a finalizar correctamente.

![Finalización del laboratorio](245-Lab-Administración-de-archivos-de-registro\6.png)
Figura 6.

## 💡 Conclusión y Comentarios Personales

La realización de este laboratorio permitió adquirir competencias críticas en la auditoría y monitoreo de seguridad de sistemas operativos mediante el análisis de archivos de registro *log files* en entornos Linux. El uso del comando **sudo less /tmp/log/secure** demostró ser una herramienta fundamental para identificar de manera proactiva fallos de autenticación, permitiendo rastrear variables clave como la dirección IP de origen y los puertos utilizados ante posibles intentos de acceso no autorizados. Por otra parte, la ejecución de sudo lastlog aportó una perspectiva integral para el control de identidades al desplegar el historial exacto y las horas del último inicio de sesión de todos los usuarios de la máquina. Validar e interpretar correctamente estas salidas en un entorno en la nube de Amazon EC2 ratifica que una gobernanza e infraestructura TI robusta depende directamente de la capacidad técnica para auditar registros locales, mitigar riesgos operacionales y garantizar la trazabilidad de accesos en tiempo real.
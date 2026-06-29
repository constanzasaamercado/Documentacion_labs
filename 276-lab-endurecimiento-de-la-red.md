# Laboratorio 276: Endurecimiento de la red

> **Descripción del Laboratorio:** > Este laboratorio práctico se enfoca en la activación y configuración de Amazon Inspector para realizar auditorías automatizadas de seguridad y análisis continuo de vulnerabilidades en arquitecturas serverless, específicamente sobre funciones de AWS Lambda.

## 🎯 Objetivos

* Activar Amazon Inspector.
* Analizar e interpretar los hallazgos de vulnerabilidades.
* Remediar las vulnerabilidades encontradas por Amazon Inspector.

---
## Contexto del caso

Los desarrolladores de AnyCompany se encuentran en las fases iniciales de construcción de una aplicación utilizando principalmente AWS Lambda. A lo largo del proceso de desarrollo, necesitan una herramienta de seguridad automatizada que no solo escanee paquetes de software vulnerables, sino que también realice escaneos dentro del propio código. Has decidido utilizar Amazon Inspector para cubrir esta necesidad.

Amazon Inspector cumple con los requisitos de poder escanear funciones de AWS Lambda respondiendo rápidamente a los nuevos despliegues. También escanea de forma automática recursos adicionales, tales como instancias EC2 y repositorios de Amazon ECR dentro de la cuenta de AWS de AnyCompany.

---

## 🛠️ Desarrollo Paso a Paso

### Inicio laboratorio: 
1. Se da por iniciado el laboratorio al iniciar el conteo. 


![Laboratorio Iniciado](276-Lab-Endurecimiento-de-la-red\1.png)
Figura 1.


### Activar Amazon Inspector 1: 
1. Se procede a activar amazon inspector.
   
![Activar Amazon Inspector 1](276-Lab-Endurecimiento-de-la-red\2.png)
Figura 2.

### Activar Amazon Inspector 2: 
1. La imagen muestra que lambda esta al 100%, lo que significa que ya se analizaron las funciones.

![Activar Amazon Inspector 2](276-Lab-Endurecimiento-de-la-red\3.png)
Figura 3.

### Revisar y analizar las vulnerabilidades 1: 
1. En la lista de hallazgos se encuentra uno de severidad Medium de nombre *CVE-2023-32681*.
2. En el detalle de este hallazgo se encuentra un get request, enlace externo. Se muestra en la figura 5, la base de datos de NIST para mayor documentación.

![Revisar y analizar las vulnerabilidades 1](276-Lab-Endurecimiento-de-la-red\4.png)
Figura 4.
![Revisar y analizar las vulnerabilidades 1.1](276-Lab-Endurecimiento-de-la-red\5.png)
Figura 5.

### Revisar y analizar las vulnerabilidades 2: 
1.  En la sección de corrección indica que es lo que se debe hacer para solucionar el hallazgo. En este caso indica que el paquete *requests* esta desactualizado, por lo que, hay que actulaizarlo.


![Revisar y analizar las vulnerabilidades 2](276-Lab-Endurecimiento-de-la-red\6.png)
Figura 6.


### Remediar la vulnerabilidad en Lambda 1: 
1.  En la sección funciones del servicio Lambda, en la lista indica la función *get-request*.

![Remediar la vulnerabilidad en Lambda 1](276-Lab-Endurecimiento-de-la-red\7.png)
Figura 7.

### Remediar la vulnerabilidad en Lambda 2: 
1. Una vez dentro de la configuración de la función, en la pestaña de código (Code), se busca el navegador de archivos de la izquierda y se selecciona *requirements.txt*. En el archivo se vera la línea requests==2.20.0. Se procede a borrar los signos de igual y el número de versión, dejando únicamente la palabra: *requests*, para que AWS Lambda instale automáticamente hasta la ultima versión segura en el próximo despliegue. 
   Luego se selecciona el boton **Deploy** para guardar y aplicar los cambios.

![Remediar la vulnerabilidad en Lambda 2](276-Lab-Endurecimiento-de-la-red\8.png)
Figura 8.

### Confirmar la solución en Amazon Inspector: 
1.  En el Amazon Inspector > Hallazgos, se cambia el filtro de status a *closed*, confirmando que el hallazgo se encuentra cerrado y solucionado.
   En la figura 10, se puede observar que para verificarlo a nivel de infraestructura en las funciones de Lambda se actualizó con la hora del despliegue.

![Confirmar la solución en Amazon Inspector 1](276-Lab-Endurecimiento-de-la-red\9.png)
Figura 9.
![Confirmar la solución en Amazon Inspector 1.1](276-Lab-Endurecimiento-de-la-red\10.png)
Figura 10.

### Submit: 
1. Cargado a **submit** el laboratorio y entregado. 

![Submit](276-Lab-Endurecimiento-de-la-red\11.png)
Figura 11.

### Finalización del laboratorio: 
1. Con el laboratorio terminado se procede a finalizar correctamente.

![Finalización del laboratorio](276-Lab-Endurecimiento-de-la-red\12.png)
Figura 12.

### Respuesta Técnica para el cliente:

La auditoría de seguridad y el análisis continuo de vulnerabilidades en la infraestructura serverless de la aplicación se han completado de manera exitosa. Mediante la integración estratégica de Amazon Inspector, se realizó un escaneo automatizado sobre las funciones de AWS Lambda que permitió detectar dependencias de software obsoletas y mitigar proactivamente posibles vectores de ataque. Tras identificar un hallazgo de severidad media asociado a una versión vulnerable del paquete requests (CVE-2023-32681), se ejecutó la correspondiente acción de remediación mediante la actualización del archivo de dependencias requirements.txt en la función get-request, forzando el despliegue de los parches de seguridad más recientes. Amazon Inspector ha verificado la correcta aplicación de la solución, determinando que los componentes evaluados cumplen plenamente con los estándares de protección y se encuentran operando en un entorno íntegro y seguro.
# Laboratorio 277: Endurecimiento de sistemas

> **Descripción del Laboratorio:** > Este laboratorio práctico aborda el endurecimiento y fortalecimiento de sistemas (systems hardening) mediante la gestión automatizada de parches utilizando AWS Systems Manager Patch Manager.

## 🎯 Objetivos

* Aplicar parches en instancias Linux utilizando la línea base por defecto.
* Crear una línea base de parches personalizada.
* Utilizar grupos de parches (patch groups) para aplicar parches en instancias Windows mediante una línea base personalizada.
* Verificar el cumplimiento de parches (patch compliance).

---
## Contexto del caso

En organizaciones con cientos y, a menudo, miles de estaciones de trabajo, puede resultar un desafío logístico mantener actualizados todos los sistemas operativos (SO) y el software de las aplicaciones. En la mayoría de los casos, las actualizaciones del SO en las estaciones de trabajo se pueden aplicar automáticamente a través de la red. Sin embargo, los administradores deben contar con una política de seguridad clara y un plan de línea base (baseline) para garantizar que todas las estaciones de trabajo ejecuten una versión mínima específica de software.

---

## 🛠️ Desarrollo Paso a Paso

### Inicio laboratorio: 
1. Se da por iniciado el laboratorio al iniciar el conteo. 


![Laboratorio Iniciado](277-Lab-endurecimiento-de-sistemas\1.png)
Figura 1.


### Parchear las instancias Linux con la línea base por defecto 1: 
1. Se ingresa a Fleet Manager desde Node Management. Se pueden identificar las 6 instancias preconfiguradas (3 Linux y 3 Windows).
   
![Parchear las instancias Linux con la línea base por defecto 1](277-Lab-endurecimiento-de-sistemas\2.png)
Figura 2.

### Parchear las instancias Linux con la línea base por defecto 2: 
1. En esta pagina se puede ver en detalle una de las instancias que corresponde a la de "Linux 1".

![Parchear las instancias Linux con la línea base por defecto 2](277-Lab-endurecimiento-de-sistemas\3.png)
Figura 3.

### Parchear las instancias Linux con la línea base por defecto 3: 
1. Se ingresa a Patch Manager desde Node Management. Luego aplicar parches ahora. Se selecciona la configuración; Patching operation: Scan and install, Reboot option: Reboot if needed, Instances to patch: Patch only the target instances I specify, Target selection: Selecciona Specify instance tags.

![Parchear las instancias Linux con la línea base por defecto 3](277-Lab-endurecimiento-de-sistemas\4.png)
Figura 4.

### Parchear las instancias Linux con la línea base por defecto 4: 
1. Se definen; Tag key: Patch Group y Tag value: LinuxProd, luego Add y aplicar parches ahora.


![Parchear las instancias Linux con la línea base por defecto 4](277-Lab-endurecimiento-de-sistemas\5.png)
Figura 5.

### Ejecución parches instancias Linux: 
1.  Se confirma que los parches se han aplicado correctamente a las instancias Linux, indicando que son 3.


![Ejecución parches instancias Linux](277-Lab-endurecimiento-de-sistemas\6.png)
Figura 6.


### Crear una línea base de parches personalizada para Windows 1: 
1.  Se ingresa a Patch baselines desde Systems Manager > Patch Manager. Luego Create patch baseline. Se selecciona la configuración; Name: WindowsServerSecurityUpdates, Description: Windows security baseline patch, Operating system: Windows.

![Crear una línea base de parches personalizada para Windows 1](277-Lab-endurecimiento-de-sistemas\7.png)
Figura 7.

### Agregar primera regla a la base personalizada: 
1. En la sección Approval rules for operating systems, se configura la primera regla; Products: WindowsServer2019, desmarcar All, Severity: Critical, Classification: SecurityUpdates, Auto-approval: 3 days, Compliance reporting: Critical. Luego agregar regla.
   
![Agregar primera regla a la base personalizada](277-Lab-endurecimiento-de-sistemas\8.png)
Figura 8.

### Agregar segunda regla a la base personalizada: 
1.  En la sección Approval rules for operating systems, se configura la primera regla; Products: WindowsServer2019, desmarcar All, Severity: Important, Classification: SecurityUpdates, Auto-approval: 3 days, Compliance reporting: High. Luego agregar regla.

![Agregar segunda regla a la base personalizada](277-Lab-endurecimiento-de-sistemas\9.png)
Figura 9.

### Confirmación de creación línea base de parches personalizada para Windows: 
1. Se crea la línea base de parches personalizada para windows en las 3 instancias.

![Confirmación de creación línea base de parches personalizada para Windows](277-Lab-endurecimiento-de-sistemas\10.png)
Figura 10.

### Modificación de grupos  de parche: 
1. Despues de seleccionar el cuadro de la linea base creada de la lista, se despliega el menú Actions y luego Modify patch groups. Se digita en el cuadro de texto *WindowsProd*, al final agregar y cerrar.

![Modificación de grupos  de parche](277-Lab-endurecimiento-de-sistemas\11.png)
Figura 11.

### Etiquetar y parchear las instancias Windows: 
1. Se ingresa a Manage tags desde EC2 > Instances, se selecciona la instancia **Windows-1**, desde la pestaña Tags. Luego Add new tag, se configura; Key: Patch Group y Value: WindowsProd. al final guardar. Se repite el mismo proceso con todas las instancias de windows restantes.

![Etiquetar y parchear las instancias Windows](277-Lab-endurecimiento-de-sistemas\12.png)
Figura 12.

### Ejecutar el parcheo: 
1. Se regresa a Patch Manager desde Systems Manager, luego aplicar ahora. Se configura de la siguiente forma; Patching operation: Scan and install, Reboot option: Reboot if needed, Instances to patch: Patch only the target instances I specify, Target selection: Specify instance tags, Tag key: Patch Group y Tag value: WindowsProd. Al final agregar y aplicar.

![Ejecutar el parcheo](277-Lab-endurecimiento-de-sistemas\13.png)
Figura 13.

### Confirmación del parcheo: 
1. Se evidencia el resumen del parcheo en curso.

![Confirmación del parcheo](277-Lab-endurecimiento-de-sistemas\14.png)
Figura 14.

### Ejecuciones de parcheo: 
1. Desde Execution ID se llega a la pantalla de State Manager.

![Ejecuciones de parcheo](277-Lab-endurecimiento-de-sistemas\15.png)
Figura 15.

### Panel de salida: 
1. Se selecciona el enlace Output de la instancia de windows que figura In progress, se abre Run Command y se puede ver el progreso interno desplegado en el panel de salida.

![Panel de salida](277-Lab-endurecimiento-de-sistemas\16.png)
Figura 16.

### Verificar el cumplimiento general: 
1. Se regresa a Patch Manager desde Systems Manager, luego la pestaña Dashboard, en la sección Compliance summary se verifica que las 6 instancias se encuentran con sus parches aplicados.

![Verificar el cumplimiento general](277-Lab-endurecimiento-de-sistemas\17.png)
Figura 17.

### Auditar lista de parches: 
1. En Node ID del servidor Windows y en la pestaña Patch, se puede auditar la lista de todos los parches específicos que se instalaron y la fecha exacta de su aplicación.

![Auditar lista de parches](277-Lab-endurecimiento-de-sistemas\18.png)
Figura 18.

### Submit: 
1. Cargado a **submit** el laboratorio y entregado. 

![Submit](277-Lab-endurecimiento-de-sistemas\19.png)
Figura 19.

### Finalización del laboratorio: 
1. Con el laboratorio terminado se procede a finalizar correctamente.

![Finalización del laboratorio](277-Lab-endurecimiento-de-sistemas\20.png)
Figura 20.

### 💡 Conclusión y Comentarios Personales

La realización de este laboratorio permitió adquirir competencias críticas en el fortalecimiento y la administración automatizada de infraestructuras a gran escala mediante el uso de AWS Systems Manager Patch Manager. La implementación de políticas de seguridad basadas en líneas base (patch baselines) demostró ser fundamental para garantizar la integridad operativa de un entorno mixto, facilitando la gestión centralizada tanto en instancias Linux como en Windows Server 2019. La configuración estratégica de grupos de parches (patch groups) y el uso de etiquetas (tags) para la selección dirigida de objetivos evidenciaron la importancia de una gobernanza de TI robusta y escalable; por otra parte, la validación del cumplimiento mediante el monitoreo de ejecuciones en Run Command y el análisis detallado del panel de Compliance reporting sirvieron como un valioso caso de estudio sobre cómo mitigar riesgos de seguridad de forma proactiva. Validar finalmente que las seis instancias alcanzaran un estado de cumplimiento exitoso ratifica que el éxito en la administración moderna de TI depende de combinar la automatización de procesos con una visibilidad constante sobre el estado de salud de los recursos críticos en la nube.
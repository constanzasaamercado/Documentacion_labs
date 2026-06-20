# Laboratorio 11: Introducción a Amazon EC2

> **Descripción del Laboratorio:** > En esta sesión práctica aprendimos a gestionar el ciclo de vida básico de un servidor en la nube, logrando crear, configurar de forma segura, conectar y redimensionar una instancia de Amazon EC2.

---

## 🎯 Objetivos

* Iniciar un servidor web con la protección contra terminación habilitada.
* Monitorear la instancia EC2.
* Modificar el grupo de seguridad que utiliza el servidor web para permitir el acceso HTTP.
* Cambiar el tamaño de la instancia Amazon EC2 para escalar.
* Probar la protección contra terminación de instancias.
* Terminar la instancia EC2.

---

## 🛠️ Desarrollo Paso a Paso

### Inicio laboratorio: 
1. Se da por iniciado el laboratorio al dar luz verde para ingresar al sistema de aws de pruebas.

![Laboratorio Iniciado](11-Introduccion-a-Amazon-EC2\1.png)
Figura 1.


### Lanzamiento de la Instancia EC2:
1. Se nombra la instancia como **Web Server**.
2. Se selecciona el sistema operativo de **Amazon Linux**.

![Lanzar instancia ec2](11-Introduccion-a-Amazon-EC2\2.png)
Figura 2.

### Imagen de la maquina:
1. En este punto se selecciona **AMI de Amazon Linux 2023 kernel-6.1**, que es apta para la capa gratuita, siendo lo apropiado para un entorno de pruebas.
2. Descripcion de **AMI de Amazon Linux 2023 kernel-6.1**.

![AMI](11-Introduccion-a-Amazon-EC2\3.png)
Figura 3.

### Configuración de la instancia:
1. El tipo de instancia para este laborotorio es la **t3.micro**.
2. En esta ocación no se necesitara el par de claves para iniciar la instancia, por lo que se selecciona **continuar sin un par de claves**.

![Configuración instancia](11-Introduccion-a-Amazon-EC2\4.png)
Figura 4.

### Configuración de la red parte 1:
1. Se selecciona el **VPC-0c5c77851e0bb3cc4 (Lab VPC)**.
2. Para el firewall se selecciona **Crear un grupo de seguridad**, para controlar el trafíco de la instancia.
3. Se define el nombre para el grupo de seguridad como;**Web Server security group**.

![Configuración de red 1](11-Introduccion-a-Amazon-EC2\5.png)
Figura 5.

### Configuración de la red parte 2:
1. Es la descripción para el grupo de seguridad del servidor web..
2. No se agregan reglas para el grupo de seguridad.


![Configuración de red 2](11-Introduccion-a-Amazon-EC2\6.png)
Figura 6.

### Configuración del almacenamiento:
1. Para el almacenamiento de la maquina se definen 8 gib.
2. En los detalles avanzados se selecciona en la sección de **Termination protection**, la opción **Enable**.

![Configuración del almacenamiento](11-Introduccion-a-Amazon-EC2\7.png)
Figura 7.

### Datos de usuario:
1. Se escribre en el campo el codigo para el html de la instancia, siendo modificado el original para agregar una imagen de fondo.
2. Resumen de la instancia que indica la AMI, el tipo de servidor virtual, el firewall y el almacenamiento.
3. Se selecciona lanza instancia para continuar.

![datos de usuario](11-Introduccion-a-Amazon-EC2\8.png)
Figura 8.

### Estado de instancia:
1. Se inicia correctamente el lanzamiento de la instancia.
2. Se procede a ver todas las instancias.

![Estado de instancia](11-Introduccion-a-Amazon-EC2\9.png)
Figura 9.

### Datos de instancia:
1. Se identifican los datos de la instancia y se copia el ip publico para cargar el html de la instancia.

![datos de instancia](11-Introduccion-a-Amazon-EC2\10.png)
Figura 10.

### Prueba 1 Html:
1. Debido a que la instancia no estaba configurada para ingresar al html por HTTP no se pudo acceder al sitio.


![Prueba 1](11-Introduccion-a-Amazon-EC2\11.png)
Figura 11.

### Reglas de entrada:
1. Se edita la regla de entrada del grupo de seguridad para que cargue el sitio, se selecciona tipo **HTTP**.
2. Se guarda la edición de la regla de entrada.

![Regla de entrada](11-Introduccion-a-Amazon-EC2\12.png)
Figura 12.

### Regla de entrada actualizada:
1. Se Modifico correctamente la regla de entrada a **HTTP**.
2. Se ve que ya esta realizada la modificació a **HTTP**.

![Regla de entrada actualizada](11-Introduccion-a-Amazon-EC2\13.png)
Figura 13.

### Sitio web de la instancia:
1. Carga con exito el sitio de la instancia personalizado.

![Sitio web de la instancia](11-Introduccion-a-Amazon-EC2\14.png)
Figura 14.

### Modificación de estado:
1. Para realizar cambios en la configuración de la isntancoia se debe cambiar el estado a **Detener instancia**.

![Modificación de estado](11-Introduccion-a-Amazon-EC2\15.png)
Figura 15.

### Modificación de estado correcto:
1. Se inicia corretamente la detención de la instancia.
2. Estado actualizado a **deteniendose**.

![Modificación de estado correcto](11-Introduccion-a-Amazon-EC2\16.png)
Figura 16.

### Cambio tipo de instancia 1:
1. Se selecciona **Acciones**, seguido de **Configuración de instancias**.
2. Luego como se indica en la imagen, se selecciona **Cambiar tipo de instancia**.

![Cambio tipo de instancia 1](11-Introduccion-a-Amazon-EC2\17.png)
Figura 17.

### Cambio tipo de instancia 2:
1. Se selecciona el nuevo tipo de instancia **t3.small**.
2. Detalle de la comparación del tipo de instancia nuevo y el anterior, muestra un aumento no significativo del valor usd por hora, pero en memoria aumenta la cantidad de 1024 mb.


![Cambio tipo de instancia 2](11-Introduccion-a-Amazon-EC2\18.png)
Figura 18.

### Tipo de instancia actualizada:
1. Se modifico correctamente el tipo de instancia de **t3.micro** a **t3.small**.
2. Muestra el tipo actualizado para la instancia.
3. Para el siguiente paso se selecciona **volumenes** de la barra lateral del EBS.

![Tipo de instancia actualizada](11-Introduccion-a-Amazon-EC2\19.png)
Figura 19.

### Modificación del almacenamiento:
1. Para la modificación se entra a la sección de **volumenes**, luego se elige la instancia y **modificar volumen**.
2. Se ingresa el nuevo tamño de almacenamiento correspondiendo a **10 gib**.
3. Se guardan los cambios.

![Modificación del almacenamiento](11-Introduccion-a-Amazon-EC2\20.png)
Figura 20.

### Almacenamiento actualizado:
1. Se modifico correctamente el almacenamiento dela instancia.
2. Se selecciona **Estado de la instancia** y luego **Terminar instancia**, para dar cierre al laboratorio.

![Almacenamiento actualizado](11-Introduccion-a-Amazon-EC2\22.png)
Figura 21.


### Terminar instancia:
1. Se selecciona el **Terminar** para cambiar de estado de la instancia y eliminarla.

![Terminar instancia](11-Introduccion-a-Amazon-EC2\23.png)
Figura 22.

### Instancia eliminada:
1. Se da por terminada la instancia correctamente.

![Instancia eliminada](11-Introduccion-a-Amazon-EC2\24.png)
Figura 23.

### Finalización del laboratorio:
1. Con el laboratorio terminado se procede a finalizar.

![Finalización del laboratorio](11-Introduccion-a-Amazon-EC2\25.png)
Figura 24.

## 💡 Conclusión y Comentarios Personales

La realización de este laboratorio permitió consolidar de forma práctica el ciclo de vida de un servidor en la nube y entender el impacto estratégico de la elasticidad en AWS. Un hito clave del proceso fue la transición de una instancia **t3.micro** a una **t3.small** y la expansión del volumen de almacenamiento de **8 GiB a 10 GiB**; esta maniobra demostró cómo la infraestructura en la nube permite realizar un escalado vertical eficiente en minutos para responder a mayores demandas de memoria (+1024 MB) y espacio, con un incremento marginal en los costos operativos.

Asimismo, la práctica evidenció la importancia de la seguridad y el control de tráfico en redes. El error de acceso inicial al sitio web personalizado confirmó que un servidor funcional requiere de una gobernanza estricta mediante Grupos de Seguridad; habilitar la regla de entrada para el protocolo **HTTP (Puerto 80)** fue indispensable para liberar el servicio al público. En conclusión, la flexibilidad para modificar recursos en caliente y proteger los activos contra eliminaciones accidentales (Termination Protection) demuestra por qué la computación en la nube es una herramienta administrativa y tecnológica indispensable para garantizar la continuidad y agilidad del negocio.

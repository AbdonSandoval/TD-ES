---
wts:
    title: '2: Implementaci�n de Azure Container Instances'
    module: 'M�dulo 02: Servicios principales de Azure'
---

# 02 - Implementaci�n de Azure Container Instances

En este tutorial creamos, configuramos e implementamos un contenedor Docker mediante Azure Container Instances (ACI) en Azure Portal. El contenedor es una aplicaci�n web Bienvenido a ACI que muestra una p�gina HTML est�tica. 

# Tarea�1: Creaci�n de una instancia de contenedor

En esta tarea, crearemos una nueva instancia de contenedor para la aplicaci�n web. 

1. Inicie sesi�n en [Azure Portal](https://portal.azure.com).

2. Desde la hoja **Todos los servicios**, busque y seleccione **Container instances** y luego haga clic en **A�adir**. 

3. Proporcione los siguientes detalles b�sicos para la nueva instancia de contenedor (deje los valores predeterminados para todo lo dem�s): 

	| Configuraci�n| Valor|
	|----|----|
	| Suscripci�n | **Elija su suscripci�n** |
	| Grupo de recursos | **myRGContainer** (crear nuevo) |
	| Nombre del contenedor| **mycontainer**|
	| Regi�n | **Este de EE. UU.** |
	| Fuente de imagen| **Docker Hub u otro registro**|
	| Tipo de imagen| **P�blico**|
	| Imagen| **microsoft / aci-helloworld**|
	| Tipo de sistema operativo| **Linux** |
	| Tama�o| ***Dejar en el valor predeterminado***|
	|||


4. Configure la pesta�a Redes (reemplace **xxxx** con letras y d�gitos para que el nombre sea globalmente �nico). Deje todas las dem�s configuraciones en sus valores predeterminados.

	| Configuraci�n| Valor|
	|--|--|
	| Etiqueta de nombre DNS| **mycontainerdnsxxxx** |
	|||
	
	**Nota**: Su contenedor ser� accesible p�blicamente en dns-name-label.region.azurecontainer.io. Si recibe un mensaje de error que dice **Etiqueta de nombre DNS no disponible** despu�s de la implementaci�n, especifique una etiqueta de nombre DNS diferente y vuelva a implementar.

	![Captura de pantalla del panel de configuraci�n de la hoja Crear instancias de contenedor en Azure Portal, con la etiqueta de nombre DNS especificada. ](../images/0201.png)

5. Haga clic en **Revisar y crear** para iniciar el proceso de validaci�n autom�tica.

6. Haga clic en **Crear** para crear la instancia de contenedor. 

7. Supervise la p�gina de implementaci�n y la de **Notificaciones**. 

8. Mientras espera puede que est� interesado en ver el [c�digo de muestra detr�s de esta sencilla aplicaci�n](https://github.com/Azure-Samples/aci-helloworld). Examine la carpeta \app. 

# Tarea�2: Compruebe la implementaci�n de la instancia del contenedor

En esta tarea, comprobamos que la instancia del contenedor se est� ejecutando asegur�ndonos de que se muestre la p�gina de bienvenida.

1. Una vez completada la implementaci�n, haga clic en el enlace **Ir al recurso** en la hoja de implementaci�n o el enlace al recurso en el �rea de notificaci�n.

2. En la hoja **Visi�n general** de **mycontainer**, aseg�rese de que el **Estado** de su contenedor est� **ejecut�ndose**. 

3. Localice el nombre de dominio completo (FQDN).

	![Captura de pantalla del panel de informaci�n general para el contenedor reci�n creado en Azure Portal, con el FQDN resaltado. ](../images/0202.png)

2. Copie el FQDN del contenedor en el explorador web del cuadro de texto URL y presione **Entrar**. La p�gina de bienvenida deber�a aparecer. 

	![Captura de pantalla del mensaje de bienvenida de ACI que se muestra en un explorador web.](../images/0203.png)

**Nota**: Tambi�n puede usar la direcci�n IP del contenedor en su explorador. 

�Enhorabuena! Ha usado Azure Portal para implementar con �xito una aplicaci�n en un contenedor en instancia de contenedor Azure.

**Nota**: Para evitar costes adicionales, puede eliminar este grupo de recursos. Busque grupos de recursos, haga clic en su grupo de recursos y, a continuaci�n, haga clic en **Eliminar grupo de recursos**. Compruebe el nombre del grupo de recursos y luego haga clic en **Eliminar**. Supervise las **Notificaciones** para ver c�mo se realiza la eliminaci�n.

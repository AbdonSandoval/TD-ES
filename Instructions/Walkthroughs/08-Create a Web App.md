---
wts:
    title: '8: Crear una aplicaci�n web'
    module: 'M�dulo 02: Servicios principales de Azure'
---
# 08 - Crear una aplic. web

En este tutorial, crearemos una nueva aplic. web que ejecute un contenedor Docker. El contenedor muestra un mensaje de bienvenida. 

# Tarea�1: Cree una aplicaci�n web

Azure App Service es en realidad una colecci�n de cuatro�servicios, los cuales est�n dise�ados para hospedar y ejecutar aplicaciones web. Los cuatro�servicios (Web Apps, Mobile Apps, API Apps y Logic Apps) se ven diferentes, pero, al final, todos funcionan de manera muy similar. De los cuatro servicios, las Web�Apps son las que se usan con mayor frecuencia y es el servicio que utilizaremos en este laboratorio.

En esta tarea, crear� una aplicaci�n web de Azure App Service. 

1. Inicie sesi�n en [Azure Portal](http://portal.azure.com/). 

2. Desde la hoja **Todos los servicios**, busque y seleccione **App Services** y haga clic en **+�Agregar**.

3. En la pesta�a **Datos b�sicos** de la hoja **Aplicaci�n web**, especifique la siguiente configuraci�n (reemplace **xxxx** en el nombre de la aplicaci�n web con letras y d�gitos para que el nombre sea �nico a nivel mundial). Deje los valores predeterminados para todo lo dem�s, incluido el plan de App Service. 

    | Configuraci�n | Valor |
    | -- | -- |
    | Suscripci�n | **Elija su suscripci�n** |
    | Grupo de recursos | **myRGWebApp1** (crear nuevo) |
    | Nombre | **myDockerWebAppxxxx** |
    | Publicar | **Contenedor de Docker** |
    | Sistema operativo | **Linux** |
    | Regi�n | **Este de EE.�UU.** (ignore cualquier advertencia de disponibilidad del plan de servicio) |
    | | |	

4. Haga clic en **Siguiente�>�Docker** y configure la informaci�n del contenedor. El comando de inicio es opcional y no es necesario en este ejercicio. 

    **Nota:** Este es el mismo contenedor que se utiliz� en el tutorial de Container Instances para mostrar un mensaje de Hola mundo. 

    | Configuraci�n | Valor |
    | -- | -- |
    | Opciones | **Contenedor individual** |
    | Fuente de la imagen | **Docker Hub** |
    | Tipo de acceso | **P�blico** |
    | Imagen y etiqueta | **microsoft/aci-helloworld** |
    | | |	


5. Haga clic en **Revisar + crear**, y luego haga clic en **Crear**. 

# Tarea�2: Probar la aplicaci�n web

En esta tarea probaremos la aplicaci�n web.

1. Espere a que se implemente la aplicaci�n web.

2. Desde **Notificaciones**, haga clic en **Ir al recurso**. 

3. En la hoja **Informaci�n general**, ubique la entrada **URL**. 

    ![Captura de pantalla de la hoja de propiedades de la aplicaci�n web. La URL est� resaltada.](../images/0801.png)

4. Haga clic en la **URL** para abrir la nueva pesta�a del explorador y mostrar la p�gina Le damos la bienvenida a Azure Container Instances.

    ![Captura de pantalla de la p�gina Le damos la bienvenida a Azure Container Instance.](../images/0802.png)

5. Vuelva a la hoja de **Informaci�n general** de su aplicaci�n web y tenga en cuenta que incluye varios gr�ficos. Si repite el paso�4 varias veces, deber�a poder ver la telemetr�a correspondiente en los gr�ficos. Esto incluye el n�mero de solicitudes y el tiempo de respuesta promedio. 

**Nota**: Para evitar costes adicionales, puede eliminar este grupo de recursos. Busque grupos de recursos, haga clic en su grupo de recursos y, a continuaci�n, haga clic en **Eliminar grupo de recursos**. Compruebe el nombre del grupo de recursos y luego haga clic en **Eliminar**. Supervise las **Notificaciones** para ver c�mo se realiza la eliminaci�n.


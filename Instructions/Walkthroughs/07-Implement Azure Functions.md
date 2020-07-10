---
wts:
    title: '07 - Implementar Azure Functions'
    module: 'M�dulo 02: Servicios principales de Azure'
---
# 07 - Implementar Azure Functions

En este tutorial, crearemos una aplicaci�n de funciones para mostrar un mensaje de saludo cuando haya una solicitud HTTP. 

# Tarea�1: Crear una aplicaci�n de funciones

En esta tarea, crearemos un aplicaci�n de funciones.

1. Inicie sesi�n en [Azure Portal](https://portal.azure.com).

1. En el cuadro de texto **Buscar recursos, servicios y documentos**, en la parte superior del portal, busque y seleccione **Aplicaci�n de funciones** y luego, desde la hoja **Aplicaci�n de funciones**, haga clic en **Agregar**.

1. En la pesta�a **B�sico** de la hoja **Aplicaci�n de funciones**, especifique la siguiente configuraci�n (reemplace **xxxx** en el nombre de la funci�n por letras y d�gitos, de modo que el nombre sea globalmente �nico, y deje todas las dem�s configuraciones con sus valores predeterminados): 

    | Configuraci�n | Valor |
    | -- | --|
    | Suscripci�n | el nombre de su suscripci�n de Azure |
    | Grupo de recursos | el nombre de un nuevo grupo de recursos **myRGFunction** |
    | Nombre de la aplicaci�n de funciones | **funci�n-xxxx** |
    | Publicar | **C�digo** |
    | Pila de tiempo de ejecuci�n | **NET Core** |
    | Regi�n | **Este de EE. UU.** |
    | | |	

1. Haga clic en **Revisar + Crear** y, despu�s de una correcta validaci�n, haga clic en **Crear** para empezar a aprovisionar e implementar su nueva aplicaci�n de funciones de Azure.

1. Espere la notificaci�n de que el recurso ha sido creado.

1. Vuelva a la hoja de **Aplicaci�n de funciones**, haga clic en **Actualizar** y compruebe que la aplicaci�n de funci�n reci�n creada tenga el estado **Ejecutando**. 

    ![Captura de pantalla de la p�gina Aplicaci�n de funciones con la nueva aplicaci�n de funciones.](../images/0701.png)

# Tarea�2: Crear una funci�n activada por HTTP y probar

En esta tarea, usaremos la funci�n API de Webhook para mostrar un mensaje cuando haya una solicitud HTTP. 

1. Sobre la hoja **Aplicaci�n de funciones**, haga clic en la aplicaci�n de funciones reci�n creada. 

1. En la hoja de la aplicaci�n de funciones, en la secci�n **Funciones**, haga clic en **Funciones** y luego en **+ A�adir**.

    ![Captura de pantalla del paso elegir un entorno de desarrollo en Azure Function para el panel de inicio dot net dentro de Azure Portal. Se resaltan los elementos de visualizaci�n para crear una nueva funci�n en el portal. Los elementos resaltados son expandir la aplicaci�n de funciones, agregar nuevas funciones, en el portal y el bot�n continuar.](../images/0702.png)

1. Sobre la pesta�a **Plantillas** de la hoja **Nueva funci�n**, haga clic en **Desencadenador HTTP**. 

    ![Captura de pantalla del paso Crear una funci�n en Azure Functions para el panel de inicio dot net dentro de Azure Portal. La tarjeta de desencadenador HTTP se resalta para ilustrar los elementos de visualizaci�n utilizados para agregar un nuevo webhook a una funci�n de Azure.](../images/0702a.png)

1. Sobre la pesta�a **Detalles** de la hoja **Nueva funci�n**, acepte el nombre predeterminado **Nueva funci�n** y el **Nivel de autorizaci�n** y luego haga clic en **Crear funci�n**. 

    ![Captura de pantalla del paso Crear una funci�n en Azure Functions para el panel de inicio dot net dentro de Azure Portal. El bot�n webhook + API y el bot�n Crear se resaltan para ilustrar los elementos de visualizaci�n que se usan para agregar un nuevo webhook a una funci�n de Azure.](../images/0703.png)

1. En la hoja **HttpTrigger1**, en la secci�n **Desarrollador**, haga clic en **C�digo + Prueba**. 

1. En la hoja **HttpTrigger1 \|** En la hoja **C�digo + prueba**, revise el c�digo generado autom�ticamente y tenga en cuenta que el c�digo est� dise�ado para ejecutar una solicitud HTTP y registrar informaci�n. Adem�s, observe que la funci�n devuelve un mensaje de saludo con un nombre. 

    ![Captura de pantalla del c�digo de funci�n. El mensaje de saludo est� resaltado.](../images/0704.png)

1. Haga clic en **Obtener URL de funci�n** desde la secci�n superior del editor de funciones. 

1. Aseg�rese de que el valor en la lista desplegable **Clave** se establece en **predeterminado** y haga clic en **Copiar** para copiar la funci�n URL. 

    ![Captura de pantalla del panel URL de obtenci�n de funciones dentro del editor de funciones en Azure Portal. Los elementos de visualizaci�n obtienen el bot�n URL de la funci�n, establecen el men� desplegable de teclas y el bot�n Copiar URL se resaltan para indicar c�mo obtener y copiar la URL de la funci�n desde el editor de funciones.](../images/0705.png)

1. Abra una nueva pesta�a del explorador y pegue la URL de la funci�n copiada en la barra de direcciones del explorador web. Cuando se solicite la p�gina, la funci�n se ejecutar�. Observe el mensaje devuelto que indica que la funci�n requiere un nombre en el cuerpo de la solicitud.

    ![Captura de pantalla del mensaje para proporcionar un nombre.](../images/0706.png)

1. Agregue **&name=*yourname*** al final de la URL.

    **Nota**: Reemplace ***yourname*** con su nombre. Por ejemplo, si su nombre es Cindy, la URL final se parecer� a la siguiente `https://azfuncxxx.azurewebsites.net/api/HttpTrigger1?code=X9xx9999xXXXXX9x9xxxXX==&name=cindy`

    ![Captura de pantalla de una URL de funci�n resaltada y un nombre de usuario de ejemplo adjunto en la barra de direcciones de un explorador web. El mensaje de saludo y el nombre de usuario tambi�n se resaltan para ilustrar el resultado de la funci�n en la ventana principal del explorador.](../images/0707.png)

1. Cuando se ejecuta su funci�n, se rastrea cada invocaci�n. Para ver el seguimiento en Azure Portal, vuelva a **HttpTrigger1 \|** Hoja **C�digo + Prueba** y haga clic en **Supervisar**.

    ![Captura de pantalla de un registro de informaci�n de seguimiento resultante de ejecutar la funci�n dentro del editor de funciones en Azure Portal.](../images/0709.png) 

�Enhorabuena! Ha creado una aplicaci�n de funciones para mostrar un mensaje de saludo cuando hay una solicitud HTTP. 

**Nota**: Para evitar costes adicionales, puede eliminar este grupo de recursos. Busque grupos de recursos, haga clic en su grupo de recursos y, a continuaci�n, haga clic en **Eliminar grupo de recursos**. Compruebe el nombre del grupo de recursos y luego haga clic en **Eliminar**. Supervise las **Notificaciones** para ver c�mo se realiza la eliminaci�n.

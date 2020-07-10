---
wts:
    title: '09: Crear una m�quina virtual con una plantilla'
    module: 'M�dulo 02: Servicios principales de Azure'
---
# 09: Crear una m�quina virtual con una plantilla

En este tutorial implementaremos una m�quina virtual con una plantilla de inicio r�pido y examinaremos las capacidades de monitoreo.

# Tarea1: Explore la galer�a y localice una plantilla

En esta tarea, examinaremos la galer�a Azure QuickStart e implementaremos una plantilla que crea una m�quina virtual. 

1. En el explorador, acceda a [Galer�a de plantillas de Azure Quickstart](https://azure.microsoft.com/resources/templates?azure-portal=true). En la galer�a encontrar� una serie de plantillas populares y recientemente actualizadas. Estas plantillas automatizan la implementaci�n de los recursos de Azure, incluida la instalaci�n de paquetes de software populares.

2. Explore los diferentes tipos de plantillas disponibles. 

    **Nota**: �Hay alguna plantilla que le interese?

3. Busque o acceda directamente a la plantilla [Implementar una m�quina virtual de Windows simple](https://azure.microsoft.com/resources/templates/101-vm-simple-windows?azure-portal=true).

    **Nota**: El bot�n **Implementar en Azure** le permite implementar la plantilla a trav�s de Azure Portal. Durante dicha implementaci�n, se le pedir� confirmaci�n solo de un peque�o conjunto de par�metros de configuraci�n. 

4. Haga clic en el bot�n **Implementar en Azure**. Su sesi�n del explorador se redirigir� autom�ticamente a [Azure Portal](http://portal.azure.com/).

5. Si se le solicita, inicie sesi�n en la suscripci�n de Azure que desea usar en este laboratorio.

6. Haga clic en **Editar plantilla**. El formato de la plantilla de Resource�Manager usa el formato�JSON. Revise las variables y localice el nombre de la m�quina virtual. Cambie el nombre a **myVMTemplate**. Seleccione **Guardar** para guardar los cambios. Regresa a la hoja **Implementaci�n personalizada** en el Azure Portal.

    ![Captura de pantalla de la plantilla con el cambio de nombre de VM resaltado.](../images/0901.png)

7. En la hoja **Implementaci�n personalizada**, configure los par�metros requeridos por la plantilla (reemplace ***xxxx*** en el prefijo de la etiqueta DNS con letras y d�gitos de modo que la etiqueta sea globalmente �nica). Deje los valores predeterminados para todo lo dem�s. 

    | Configuraci�n| Valor|
    |----|----|
    | Suscripci�n | **Elija su suscripci�n**|
    | Grupo de recursos | **myRGTemplate** (crear nuevo) |
    | Ubicaci�n | **Este de EE. UU.** |
    | Nombre del usuario administrador | **azureuser** |
    | Contrase�a del administrador | **Pa$$w0rd1234** |
    | Prefijo de etiqueta DNS | **myvmtemplate*xxxx*** |
    | Versi�n del sistema operativo Windows | **2019-Centro de datos** |
    | | |

8. Marque la casilla **Acepto los t�rminos y las condiciones establecidos anteriormente** y luego haga clic en **Comprar**.

    **Nota**: No hay coste asociado con esta plantilla.

9. Supervise su implementaci�n. 

# Tarea�2: Compruebe la m�quina virtual y haga un seguimiento de ella

En esta tarea, comprobaremos que la m�quina virtual se implement� correctamente. 

1. Desde la hoja **Todos los servicios**, busque y seleccione **Maquinas virtuales**.

2. Aseg�rese de que se haya creado su nueva m�quina virtual. 

    ![Captura de pantalla de la p�gina de m�quinas virtuales. Se muestra y se ejecuta la nueva VM.](../images/0902.png)

3. Seleccione su m�quina virtual y en el panel **Informaci�n general** despl�cese hacia abajo para ver los datos de supervisi�n.

    **Nota**: El plazo de supervisi�n se puede ajustar de una hora a 30 d�as.

4. Revise los diferentes cuadros que se proporcionan, incluidos **CPU (promedio)**, **Red (total)**y **Bytes de disco (total)**. 

    ![Captura de pantalla de los cuadros de supervisi�n de m�quinas virtuales.](../images/0903.png)

5. Haga clic en cualquier gr�fico. Tenga en cuenta que puede seleccionar **Agregar m�trica** y cambiar el tipo de gr�fico. Dado que tiene tiempo, experimente. 

6. Vuelva a la hoja **Visi�n general**.

7. Haga clic en el **Registro de actividades** (panel izquierdo). Los registros de actividad registran eventos tales como la creaci�n o modificaci�n de recursos. 

8. Haga clic en **A�adir filtro** y experimente buscando diferentes tipos de eventos y operaciones. 

    ![Captura de pantalla de la p�gina A�adir filtros con el tipo de evento seleccionado.](../images/0904.png)

**Nota**: Para evitar costes adicionales, puede eliminar este grupo de recursos. Busque grupos de recursos, haga clic en su grupo de recursos y, a continuaci�n, haga clic en **Eliminar grupo de recursos**. Compruebe el nombre del grupo de recursos y luego haga clic en **Eliminar**. Supervise las **Notificaciones** para ver c�mo se realiza la eliminaci�n.

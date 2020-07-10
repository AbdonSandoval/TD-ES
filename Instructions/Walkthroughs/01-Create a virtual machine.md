---
wts:
    title: '1: Crear una m�quina virtual en el portal'
    module: 'M�dulo 02: Servicios principales de Azure'
---
# 01 - Crear una m�quina virtual en el portal

En este tutorial crearemos una m�quina virtual en el Azure Portal, nos conectaremos a dicha m�quina virtual, instalaremos la funci�n del servidor web y la probaremos. 

**Nota**: T�mese el tiempo durante este tutorial para hacer clic y leer los iconos informativos. 

# Tarea�1: Crear la m�quina virtual

En esta tarea, crearemos una m�quina virtual de Windows Server 2019 Datacenter. 

1. Inicie sesi�n en [Azure Portal](https://portal.azure.com).

2. Desde la hoja **Todos los servicios**, busque y seleccione **M�quinas virtuales** y luego haga clic en **+ Agregar**.

3. En la pesta�a **Datos b�sicos**, complete la siguiente informaci�n (deje los valores predeterminados para todo lo dem�s):

    | Configuraci�n | Valores |
    |  -- | -- |
    | Suscripci�n | **Elija su suscripci�n**|
    | Grupo de recursos | **myRGVM** (crear nueva) |
    | Nombre de la m�quina virtual | **myVm** |
    | Ubicaci�n | **Este de EE. UU.**|
    | Imagen | **Windows Server 2019 Datacenter**|
    | Tama�o | Est�ndar D2s, v3|
    | Nombre de usuario de la cuenta de administrador | **azureuser** |
    | Contrase�a de cuenta de administrador | **Pa$$w0rd1234**|
    | Reglas del puerto de entrada - Permitir puertos seleccionados | **RDP (3389)** y **HTTP (80)**|
    | | |

4. Vaya a la pesta�a Administraci�n y, en la secci�n **Monitoreo**, seleccione la siguiente configuraci�n:

    | Configuraci�n | Valores |
    | -- | -- |
    | Diagn�stico de arranque | **Off**|
    | | |

5. Deje los valores predeterminados restantes y luego haga clic en el bot�n **Revisar + crear**, en la parte inferior de la p�gina.

6. Una vez que se pasa la validaci�n, haga clic en el bot�n **Crear**. La implementaci�n de la m�quina virtual puede demorar entre cinco y siete minutos.

7. Recibir� actualizaciones en la p�gina de implementaci�n y a trav�s del �rea **Notificaciones** (el icono de la campana en el men� superior).

# Tarea�2: Conectarse a la m�quina virtual

En esta tarea nos conectaremos a nuestra nueva m�quina virtual usando el RDP. 

1. Busque **myVM** y seleccione su nueva m�quina virtual.

    **Nota**: Tambi�n puede usar el v�nculo **Ir al recurso** en la p�gina de implementaci�n o el enlace para acceder al recurso en el �rea de **Notificaciones**.

2. En la hoja de **Informaci�n general** de la m�quina virtual, haga clic en el bot�n **Conectar**.

    ![Captura de pantalla de las propiedades de la m�quina virtual con el bot�n Conectar resaltado.](../images/0101.png)

    **Nota**: Las siguientes instrucciones le indican c�mo conectarse a su VM desde un equipo con Windows. En una Mac necesita un cliente RDP, como este Remote Desktop Client de Mac App Store, y en un PC Linux puede usar un cliente RDP de c�digo abierto.

2. En la p�gina **Conectarse a la m�quina virtual**, mantenga las opciones predeterminadas para conectarse con la direcci�n IP p�blica a trav�s del puerto 3389 y haga clic en **Descargar archivo RDP**.

3. **Abra** el archivo RDP descargado y haga clic en **Conectar** cuando se le solicite. 

    ![Captura de pantalla de las propiedades de la m�quina virtual con el bot�n Conectar resaltado. ](../images/0102.png)

4. En la ventana **Seguridad de Windows**, seleccione **M�s opciones** y luego **Usar una cuenta diferente**. Proporcione el nombre de usuario (.\azureuser) y la contrase�a (Pa$$w0rd1234). Haga clic en **Aceptar** para conectarse.

    ![Captura de pantalla del di�logo de seguridad de Windows con la opci�n Usar una cuenta diferente seleccionada, y el nombre de usuario Azure y una contrase�a ingresados.](../images/0103.png)

5. Es posible que reciba una advertencia de certificado durante el proceso de inicio de sesi�n. Haga clic en **S�** o cree la conexi�n y con�ctese a su VM implementada. Deber�a conectarse correctamente.

    ![Captura de pantalla del cuadro de di�logo de advertencia de certificado que informa al usuario de un certificado no confiable, con el bot�n S� resaltado. ](../images/0104.png)

�Enhorabuena! Ha implementado una m�quina virtual de Windows Server en Azure y se ha conectado a ella

# Tarea�3: Instalar la funci�n del servidor web y probarla

En esta tarea, instale el rol Servidor web en el servidor y aseg�rese de que se pueda mostrar la p�gina de bienvenida de IIS predeterminada.

1. Abra un s�mbolo del sistema de PowerShell en la m�quina virtual. Para ello, haga clic en el bot�n **Iniciar**, escriba **PowerShell**, haga clic con el bot�n derecho en **Windows PowerShell** y seleccione **Ejecutar como administrador** en el men� contextual.

    ![Captura de pantalla del escritorio de la m�quina virtual con el bot�n de inicio presionado y PowerShell seleccionado, con la opci�n Ejecutar como administrador resaltada.](../images/0105.png)

2. Instale la caracter�stica **Servidor web** en la m�quina virtual al ejecutar el siguiente comando en el s�mbolo del sistema de PowerShell. Puede copiar y pegar este comando.

    ```PowerShell
    Install-WindowsFeature -name Web-Server -IncludeManagementTools
    ```
  
3. Cuando complete este paso, aparecer� un aviso que indicar� **Correcto** con un valor **Verdadero**. No es necesario que reinicie la m�quina virtual para completar la instalaci�n. Cierre la conexi�n RDP a la VM.

    ![Captura de pantalla del s�mbolo del sistema de Windows PowerShell con el comando Install-WindowsFeature -name Web-Server -IncludeManagementTools completado correctamente y la salida que indica que fue exitoso.](../images/0106.png)

4. De vuelta en el portal, navegue hasta la hoja **Informaci�n general** de myVM y use el bot�n **Clic para copiar al Portapapeles** para copiar la direcci�n IP p�blica de myVM. Abra una nueva pesta�a del explorador, pegue la direcci�n IP p�blica en el cuadro de texto de URL y presione la tecla **Entrar** para acceder a ella.

    ![Captura de pantalla del panel de propiedades de la m�quina virtual de Azure Portal con la direcci�n IP copiada.](../images/0107.png)

5. Se abrir� la p�gina de bienvenida predeterminada del servidor web IIS.

    ![Captura de pantalla de la p�gina de bienvenida predeterminada del servidor web IIS a la que se accede a trav�s de la direcci�n IP p�blica en un explorador web.](../images/0108.png)

�Enhorabuena! Cre� un servidor web al que se puede acceder a trav�s de su direcci�n IP p�blica. Si tuviera una aplicaci�n web para hospedar, podr�a implementar archivos de aplicaci�n en la m�quina virtual y hospedarlos para acceso p�blico en la m�quina virtual implementada.


**Nota**: Para evitar costes adicionales, puede eliminar este grupo de recursos. Busque grupos de recursos, haga clic en su grupo de recursos y, a continuaci�n, haga clic en **Eliminar grupo de recursos**. Compruebe el nombre del grupo de recursos y luego haga clic en **Eliminar**. Monitoree las **Notificaciones** para verificar que la eliminaci�n se haya completado correctamente. 

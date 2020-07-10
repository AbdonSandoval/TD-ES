---
wts:
    title: '6: Implementar un Azure IoT Hub'
    module: 'M�dulo 02: Servicios principales de Azure'
---
# 06 - Implementar un Azure IoT Hub

En este tutorial, configuraremos un nuevo Azure IoT Hub en Azure Portal, y luego autenticaremos una conexi�n a un dispositivo IoT usando el simulador de dispositivo Raspberry Pi en l�nea. Los datos y los mensajes del sensor se pasan del simulador de Raspberry Pi a su Azure IoT Hub, y puede ver las m�tricas para la actividad de mensajer�a en Azure Portal.

# Tarea�1: Crear un centro de IoT 

En esta tarea, crearemos un centro de IoT. 

1. Inicie sesi�n en [Azure Portal](https://portal.azure.com).

2. Desde la hoja **Todos los servicios**, busque y seleccione **Centro de IoT** y luego haga clic en **+�Agregar**.

3. En la pesta�a **Datos b�sicos** de la hoja **centro de IoT**, complete los campos con los siguientes detalles (reemplace **xxxx** en el nombre de la cuenta de almacenamiento con letras y d�gitos de modo que el nombre sea globalmente �nico):

    | Configuraci�n | Valor |
    |--|--|
    | Suscripci�n | **Elija su suscripci�n** |
    | Grupo de recursos |  **myRGIoT** (crear nuevo)|
    | Regi�n | **Este de EE.�UU.** |
    | Nombre del centro de IoT | **my-hub-groupxxxx** |
    | | |	

4. Vaya a la pesta�a **Tama�o y escala**, use la lista desplegable para configurar **Precios y nivel de escala** en **S1: Nivel est�ndar**. 

5. Haga clic en el bot�n **Revisar + Crear**.

6. Haga clic en el bot�n **Crear** para comenzar a crear su nueva instancia de Azure IoT Hub.

7. Espere hasta que se implemente la instancia de Azure IoT Hub. 

# Tarea�2: Agregar un dispositivo de IoT

En esta tarea, agregaremos un dispositivo IoT al centro de IoT. 

1. Cuando la implementaci�n se haya completado, haga clic en **Ir al recurso** desde la hoja de implementaci�n. Si no, desde la hoja **Todos los servicios**, busque y seleccione **Centro de IoT** y ubique su nueva instancia de centro de IoT.

	![Captura de pantalla de la implementaci�n en curso y notificaciones de implementaci�n exitosa en Azure Portal.](../images/0601.png)

2. Para a�adir un nuevo dispositivo IoT, despl�cese hacia abajo hasta la secci�n **Exploradores** y haga clic en **Dispositivos IoT**. Luego, haga clic en **+ Nuevo**.

	![Captura de pantalla del panel de dispositivos IoT, resaltado dentro de la hoja de navegaci�n del centro IoT, en Azure Portal. El bot�n Nuevo se resalta para ilustrar c�mo a�adir una nueva identidad del dispositivo IoT al centro de IoT.](../images/0602.png)

3. Proporcione un nombre para su nuevo dispositivo IoT, **myRaspberryPi**, y haga clic en el bot�n **Guardar**. Esto crear� una nueva identidad del dispositivo IoT en su Azure IoT Hub.

4. Si no ve su nuevo dispositivo, **actualice** la p�gina de dispositivos IoT. 

5. Seleccione **myRaspberryPi** y copie el valor **Cadena de conexi�n primaria**. Utilizar� esta clave en la siguiente tarea para autenticar una conexi�n al simulador de Raspberry Pi.

	![Captura de pantalla de la p�gina Cadena de conexi�n primaria con el icono de copia resaltado.](../images/0603.png)

# Tarea�3: Probar el dispositivo con el simulador de Raspberry Pi

En esta tarea probaremos nuestro dispositivo usando el simulador de Raspberry Pi. 

1. Abra una nueva pesta�a en el explorador web y navegue hasta el [simulador en l�nea de Raspberry Pi](https://azure-samples.github.io/raspberry-pi-web-simulator/#Getstarted). 

2. Lea sobre el simulador de Raspberry Pi. Si hay una ventana emergente de informaci�n general, seleccione "**X**" para cerrar la ventana.

3. En el �rea de c�digo, al lado derecho, ubique la l�nea con 'const connectionString ='. Reempl�celo con la cadena de conexi�n que copi� de Azure Portal. Tenga en cuenta que la cadena de conexi�n incluye las entradas DeviceId (**myRaspberryPi**) y SharedAccessKey.

	![Captura de pantalla del �rea de codificaci�n dentro del simulador de Raspberry Pi.](../images/0604.png)

4. Haga clic en **Ejecutar** (debajo del �rea de c�digo) para ejecutar la aplicaci�n. La salida de la consola debe mostrar los datos y mensajes del sensor que se env�an desde el simulador de Raspberry Pi a su Azure IoT Hub. Los datos y mensajes se env�an cada vez que parpadea el LED del simulador Raspberry Pi. 

	![Captura de pantalla de la consola del simulador Raspberry Pi.  La salida de la consola muestra los datos y mensajes del sensor enviados desde el simulador de Raspberry Pi a Azure IoT Hub.](../images/0605.png)

5. Haga clic en **Detener** para dejar de enviar datos.

6. Regrese al Azure Portal y a su centro de IoT.

7. Cambie la hoja de **Informaci�n general** del centro de IoT y despl�cese hacia abajo hasta la informaci�n de **Utilizaci�n del centro de IoT**.

	![Captura de pantalla de las m�tricas dentro del �rea de utilizaci�n del centro de IoT de Azure Portal.](../images/0606.png)


�Enhorabuena! Ha configurado Azure IoT Hub para recopilar datos del sensor de un dispositivo IoT.

**Nota**: Para evitar costes adicionales, puede eliminar este grupo de recursos. Busque grupos de recursos, haga clic en su grupo de recursos y, a continuaci�n, haga clic en **Eliminar grupo de recursos**. Compruebe el nombre del grupo de recursos y luego haga clic en **Eliminar**. Supervise las **Notificaciones** para ver c�mo se realiza la eliminaci�n.

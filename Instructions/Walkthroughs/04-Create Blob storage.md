---
wts:
    title: '04: Creaci�n de almacenamiento de blobs'
    module: 'M�dulo 02: Servicios principales de Azure'
---
# 04 - Crear almacenamiento de blobs

En este tutorial, crearemos una cuenta de almacenamiento y luego trabajaremos con archivos de almacenamiento de blobs.

# Tarea�1: Crear una cuenta de almacenamiento

En esta tarea crearemos una nueva cuenta de almacenamiento. 

1. Inicie sesi�n en Azure Portal en <a href="https://portal.azure.com" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://portal.azure.com</span></a>

2. Desde la hoja **Todos los servicios**, busque y seleccione **Cuentas de almacenamiento** y luego haga clic en **+�Agregar**. 

3. En la pesta�a **Datos b�sicos** de la hoja **Crear cuenta de almacenamiento**, complete la siguiente informaci�n (reemplace **xxxx** en el nombre de la cuenta de almacenamiento con letras y d�gitos de modo que el nombre sea globalmente �nico). Deje los valores predeterminados para todo lo dem�s.

    | Configuraci�n | Valor | 
    | --- | --- |
    | Suscripci�n | **Elija su suscripci�n** |
    | Grupo de recursos | **myRGStorage** (crear nuevo) |
    | Nombre de la cuenta de almacenamiento | **storageaccountxxxx** |
    | Ubicaci�n | **Este de EE. UU.**  |
    | Rendimiento | **Est�ndar** |
    | Variante de cuenta | **Almacenamiento�V2 (uso general�v2)** |
    | Replicaci�n | **Almacenamiento con redundancia local (LRS)** |
    | Nivel de acceso (predeterminado) | **Frecuente** |
    | | |

5. Haga clic en **Revisar�+�Crear** para revisar la configuraci�n de su cuenta de almacenamiento y permitir que Azure valide la configuraci�n. 

6. Una vez validada, haga clic en **Crear**. Espere la notificaci�n de que la cuenta se cre� correctamente. 

7. Desde la p�gina de inicio, busque y seleccione **Cuentas de almacenamiento** y aseg�rese de que su nueva cuenta de almacenamiento aparezca en la lista.

    ![Captura de pantalla de la cuenta de almacenamiento reci�n creada en Azure Portal.](../images/0401.png)

# Tarea�2: Trabaje con almacenamiento de blobs

En esta tarea, crearemos un contenedor de blobs y subiremos un archivo de blobs. 

1. Haga clic en el nombre de la nueva cuenta de almacenamiento, despl�cese hasta la secci�n **Blob service** y luego haga clic **Contenedores**.

2. Haga clic en **+ Contenedor** y complete la informaci�n. Use los iconos de informaci�n para obtener m�s informaci�n. Cuando termine, haga clic en **Aceptar**.


    | Valor | Valor |
    | --- | --- |
    | Nombre | **contenedor1**  |
    | Nivel de acceso p�blico| **Privado (sin acceso an�nimo)** |
    | | |

    ![Captura de pantalla del contenedor de blobs reci�n creado en la cuenta de almacenamiento en Azure Portal.](../images/0402.png)

4. Haga clic en el contenedor **contenedor1** y luego en **Cargar**.

5. Busque un archivo en su computadora local. 

    **Nota**: Puede crear un archivo `.txt` vac�o o usar cualquier archivo existente. Considere elegir un archivo de tama�o peque�o para minimizar el tiempo de carga.

6. Haga clic en la flecha **Avanzado**, deje los valores predeterminados pero revise las opciones disponibles y luego haga clic en **Cargar**.

    **Nota**: Puede cargar tantos blobs como quiera de esta manera. Los nuevos blobs se enumerar�n dentro del contenedor.

7. Una vez que se carga el archivo, haga clic con el bot�n derecho en el archivo y observe las opciones que incluyen Ver/editar, Descargar, Propiedades y Eliminar. 

8. A medida que tenga tiempo, desde la hoja de la cuenta de almacenamiento, revise las opciones para Archivos, Tablas y Colas.

# Tarea�3: Supervisar la cuenta de almacenamiento

1. Si es necesario, regrese a la hoja de la cuenta de almacenamiento y haga clic en **Diagnosticar y resolver problemas**. 

2. Explore algunos de los problemas de almacenamiento m�s comunes. Tenga en cuenta que hay m�ltiples solucionadores de problemas.

3. En la hoja de la cuenta de almacenamiento, despl�cese hacia abajo hasta la secci�n **Supervisi�n** y haga clic en **Informaci�n (vista previa)**. Observe que hay informaci�n sobre Fallas, Rendimiento, Disponibilidad y Capacidad. Su informaci�n ser� diferente.

    ![Captura de pantalla de la p�gina Insights de la cuenta de almacenamiento.](../images/0403.png)

�Enhorabuena! Cre� una cuenta de almacenamiento y luego trabaj� con blobs de almacenamiento.

**Nota**: Para evitar costes adicionales, puede eliminar este grupo de recursos. Busque grupos de recursos, haga clic en su grupo de recursos y, a continuaci�n, haga clic en **Eliminar grupo de recursos**. Compruebe el nombre del grupo de recursos y luego haga clic en **Eliminar**. Supervise las **Notificaciones** para ver c�mo se realiza la eliminaci�n.

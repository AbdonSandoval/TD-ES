---
wts:
    title: '16: Administrar bloqueos de recursos'
    module: 'M�dulo 03: Seguridad, privacidad, cumplimiento y confianza'
---
# 16 - Administrar bloqueos de recursos

En este tutorial, crearemos un grupo de recursos, a�adiremos un bloqueo al grupo de recursos y probaremos su eliminaci�n, probaremos la eliminaci�n de un recurso en el grupo de recursos y quitaremos el bloqueo de recursos. 

# Tarea�1: Crear un grupo de recursos

En esta tarea, crearemos un grupo de recursos para este ejercicio. 

1. Inicie sesi�n en [Azure Portal](https://portal.azure.com).

2. Desde la hoja **Todos los servicios**, busque y seleccione **Grupos de recursos**, luego seleccione **+�A�adir**.

3. Cree un grupo de recursos nuevo. Cuando haya terminado, haga clic en **Revisar�+�crear** y luego en **Crear**. 

    | Configuraci�n | Valor |
    | -- | -- |
    | Suscripci�n | **Use su suscripci�n** |
    | Nombre | **myRGLocks** |
    | Regi�n | **Este de EE. UU.** |
    | | |

# Tarea�2:  A�adir un bloqueo al grupo de recursos y probar su eliminaci�n

En esta tarea, agregaremos un bloqueo de recursos al grupo de recursos y probaremos la eliminaci�n del grupo de recursos. 

1. En Azure Portal, navegue hasta el grupo de recursos reci�n creado **myRGLocks**.

2. Puede aplicar un bloqueo a una suscripci�n, un grupo de recursos o un recurso individual para evitar la eliminaci�n o modificaci�n accidental de recursos cr�ticos. 

3. En la secci�n **Configuraci�n**, haga clic en **Bloqueos** y luego en **+�Agregar**. 

    ![Captura de pantalla del grupo de recursos myRGLocks  mostrando el panel Bloqueos.](../images/1601.png)

4. Configure el nuevo bloqueo. Al finalizar, haga clic en **Aceptar**. 

    | Configuraci�n | Valor |
    | -- | -- |
    | Nombre del bloqueo | **RGLock** |
    | Tipo de bloqueo | **Eliminar** |
    | | |

5. Haga clic en **Informaci�n general** y en **Eliminar grupo de recursos**. Escriba el nombre del grupo de recursos y haga clic en **Aceptar**. Recibir� un mensaje de error que indica que el grupo de recursos est� bloqueado y que no se puede eliminar.

    ![Captura de pantalla del error de eliminaci�n de bloqueos.](../images/1602.png)

# Tarea�3: Pruebe eliminar un miembro del grupo de recursos

En esta tarea, probaremos si el bloqueo de recursos protege una cuenta de almacenamiento en el grupo de recursos. 

1. Desde la hoja **Todos los servicios**, busque y seleccione **Cuentas de almacenamiento** y luego haga clic en **+�Agregar**. 

2. En la pesta�a **Datos b�sicos** de la hoja **Crear cuenta de almacenamiento**, complete la siguiente informaci�n (reemplace **xxxx** en el nombre de la cuenta de almacenamiento con letras y d�gitos de modo que el nombre sea globalmente �nico). Deje los valores predeterminados para todo lo dem�s.

    | Configuraci�n | Valor | 
    | --- | --- |
    | Suscripci�n | **Seleccione su suscripci�n** |
    | Grupo de recursos | **myRGLocks** |
    | Nombre de la cuenta de almacenamiento | **storageaccountxxxx** |
    | Ubicaci�n | **Este de EE. UU.**  |
    | Rendimiento | **Est�ndar** |
    | Variante de cuenta | **Almacenamiento�V2 (uso general�v2)** |
    | Replicaci�n | **Almacenamiento con redundancia local (LRS)** |
    | Nivel de acceso (predeterminado) | **Frecuente** |
    | | |

3. Haga clic en **Revisar�+�Crear** para revisar la configuraci�n de su cuenta de almacenamiento y permitir que Azure valide la configuraci�n. 

4. Una vez validada, haga clic en **Crear**. Espere la notificaci�n de que la cuenta se cre� correctamente. 

5.  Espere la notificaci�n de que la cuenta de almacenamiento se cre� correctamente. 

6. Acceda a su nueva cuenta de almacenamiento y, desde el panel **Informaci�n general**, haga clic en **Eliminar**. Recibir� un mensaje de error que indica que el recurso o su primario tiene un bloqueo de eliminaci�n. 

    ![Captura de pantalla del error al eliminar la cuenta de almacenamiento.](../images/1603.png)

    **Nota**: Aunque no hayamos creado espec�ficamente un bloqueo para la cuenta de almacenamiento, hemos creado un bloqueo en el nivel del grupo de recursos que contiene la cuenta de almacenamiento. Como tal, este bloqueo de nivel *primario* nos impide eliminar el recurso y la cuenta de almacenamiento hereda el bloqueo del nivel primario.

# Tarea�4 Quitar el bloqueo de recurso

En esta tarea quitaremos el bloqueo del recurso y lo probaremos. 

1. Vuelva a la hoja del grupo de recursos **miRGLocks** y, en la secci�n **Configuraci�n**, haga clic en **Bloqueos**.
    
2. Haga clic en el v�nculo **Eliminar** a la derecha de la entrada **RGLock**.

    ![Captura de pantalla del bloqueo con el v�nculo Eliminar resaltado](../images/1604.png)

3. Vuelva a la hoja de la cuenta de almacenamiento y confirme que ahora puede eliminar el recurso.

�Enhorabuena! Cre� un grupo de recursos, agreg� un bloqueo al grupo de recursos y prob� su eliminaci�n, prob� la eliminaci�n de un recurso en el grupo de recursos y quit� el bloqueo de un recurso. 

**Nota**: Para evitar costes adicionales, puede eliminar este grupo de recursos. Busque grupos de recursos, haga clic en su grupo de recursos y, a continuaci�n, haga clic en **Eliminar grupo de recursos**. Compruebe el nombre del grupo de recursos y luego haga clic en **Eliminar**. Supervise las **Notificaciones** para ver c�mo se realiza la eliminaci�n.
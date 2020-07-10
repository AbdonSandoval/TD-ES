---
wts:
    title: '13: Implementar Azure Key Vault'
    module: 'M�dulo 03: Seguridad, privacidad, cumplimiento y confianza'
---
# 13 - Implementar Azure Key Vault

En este tutorial, crearemos un Azure Key Vault y luego crearemos un secreto de contrase�a en ese almac�n de claves, lo que le proporciona una contrase�a almacenada de forma segura y administrada de manera centralizada para su uso con aplicaciones.

# Tarea�1: Crear un almac�n de claves de Azure

1. Inicie sesi�n en [Azure Portal](https://portal.azure.com).

2. Desde la hoja **Todos los servicios**, busque y seleccione **Almacenes de claves** y, luego, **+ A�adir**.

3. Configure el almac�n de claves (reemplace **xxxx** en el nombre del almac�n de claves con letras y d�gitos de manera que el nombre sea globalmente �nico). Deje los valores predeterminados para todo lo dem�s.

    | Configuraci�n | Valor | 
    | --- | --- |
    | Suscripci�n | **Use su suscripci�n** |
    | Grupo de recursos | **myRGKV** (crear nuevo) |
    | Nombre del almac�n de claves | **keyvaulttestxxx** |
    | Ubicaci�n | **Este de EE. UU.** |
    | Plan de tarifas | **Est�ndar** |
    | | |

4. Haga clic en **Revisar + crear**, y luego haga clic en **Crear**. 

5. Una vez que se aprovisione el nuevo almac�n de claves, haga clic en **Ir al recurso**. O puede localizar su nuevo almac�n de claves busc�ndolo. 

6. Haga clic en la pesta�a **Informaci�n general** del almac�n de claves y tome nota del **Nombre DNS**. Las aplicaciones que usan su almac�n a trav�s de la API de REST necesitar�n este URI.

7. T�mese un momento para examinar algunas de las otras opciones de almac�n de claves. Debajo de **Configuraciones** revise **Claves**, **Secretos**, **Certificados**, **Pol�ticas de acceso**, **Cortafuegos y redes virtuales**.

    **Nota**: Su cuenta de Azure es la �nica autorizada para realizar operaciones en este nuevo almac�n. Puede modificar esto si lo desea en el **Configuraciones** y luego en la secci�n **Pol�ticas de acceso**.

# Tarea�2: Agregue un secreto a Key�Vault
        
En esta tarea a�adiremos una contrase�a al almac�n de claves. 

1. Debajo de **Configuraciones**, haga clic en **Secretos**, luego haga clic **+ Generar/Importar**.

2. Configure el secreto. Deje los otros valores en sus valores predeterminados. Tenga en cuenta que puede establecer una fecha de expiraci�n y activaci�n. Tenga en cuenta que tambi�n puede deshabilitar el secreto.

    | Configuraci�n | Valor | 
    | --- | --- |
    | Opciones de carga | **Manual** |
    | Nombre | **Contrase�a de ejemplo** |
    | Valor | **hVFkk96** |
    | | |

3. Haga clic en **Crear**.

4. Una vez que el secreto se haya creado con �xito, haga clic en el **Contrase�a de ejemplo** y tenga en cuenta que tiene el estado de **Habilitado**

5. Haga clic en la versi�n actual, observe el **Identificador del secreto**. Este es el valor de la URL que ahora puede usar con las aplicaciones. Proporciona una contrase�a centralmente administrada y almacenada de forma segura.

6. Haga clic en el bot�n **Mostrar valor secreto**, para mostrar la contrase�a que especific� anteriormente.

�Enhorabuena! Ha creado un Azure Key Vault y, luego, un secreto de contrase�a en ese almac�n de claves, lo que le proporciona una contrase�a almacenada de forma segura y administrada centralmente para su uso con aplicaciones.

**Nota**: Para evitar costes adicionales, puede eliminar este grupo de recursos. Busque grupos de recursos, haga clic en su grupo de recursos y, a continuaci�n, haga clic en **Eliminar grupo de recursos**. Compruebe el nombre del grupo de recursos y luego haga clic en **Eliminar**. Supervise las **Notificaciones** para ver c�mo se realiza la eliminaci�n.

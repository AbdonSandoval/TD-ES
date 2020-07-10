---
wts:
    title: '05: Creaci�n de una base de datos SQL'
    module: 'M�dulo 02: Servicios principales de Azure'
---

# 05 - Crear una base de datos SQL

En este tutorial, crearemos una base de datos SQL en Azure y luego consultaremos los datos en esa base de datos.

# Tarea�1: Cree la base de datos

En esta tarea, crearemos una base de datos SQL seg�n la base de datos de muestra AdventureWorksLT. 

1. Inicie sesi�n en Azure Portal a trav�s de [**https://portal.azure.com**](https://portal.azure.com).

2. En la hoja **Todos los servicios**, busque y seleccione **Bases de datos SQL** y, despu�s, haga clic en **+ Agregar**. 

3. En la pesta�a **Datos b�sicos**, rellene esta informaci�n.  

    | Valor | Valor | 
    | --- | --- |
    | Suscripci�n | **Elija su suscripci�n** |
    | Grupo de recursos | **myRGDb** (crear nuevo) |
    | Nombre de la base de datos| **db1** | 
    | | |

3. Junto a la lista desplegable **Servidor**, haga clic en **Crear nuevo** e introduzca esta informaci�n (sustituya **xxxx** en el nombre del servidor por letras y d�gitos de modo que el nombre sea globalmente �nico). Haga clic en **Aceptar** cuando haya terminado.

    | Valor | Valor | 
    | --- | --- |
    | Nombre del servidor | **sqlserverxxxx** (debe ser �nico) | 
    | Inicio de sesi�n del administrador del servidor | **sqluser** |
    | Contrase�a | **Pa$$w0rd1234** |
    | Ubicaci�n | **Este de EE. UU.** |
    | Permitir que los servicios de Azure accedan al servidor| ***Seleccione la casilla*** |
    | | |

   ![Captura de pantalla del panel Servidor y del panel Nuevo servidor con los campos rellenados seg�n la tabla y los botones Revisar + crear y Aceptar resaltados.](../images/0501.png)

4. Vaya a la pesta�a **Redes** y configure los siguientes ajustes (deje los dem�s con sus valores predeterminados) 

    | Valor | Valor | 
    | --- | --- |
    | M�todo de conectividad | **Extremo p�blico** |    
    | Permitir que los servicios y recursos de Azure accedan a este servidor | **S�** |
    | Agregar la direcci�n IP actual del cliente | **No** |
    | | |
    
   ![Captura de pantalla de la pesta�a Redes de la hoja Crear base de datos SQL con la configuraci�n seleccionada seg�n la tabla y el bot�n Revisar + crear resaltado.](../images/0501b.png)

5. Vaya a la pesta�a **Configuraci�n adicional**. Utilizaremos la base de datos de muestra AdventureWorksLT.

    | Valor | Valor | 
    | --- | --- |
    | Use datos existentes | **Muestra** |
    | Intercalaci�n | ***usar valor predeterminado*** |
    | Habilitar Advanced Data Security | **Ahora no** |
    | | |

    ![Captura de pantalla de la pesta�a Configuraci�n adicional de la hoja Crear base de datos SQL con la configuraci�n seleccionada seg�n la tabla y el bot�n Revisar + crear resaltado.](../images/0501c.png)

6. Haga clic en **Revisar + crear** y, a continuaci�n, en **Crear** para implementar y aprovisionar el grupo de recursos, el servidor y la base de datos. La implementaci�n puede tardar de 2 a 5 minutos.

7. Supervise su implementaci�n. 

# Tarea�2: Pruebe la base de datos.

En esta tarea, configuraremos el servidor SQL y ejecutaremos una consulta SQL. 

1. En la hoja **Todos los servicios**, busque y seleccione **Bases de datos SQL** y aseg�rese de que se haya creado la nueva base de datos. Es posible que necesite **Actualizar** la p�gina.

    ![Captura de pantalla de la base de datos SQL y el servidor que se acaban de implementar.](../images/0502.png)

2. Haga clic en la entrada **db1**, que representa la base de datos SQL que ha creado, y en **Editor de consultas (vista previa)**.

3. Inicie la sesi�n como **sqluser** con la contrase�a **Pa$$w0rd1234**.

4. No podr� iniciar la sesi�n. Lea el error con atenci�n y tome nota de la direcci�n IP que debe permitirse a trav�s del firewall. 

    ![Captura de pantalla de la p�gina de inicio de sesi�n del Editor de consultas con un error de direcci�n IP.](../images/0503.png)

5. En la hoja **db1**, haga clic en **Informaci�n general**. 

    ![Captura de pantalla de la p�gina del servidor SQL.](../images/0504.png)

6. En la hoja **Informaci�n general** del servidor SQL, haga clic en **Establecer el firewall del servidor**.

7. Haga clic en **Agregar IP de cliente** (barra de men� superior) para a�adir la direcci�n IP referenciada en el error. Aseg�rese de **guardar** los cambios. 

    ![Captura de pantalla de la p�gina de configuraci�n del firewall del servidor SQL con la nueva regla de IP resaltada.](../images/0506.png)

8. Vuelva a su base de datos SQL y a la p�gina de inicio de sesi�n del **Editor de consultas (vista previa)**. Intente iniciar sesi�n de nuevo como **sqluser** con la contrase�a **Pa$$w0rd1234**. Esta vez deber�a poder hacerlo. Tenga en cuenta que la implementaci�n de la nueva regla de firewall puede tardar un par de minutos. 

9. Una vez que inicie sesi�n correctamente, aparecer� el panel de consultas. Introduzca la siguiente consulta en el panel de editor.

    ```SQL
    SELECT TOP 20 pc.Name as CategoryName, p.name as ProductName
    FROM SalesLT.ProductCategory pc
    JOIN SalesLT.Product p
    ON pc.productcategoryid = p.productcategoryid;
    ```

    ![Captura de pantalla del Editor de consultas con el panel de consultas y los comandos ejecut�ndose correctamente.](../images/0507.png)

10. Haga clic en **Ejecutar** y, luego, revise los resultados de la consulta en el panel **Resultados**. La consulta deber�a ejecutarse correctamente.

    ![Captura de pantalla del panel del Editor de consultas de la base de datos con el c�digo SQL ejecutado con �xito y la salida visible en el panel de resultados.](../images/0508.png)

�Enhorabuena! Ha creado una base de datos SQL en Azure y ha consultado con �xito los datos en esa base de datos.

**Nota**: Para evitar costes adicionales, puede eliminar este grupo de recursos. Busque grupos de recursos, haga clic en su grupo de recursos y, a continuaci�n, haga clic en **Eliminar grupo de recursos**. Compruebe el nombre del grupo de recursos y luego haga clic en **Eliminar**. Supervise las **Notificaciones** para ver c�mo se realiza la eliminaci�n.

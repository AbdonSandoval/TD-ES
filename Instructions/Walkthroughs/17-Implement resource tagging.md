---
wts:
    title: '17: Implementaci�n del etiquetado de recursos'
    module: 'M�dulo 03: Seguridad, privacidad, cumplimiento y confianza'
---
# 17 - Implementar etiquetado de recursos

En este tutorial, crearemos una asignaci�n de directivas que requiera etiquetado, crearemos una cuenta de almacenamiento y probaremos el etiquetado, veremos recursos con una etiqueta espec�fica y quitaremos la directiva de etiquetado.

# Tarea�1: Crear una asignaci�n de directiva

En esta tarea, configuraremos la directiva **Requerir una etiqueta en los recursos** y la asignaremos a nuestra suscripci�n. 

1. Inicie sesi�n en [Azure Portal](https://portal.azure.com).

2. Desde la hoja **Todos los servicios**, busque y seleccione **Directiva**.

3. Despl�cese hacia abajo hasta la secci�n **Creaci�n**, haga clic en **Asignaciones** y luego haga clic en **Asignar directiva** desde la parte superior de la p�gina.

4. Tenga en cuenta que el **�mbito** para nuestra directiva ser� toda la suscripci�n. 

5. Seleccione el bot�n de puntos suspensivos **Definici�n de la pol�tica** (al final del cuadro de texto de la derecha). **Busque** definiciones de directivas que incluyen la **etiqueta** de valor, en el conjunto de resultados, haga clic en la definici�n **Requerir una etiqueta en los recursos**, luego haga clic en **Seleccionar**.

   ![Captura de pantalla del panel Definiciones disponibles con la opci�n Requerir una etiqueta en los recursos seleccionada.](../images/1701.png)

6. En la hoja **Asignar directiva**, en la pesta�a **Par�metros**, escriba **Empresa** para el nombre de la etiqueta. Haga clic en **Revisar + crear** y, luego, en **Crear**.

    **Nota:** Este es un ejemplo simple para demostrar el etiquetado. 

    ![Captura de pantalla del panel Asignar pol�tica con el nombre de etiqueta completado.](../images/1702.png)

7. La asignaci�n de la directiva **Requerir una etiqueta en los recursos** ahora est� implementada. Cuando se crea un recurso, debe incluir una etiqueta con la clave de compa��a.

   ![Captura de pantalla de la directiva: panel de asignaciones con la asignaci�n de ubicaciones permitidas resaltada.](../images/1703.png)

# Tarea�2: Cree una cuenta de almacenamiento para probar el etiquetado requerido

En esta tarea crearemos cuentas de almacenamiento para probar el etiquetado requerido. 

1. En el Azure Portal, desde la hoja **Todos los servicios**, busque y seleccione **Cuentas de almacenamiento** y luego haga clic en **+ A�adir**.

2. En la pesta�a **Datos b�sicos** de la hoja **Crear cuenta de almacenamiento**, complete la siguiente informaci�n (reemplace **xxxx** en el nombre de la cuenta de almacenamiento con letras y d�gitos de modo que el nombre sea globalmente �nico). Deje los valores predeterminados para todo lo dem�s.

    | Configuraci�n | Valor | 
    | --- | --- |
    | Suscripci�n | **Use su suscripci�n** |
    | Grupo de recursos | **myRGTags** (nuevo) |
    | Nombre de la cuenta de almacenamiento | **storageaccountxxxx** |
    | Ubicaci�n | **Este de EE. UU.** |
    | | |

3. Haga clic en **Revisar + Crear**. 

    **Nota:** Estamos probando para ver qu� sucede cuando no se suministra la etiqueta. 

4. Recibir� un mensaje de error de validaci�n. Haga clic en el mensaje **Haga clic aqu� para ver los detalles**. En la hoja **Errores**, en la pesta�a **Resumen**, observe el mensaje de error que indica que la directiva no permite el recurso.

    **Nota:** Si ve la pesta�a Error sin formato, ver� el nombre de etiqueta espec�fico que se necesita. 

    ![Captura de pantalla de rechazado debido a un error de directiva.](../images/1704.png)

5. Cierre el panel de **Error** y haga clic en **Anterior** (parte inferior de la pantalla). Proporcione la informaci�n de etiquetado. 

    | Configuraci�n | Valor | 
    | --- | --- |
    | Nombre de etiqueta | **Compa��a** (puede no estar en la lista desplegable) |
    | Valor de la etiqueta | **Contoso** |
    | | |

6. Haga clic en **Revisar + crear** y verifique que la validaci�n haya sido exitosa. Haga clic en **Crear** para implementar la cuenta de almacenamiento. 

# Tarea�3: Vea todos los recursos con una etiqueta espec�fica

1. En Azure Portal, desde la hoja **Todos los servicios**, busque y seleccione **Etiquetas**.

2. Tenga en cuenta todas las etiquetas y sus valores. Haga clic en la **Compa��a: Contoso** par clave/valor. Esto mostrar� una hoja que muestra la cuenta de almacenamiento reci�n creada, siempre que haya incluido la etiqueta durante su implementaci�n. 

   ![Captura de pantalla de las etiquetas con empresa y contoso seleccionados.](../images/1705.png)

3. En el Portal, muestre la hoja **Todos los recursos**.

4. Haga clic en **A�adir filtro** y a�ada la clave de etiqueta de la **Compa��a** como la categor�a de filtro. Con el filtro aplicado, solo se mostrar� su cuenta de almacenamiento.

    ![Captura de pantalla del filtro Todos los recursos con la compa��a seleccionada.](../images/1706.png)

# Tarea�4 Elimine la asignaci�n de directiva

En esta tarea eliminaremos la directiva **Pedir una etiqueta en los recursos** para que no afecte nuestro trabajo futuro. 

1. En el portal, desde la hoja **Todos los servicios**, busque y seleccione la **Directiva**.

2. Haga clic en la entrada de la directiva **Pedir una etiqueta en los recursos**.

3. Haga clic en **Eliminar asignaci�n** en el panel superior.

4. Confirme que desea eliminar la asignaci�n de directiva en el di�logo **Eliminar asignaci�n** haciendo clic en **S�**

5. Si tiene tiempo, cree otro recurso sin una etiqueta para asegurarse de que la directiva ya no est� vigente.

En este tutorial creamos una asignaci�n de directivas que requer�a etiquetado, creamos una cuenta de almacenamiento y probamos el etiquetado, vimos recursos con una etiqueta espec�fica y eliminamos las directivas de etiquetado.


**Nota**: Para evitar costes adicionales, puede eliminar este grupo de recursos. Busque grupos de recursos, haga clic en su grupo de recursos y, a continuaci�n, haga clic en **Eliminar grupo de recursos**. Compruebe el nombre del grupo de recursos y luego haga clic en **Eliminar**. Supervise las **Notificaciones** para ver c�mo se realiza la eliminaci�n.

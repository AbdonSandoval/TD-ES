---
wts:
    title: '14: Creaci�n de una directiva de Azure'
    module: 'M�dulo 03: Seguridad, privacidad, cumplimiento y confianza'
---
# 14: Crear una directiva de Azure

En este tutorial crearemos una directiva de Azure para restringir la implementaci�n de los recursos de Azure en una ubicaci�n espec�fica.

# Tarea�1: Crear una asignaci�n de directiva

En esta tarea, configuraremos la pol�tica de ubicaci�n permitida y la asignaremos a nuestra suscripci�n. 

1. Inicie sesi�n en [Azure Portal](https://portal.azure.com).

2. Desde la hoja **Todos los servicios**, busque y seleccione **Pol�tica**, bajo la secci�n **Creaci�n**, haga clic en **Definiciones**.  T�mese un momento para revisar la lista de definiciones de las directivas integradas. Por ejemplo, en el men� desplegable **Categor�a** seleccione solo **Calcular**. Tenga en cuenta que la definici�n **SKU de m�quinas virtuales permitidas** le habilita especificar un conjunto de SKU de m�quinas virtuales que su organizaci�n puede implementar.

3. Vuelva a la p�gina **Directiva**, en la secci�n **Creaci�n** y haga clic en **Asignaciones**. Una asignaci�n es una directiva que se ha asignado para que tenga lugar dentro de un alcance espec�fico. Por ejemplo, se podr�a asignar una definici�n al �mbito de la suscripci�n. 

4. Haga clic en **Asignar directiva** en la parte superior de la p�gina **Directiva: Asignaciones**.

5. En la p�gina **Asignar pol�tica**, seleccione el selector de �mbito haciendo clic en los puntos suspensivos.

    ![Captura de pantalla de los puntos suspensivos del selector de �mbito.](../images/1401.png)

6. Aseg�rese de que su suscripci�n est� seleccionada. El nombre de su suscripci�n puede ser diferente. Tenga en cuenta que, opcionalmente, puede definir el �mbito de la directiva a un grupo de recursos. Deje los valores predeterminados y haga clic en **Seleccionar**. 

    **Nota**: Un �mbito determina a qu� recursos o agrupaci�n de recursos se aplica la asignaci�n de directiva. En nuestro caso, podr�amos asignar esta directiva a un grupo de recursos espec�fico. Sin embargo, elegimos asignar la directiva en el nivel de suscripci�n. Tenga en cuenta que los recursos se pueden excluir en funci�n de la configuraci�n del �mbito. Las exclusiones son opcionales.

    ![Captura de pantalla del panel �mbito con valores de campo rellenados y el bot�n Seleccionar resaltado. ](../images/1402.png)

7. Seleccione el bot�n de puntos suspensivos **Definici�n de directiva**. En el cuadro **Buscar** escriba **ubicaci�n**, haga clic en la definici�n **Ubicaciones permitidas** y luego en **Seleccionar**.

    **Nota**: Esta definici�n de directiva de **Ubicaciones permitidas** especificar� una ubicaci�n en la que se deben implementar todos los recursos. Si se elige una ubicaci�n diferente, no se permitir� la implementaci�n. Para obtener m�s informaci�n, vea la p�gina [Muestras de pol�tica de Azure](https://docs.microsoft.com/es-es/azure/governance/policy/samples/index).

   ![Captura de pantalla del panel Definiciones disponibles con varios campos resaltados y la opci�n Auditar m�quinas virtuales que no usan discos administrados seleccionada.](../images/1403.png)

8.  En el panel **Asignar directiva**, cambie a la pesta�a **Par�metros**, haga clic en la flecha al final del cuadro **Ubicaciones permitidas** y de la siguiente lista elija **Jap�n Occidental**. Deje todos los dem�s valores como est�n y haga clic en **Revisar + crear**, y luego en **Crear**.

    ![Captura de pantalla del panel Asignar directiva con varios campos rellenados junto con la ubicaci�n Jap�n Occidental completada y el bot�n de asignaci�n resaltado.](../images/1404.png)

9. La asignaci�n de pol�tica de **Ubicaciones permitidas** ahora aparece en el panel **Pol�tica: Asignaciones** y ahora est� implementada, aplicando la pol�tica en el nivel de alcance que especificamos (nivel de suscripci�n).

# Tarea�2: Prueba de la directiva de Ubicaci�n permitida

En esta tarea probaremos la directiva de Ubicaci�n permitida. 

1. En el Azure Portal, desde la hoja **Todos los servicios**, busque y seleccione **Cuentas de almacenamiento** y luego haga clic en **+ A�adir**.

2. Configure la cuenta de almacenamiento (reemplace **xxxx** en el nombre de la cuenta de almacenamiento con letras y d�gitos de modo que el nombre sea �nico a nivel global). Deje los valores predeterminados para todo lo dem�s. 

    | Valor | Valor | 
    | --- | --- |
    | Suscripci�n | **Use su suscripci�n** |
    | Grupo de recursos | **myRGPolicy** (crear nuevo) |
    | Nombre de la cuenta de almacenamiento | **storageaccountxxxx** |
    | Ubicaci�n | **Este de EE. UU.** |
    | | |

3. Haga clic en **Revisar + crear** y luego haga clic en **Crear**. 

4. Recibir� el error de implementaci�n fallida que indica que la directiva rechaz� el recurso, incluido el nombre de la directiva de **Ubicaciones permitidas**.

# Tarea�3: Elimine la asignaci�n de directiva

En esta tarea, quitaremos la asignaci�n y prueba de la directiva de ubicaci�n permitida. 

Eliminaremos la asignaci�n de directivas para asegurarnos de que no estemos bloqueados en ning�n trabajo futuro que deseemos hacer.

1. Desde la hoja **Todos los servicios**, busque y seleccione **Directiva** y luego haga clic en la directiva **Ubicaciones permitidas**.

    **Nota**: En la hoja **Directiva** puede ver el estado de cumplimiento de las diversas directivas que ha asignado.

    **Nota**: La pol�tica de ubicaci�n permitida puede mostrar recursos no compatibles. Si es as�, estos son recursos creados antes de la asignaci�n de la pol�tica.

2. Haga clic en **Eliminar asignaci�n** en el panel superior.

   ![Captura de pantalla del elemento de men� Eliminar asignaci�n.](../images/1407.png)

3. Confirme que desea eliminar la asignaci�n de directiva en el di�logo **Eliminar asignaci�n** haciendo clic en **S�**

4. Trate de crear otra cuenta de almacenamiento para asegurarse de que la directiva ya no est� vigente.

    **Nota**: Entre las situaciones comunes donde la directiva de **Ubicaciones permitidas** puede ser �til se incluyen las siguientes: 
    - *Seguimiento de costes*: Podr�a tener diferentes suscripciones para diferentes ubicaciones regionales. La directiva garantizar� que todos los recursos se implementen en la regi�n prevista para ayudar con el seguimiento de costes. 
    - *Cumplimiento de Seguridad y residencia de datos*: Tambi�n podr�a tener requisitos de residencia de datos, crear suscripciones por cliente o carga de trabajo espec�fica y definir que todos los recursos deban implementarse en un centro de datos particular para garantizar los requisitos de cumplimiento de seguridad y datos.

�Enhorabuena! Ha creado una directiva de Azure para restringir la implementaci�n de los recursos de Azure en un centro de datos particular.

**Nota**: Para evitar costes adicionales, puede eliminar este grupo de recursos. Busque grupos de recursos, haga clic en su grupo de recursos y, a continuaci�n, haga clic en **Eliminar grupo de recursos**. Compruebe el nombre del grupo de recursos y luego haga clic en **Eliminar**. Supervise las **Notificaciones** para ver c�mo se realiza la eliminaci�n.
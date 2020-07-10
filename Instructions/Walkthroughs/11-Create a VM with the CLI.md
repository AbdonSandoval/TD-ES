---
wts:
    title: '11 - Crear una VM con la CLI'
    module: 'M�dulo 02: Servicios principales de Azure'
---
# 11 - Crear una VM con la CLI

En este tutorial, configuraremos Cloud Shell, utilizaremos la CLI de Azure para crear un grupo de recursos y una m�quina virtual, y revisaremos las recomendaciones de Azure Advisor. 

# Tarea�1: Configurar el Cloud Shell

En esta tarea, configuraremos Cloud Shell. 

1. Inicie sesi�n en [Azure Portal](https://portal.azure.com).

2. Desde Azure Portal, abra el **Azure Cloud Shell** haciendo clic en el icono de la esquina superior derecha de Azure Portal.

    ![Captura de pantalla del icono de Azure Portal Azure Cloud Shell.](../images/1002.png)

3. Si ya ha utilizado Cloud Shell, contin�e con la siguiente tarea. 

4. Cuando se le solicite seleccionar **Bash** o **PowerShell**, seleccione **Bash**. 

5. Cuando se le solicite, haga clic en **Crear almacenamiento**y espere a que Azure Cloud Shell se inicialice. 

# Tarea�2: Creaci�n de un grupo de recursos y una m�quina virtual.

En esta tarea, usaremos la CLI de Azure para crear un grupo de recursos y una m�quina virtual.  

1. Aseg�rese de que **Bash** est� seleccionado en el men� desplegable superior izquierdo del panel Cloud Shell (y si no, selecci�nelo).

    ![Captura de pantalla de Azure Portal Azure Cloud Shell con el men� desplegable Bash resaltado.](../images/1002a.png)

2. En la sesi�n Bash, dentro del panel Cloud Shell, cree un nuevo grupo de recursos. 

    ```cli
    az group create --name myRGCLI --location EastUS
    ```

3. Verifique que se haya creado el grupo de recursos.

    ```cli
    az group list --output table
    ```

4. Crear una nueva m�quina virtual. Aseg�rese de que cada l�nea, excepto la �ltima, vaya seguida del car�cter de barra diagonal inversa (`\`). Si escribe el comando completo en la misma l�nea, no utilice caracteres de barra invertida. 

    ```cli
    az vm create \
    --name myVMCLI \
    --resource-group myRGCLI \
    --image UbuntuLTS \
    --location EastUS \
    --admin-username azureuser \
    --admin-password Pa$$w0rd1234
    ```

    >**Nota**: Si est� utilizando la l�nea de comandos en un equipo Windows, reemplace el car�cter de barra diagonal inversa (`\`) con el car�cter de intercalaci�n (`^`).
    
    **Nota**: El comando tardar� entre 2 y 3 minutos en completarse. El comando crear� una m�quina virtual y varios recursos asociados, como recursos de seguridad, almacenamiento y redes. No contin�e con el siguiente paso hasta que se complete la implementaci�n de la m�quina virtual. 

5. Cuando el comando termine de ejecutarse, en la ventana del explorador cierre el panel Cloud Shell.

6. En Azure Portal, busque **Virtual Machines** y verifique que **myVMCLI** se est� ejecutando.

    ![Captura de pantalla de la p�gina de Virtual Machines con myVMPS en estado de ejecuci�n.](../images/1101.png)


# Tarea�3: Ejecutar comandos en Cloud Shell

En esta tarea, practicaremos la ejecuci�n de comandos de CLI desde Cloud Shell. 

1. Desde Azure Portal, abra el **Azure Cloud Shell** haciendo clic en el icono de la esquina superior derecha de Azure Portal.

2. Aseg�rese de que **Bash** est� seleccionado en el men� desplegable superior izquierdo del panel Cloud Shell.

3. Recupere informaci�n sobre la m�quina virtual que aprovision�, incluido el nombre, el grupo de recursos, la ubicaci�n y el estado. Observe que el PowerState se est� **ejecutando**.

    ```cli
    az vm show --resource-group myRGCLI --name myVMCLI --show-details --output table 
    ```

4. Reinicie la m�quina virtual. Observe el mensaje de que la facturaci�n contin�a hasta que la m�quina virtual se desasigna. 

    ```cli
    az vm stop --resource-group myRGCLI --name myVMCLI
    ```

5. Compruebe el estado de su m�quina virtual. El PowerState ahora deber�a estar **parado**.

    ```cli
    az vm show --resource-group myRGCLI --name myVMCLI --show-details --output table 
    ```

# Tarea�4 Revise las recomendaciones de Azure Advisor

En esta tarea, revisaremos las recomendaciones de Azure Advisor.

   **Nota:** Si ha completado el laboratorio anterior (Crear una VM con PowerShell), entonces ya ha realizado esta tarea. 

1. Desde la hoja **Todos los servicios**, busque y seleccione **Advisor**. 

2. Sobre la hoja **Advisor**, seleccione **Visi�n general**. Las recomendaciones de aviso est�n agrupadas por Alta disponibilidad, Seguridad, Rendimiento y Coste. 

    ![Captura de pantalla de la p�gina Visi�n general de Advisor. ](../images/1103.png)

3. Seleccione **Todas las recomendaciones** y t�mese un tiempo para ver cada recomendaci�n y acciones sugeridas. 

    **Nota:** Dependiendo de sus recursos, sus recomendaciones ser�n diferentes. 

    ![Captura de pantalla de la p�gina Todas las recomendaciones de Advisor. ](../images/1104.png)

4. Tenga en cuenta que puede descargar las recomendaciones como un archivo CSV o PDF. 

5. Tenga en cuenta que puede crear alertas. 

6. Si tiene tiempo, contin�e experimentando con la CLI de Azure. 

�Enhorabuena! Ha configurado Cloud Shell, ha creado una m�quina virtual con la CLI de Azure, ha practicado con los comandos de la CLI de Azure y ha visto las recomendaciones de Advisor.

**Nota**: Para evitar costes adicionales, puede eliminar este grupo de recursos. Busque grupos de recursos, haga clic en su grupo de recursos y, a continuaci�n, haga clic en **Eliminar grupo de recursos**. Compruebe el nombre del grupo de recursos y luego haga clic en **Eliminar**. Supervise las **Notificaciones** para ver c�mo se realiza la eliminaci�n.

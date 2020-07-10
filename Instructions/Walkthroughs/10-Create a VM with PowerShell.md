---
wts:
    title: '10 - Crear una VM con PowerShell'
    module: 'M�dulo 02: Servicios principales de Azure'
---
# 10 - Crear una VM con PowerShell

En este tutorial, configuraremos Cloud Shell, utilizaremos el m�dulo Azure PowerShell para crear un grupo de recursos y una m�quina virtual, y revisaremos las recomendaciones de Azure Advisor. 

# Tarea�1: Configurar el Cloud Shell

En esta tarea, configuraremos Cloud Shell. 

1. Inicie sesi�n en [Azure Portal](https://portal.azure.com).

2. Desde Azure Portal, abra el **Azure Cloud Shell** haciendo clic en el icono de la esquina superior derecha de Azure Portal.

    ![Captura de pantalla del icono de Azure Portal Azure Cloud Shell.](../images/1002.png)

3. Si ya ha utilizado Cloud Shell, contin�e con la siguiente tarea. 

4. Cuando se le solicite seleccionar **Bash** o **PowerShell**, seleccione **PowerShell**. 

5. Cuando se le solicite, haga clic en **Crear almacenamiento**y espere a que Azure Cloud Shell se inicialice. 

# Tarea�2: Crear un grupo de recursos y una m�quina virtual.

En esta tarea, utilizaremos PowerShell para crear un grupo de recursos y una m�quina virtual.  

1. Aseg�rese de que **PowerShell** est� seleccionado en el men� desplegable superior izquierdo del panel Cloud Shell.

2. En la sesi�n de PowerShell, dentro del panel Cloud Shell, cree un nuevo grupo de recursos. 

    ```PowerShell
    New-AzResourceGroup -Name myRGPS -Location EastUS
    ```

3. Verifique su nuevo grupo de recursos. 

    ```PowerShell
    Get-AzResourceGroup | Format-Table
    ```

4. Cree una m�quina virtual. Cuando se le solicite, proporcione el nombre de usuario (**azureuser**) y la contrase�a (**Pa$$w0rd1234**) que se configurar� como la cuenta de administrador local en esas m�quinas virtuales. Aseg�rese de incluir los caracteres de marca (`) al final de cada l�nea, excepto en la �ltima (no debe haber ning�n car�cter de marca si escribe el comando completo en una sola l�nea).

    ```PowerShell
    New-AzVm `
    -ResourceGroupName "myRGPS" `
    -Name "myVMPS" `
    -Location "East US" `
    -VirtualNetworkName "myVnetPS" `
    -SubnetName "mySubnetPS" `
    -SecurityGroupName "myNSGPS" `
    -PublicIpAddressName "myPublicIpPS"
    ```

5. Cierre el panel de Cloud Shell de la sesi�n de PowerShell.

6. En Azure Portal, busque **Virtual Machines** y verifique que **myVMPS** se est� ejecutando. Este proceso puede durar unos minutos.

    ![Captura de pantalla de la p�gina de Virtual Machines con myVMPS en estado de ejecuci�n.](../images/1001.png)

7. Acceda a la nueva m�quina virtual y revise las configuraciones de Descripci�n general y Redes para comprobar que su informaci�n se haya implementado correctamente. 

# Tarea�3: Ejecutar comandos en Cloud Shell

En esta tarea, practicaremos la ejecuci�n de comandos de PowerShell desde Cloud Shell. 

1. Desde Azure Portal, abra el **Azure Cloud Shell** haciendo clic en el icono de la esquina superior derecha de Azure Portal.

2. Aseg�rese de que **PowerShell** est� seleccionado en el men� desplegable superior izquierdo del panel Cloud Shell.

3. Recupere informaci�n sobre su m�quina virtual, incluido el nombre, el grupo de recursos, la ubicaci�n y el estado. Observe que el PowerState se est� **ejecutando**.

    ```PowerShell
    Get-AzVM -name myVMPS -status | Format-Table -autosize
    ```

4. Reinicie la m�quina virtual. Cuando se le solicite, confirme (S�) a la acci�n. 

    ```PowerShell
    Stop-AzVM -ResourceGroupName myRGPS -Name myVMPS
    ```

5. Verifique el estado de su m�quina virtual. Ahora PowerState deber�a estar **desasignado**. Tambi�n puede verificar el estado de la m�quina virtual en el portal. 

    ```PowerShell
    Get-AzVM -name myVMPS -status | Format-Table -autosize
    ```

# Tarea�4 Revise las recomendaciones de Azure Advisor

**Nota:** Esta misma tarea se encuentra en el laboratorio Crear una VM con la CLI de Azure. 

En esta tarea, revisaremos las recomendaciones de Azure Advisor para nuestra m�quina virtual. 

1. Desde la hoja **Todos los servicios**, busque y seleccione **Advisor**. 

2. Sobre la hoja **Advisor**, seleccione **Visi�n general**. Las recomendaciones de aviso est�n agrupadas por Alta disponibilidad, Seguridad, Rendimiento y Coste. 

    ![Captura de pantalla de la p�gina Visi�n general de Advisor. ](../images/1003.png)

3. Seleccione **Todas las recomendaciones** y t�mese un tiempo para ver cada recomendaci�n y acciones sugeridas. 

    **Nota:** Dependiendo de sus recursos, sus recomendaciones ser�n diferentes. 

    ![Captura de pantalla de la p�gina Todas las recomendaciones de Advisor. ](../images/1004.png)

4. Tenga en cuenta que puede descargar las recomendaciones como un archivo CSV o PDF. 

5. Tenga en cuenta que puede crear alertas. 

6. Si tiene tiempo, contin�e experimentando con Azure PowerShell. 

�Enhorabuena! Ha configurado Cloud Shell, creado una m�quina virtual con PowerShell, practicado con comandos de PowerShell y visto las recomendaciones de Advisor.

**Nota**: Para evitar costes adicionales, puede eliminar este grupo de recursos. Busque grupos de recursos, haga clic en su grupo de recursos y, a continuaci�n, haga clic en **Eliminar grupo de recursos**. Compruebe el nombre del grupo de recursos y luego haga clic en **Eliminar**. Supervise las **Notificaciones** para ver c�mo se realiza la eliminaci�n.

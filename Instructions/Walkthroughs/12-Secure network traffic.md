---
wts:
    title: '12 - Tr�fico de red segura'
    module: 'M�dulo 03: Seguridad, privacidad, cumplimiento y confianza'
---
# 12 - Tr�fico de red segura

En este tutorial, configuraremos un grupo de seguridad de red.

# Tarea�1: Crear una m�quina virtual

En esta tarea, crearemos una m�quina virtual de Windows Server 2019 Datacenter. 

1. Inicie sesi�n en [Azure Portal](https://portal.azure.com).

2. Desde la hoja **Todos los servicios**, busque y seleccione **M�quinas virtuales** y luego haga clic en **+ Agregar**.

3. En la pesta�a **Datos b�sicos**, complete la siguiente informaci�n (deje los valores predeterminados para todo lo dem�s):

    | Configuraci�n | Valores |
    |  -- | -- |
    | Suscripci�n | **Elija su suscripci�n**|
    | Grupo de recursos | **myRGSecure** (crear nuevo) |
    | Nombre de la m�quina virtual | **SimpleWinVM** |
    | Ubicaci�n | **Este de EE. UU.**|
    | Imagen | **Windows Server 2019 Datacenter**|
    | Tama�o | **Est�ndar D2s v3**|
    | Nombre de usuario de la cuenta de administrador | **azureuser** |
    | Contrase�a de cuenta de administrador | **Pa$$w0rd1234**|
    | Reglas de puerto de entrada | **Ninguna**|
    | | |

4. Cambie a la pesta�a **Redes** y configure la siguiente configuraci�n:

    | Configuraci�n | Valores |
    | -- | -- |
    | Grupo de seguridad de red NIC | **Ninguna**|
    | | |

5. Cambie a la pesta�a **Administraci�n** y en la secci�n **Supervisi�n**, seleccione la siguiente configuraci�n:

    | Configuraci�n | Valores |
    | -- | -- |
    | Diagn�stico de arranque | **Off**|
    | | |

6. Deje los valores predeterminados restantes y luego haga clic en el bot�n **Revisar + crear**, en la parte inferior de la p�gina.

7. Una vez que se pasa la validaci�n, haga clic en el bot�n **Crear**. La implementaci�n de la m�quina virtual puede tardar unos cinco minutos.

8. Supervisar la implementaci�n. La creaci�n del grupo de recursos y la m�quina virtual puede tomar varios minutos. 

9. Desde la hoja de implementaci�n o desde el �rea Notificaci�n, haga clic en **Ir al recurso**. 

10. Sobre la hoja de la m�quina virtual **SimpleWinVM**, haga clic en **Redes**, revise la pesta�a de **Reglas de puerto de entrada** y tenga en cuenta que no hay un grupo de seguridad de red asociado con la interfaz de red de la m�quina virtual o la subred a la que est� conectada la interfaz de red.

    **Nota**: Identifique el nombre de la interfaz de red. Lo necesitar� en la pr�xima tarea.

# Tarea�2: Crear un grupo de seguridad de red

En esta tarea, crearemos un grupo de seguridad de red y lo asociaremos con la interfaz de red.

1. Desde la hoja **Todos los servicios**, busque y seleccione **Grupos de seguridad de red** y luego haga clic en **+ A�adir**

2. Sobre la pesta�a **Datos b�sicos** de la hoja **Crear grupo de seguridad de red**, especifique la siguiente configuraci�n.

    | Configuraci�n | Valor |
    | -- | -- |
    | Suscripci�n | **Elija su suscripci�n** |
    | Grupo de recursos | **myRGSecure** |
    | Nombre | **myNSGSecure** |
    | Regi�n | **Este de EE. UU.**  |
    | | |

3. Haga clic en **Revisar + crear** y luego, despu�s de la validaci�n, haga clic en  **Crear**.

4. Despu�s de crear el NSG, haga clic en **Ir al recurso**.

5. Debajo de **Configuraci�n**, haga clic en **Interfaces de red** y luego en **+ Asociar**.

6. Seleccione la interfaz de red que identific� en la tarea anterior. 

# Tarea�3: Configure una regla de puerto de seguridad entrante para permitir RDP

En esta tarea, permitiremos el tr�fico RDP a la m�quina virtual configurando una regla de puerto de seguridad entrante. 

1. En Azure Portal, navegue hasta la hoja de la m�quina virtual **SimpleWinVM**. 

2. Sobre el panel de **Visi�n general**, haga clic en **Conectar**.

3. Intente conectarse a la m�quina virtual mediante RDP. Por defecto, el grupo de seguridad de red no permite RDP. Cierre la ventana de error. 

    ![Captura de pantalla del mensaje de error de que la conexi�n de la m�quina virtual ha fallado.](../images/1201.png)

4. En la hoja de la m�quina virtual, despl�cese hacia abajo hasta la secci�n **Configuraci�n**, haga clic en **Redes** y observe las reglas de entrada para el grupo de seguridad de red **myNSGSecure (conectado a la interfaz de red: myVMNic)** niega todo el tr�fico entrante, excepto el tr�fico dentro de la red virtual y las sondas de equilibrador de carga.

5. Sobre la pesta�a **Reglas de puerto de entrada**, haga clic en **Agregar regla de puerto de entrada** . Haga clic en **A�adir** cuando haya terminado. 

    | Configuraci�n | Valor |
    | -- | -- |
    | Origen | **Cualquiera**|
    | Rangos de puertos de origen | **\*** |
    | Destino | **Cualquiera** |
    | Rangos de puertos de destino | **3389** |
    | Protocolo | **TCP** |
    | Acci�n | **Permitir** |
    | Prioridad | **300** |
    | Nombre | **AllowRDP** |
    | | |

6. Espere a que se aprovisione la regla e intente nuevamente RDP en la m�quina virtual. Esta vez deber�a tener �xito. Recuerde que el usuario es **azureuser** y la contrase�a es **Pa$$w0rd1234**.

# Tarea�4 Configure una regla de puerto de seguridad saliente para denegar el acceso a Internet

En esta tarea, crearemos una regla de puerto saliente NSG que denegar� el acceso a Internet y luego la probaremos para asegurarnos de que la regla funciona.

1. Contin�e en su sesi�n de m�quina virtual RDP. 

2. Despu�s de que la m�quina arranque, abra el explorador de **Internet Explorer**. 

3. Compruebe que puede acceder **https://www.bing.com** y luego cierre Internet Explorer. Deber� trabajar a trav�s de las ventanas emergentes de seguridad mejorada de IE. 

    **Nota**: Ahora configuraremos una regla para denegar el acceso saliente a Internet. 

4. En Azure Portal, vuelva a la hoja de la m�quina virtual **SimpleWinVM**. 

5. Debajo de **Configuraciones**, haga clic en **Redes** y, a continuaci�n, en **Reglas de puerto de salida**.

6. Observe que hay una regla, **AllowInternetOutbound**. Esta es una regla predeterminada y no se puede eliminar. 

7. Haga clic en **Agregar regla de puerto de salida**, a la derecha del grupo de seguridad de red **myNSGSecure (conectado a la interfaz de red: myVMNic)** y configure una nueva regla de seguridad saliente con una prioridad m�s alta que denegar� el tr�fico de Internet. Seleccione **A�adir** cuando haya acabado. 

    | Configuraci�n | Valor |
    | -- | -- |
    | Origen | **Cualquiera**|
    | Rangos de puertos de origen | **\*** |
    | Destino | **Etiqueta de servicio** |
    | Etiqueta de servicio de destino | **Internet** |
    | Rangos de puertos de destino | **\*** |
    | Protocolo | **TCP** |
    | Acci�n | **Denegar** |
    | Prioridad | **4000** |
    | Nombre | **DenegarInternet** |
    | | |

8. Vuelva a su sesi�n RDP. 

9. Visite **https://www.microsoft.com**. La p�gina no debe mostrarse. Es posible que deba trabajar a trav�s de ventanas emergentes de seguridad mejoradas de IE adicionales.  

**Nota**: Para evitar costes adicionales, puede eliminar este grupo de recursos. Busque grupos de recursos, haga clic en su grupo de recursos y, a continuaci�n, haga clic en **Eliminar grupo de recursos**. Compruebe el nombre del grupo de recursos y luego haga clic en **Eliminar**. Supervise las **Notificaciones** para ver c�mo se realiza la eliminaci�n.

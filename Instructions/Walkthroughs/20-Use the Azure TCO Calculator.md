---
wts:
    title: '20: Uso de la calculadora de TCO de Azure'
    module: 'M�dulo 4: precios y soporte t�cnico de Azure'
---
# 20 - Usar la calculadora de TCO de Azure


En este tutorial usar� la Calculadora de costo total de propiedad (TCO) para generar un informe de comparaci�n de costes para un entorno local.

**Nota**: En este tutorial, se proporcionan definiciones de ejemplo de la infraestructura local y las cargas de trabajo para un centro de datos t�pico. Para crear un informe de la Calculadora de TCO, use las definiciones de ejemplo o proporcione detalles de su infraestructura local y sus cargas de trabajo *reales*.

# Tarea�1: Configurar la calculadora de TCO

En esta tarea a�adiremos informaci�n de infraestructura a la calculadora. 

1. En el explorador navegue hasta la p�gina [Calculadora de costo total de propiedad (TCO)](https://azure.microsoft.com/es-es/pricing/tco/calculator/).

2. Para a�adir detalles de su infraestructura de servidor local, haga clic en **+�A�adir carga de trabajo del servidor** en el panel **Definir cargas de trabajo**.

    | Configuraci�n | Valor |
    | -- | -- |
    | Nombre | **Servidores: VM de Windows** |
    | Carga de trabajo | **Servidor Windows/Linux** |
    | Entorno | **Virtual Machines** |
    | Sistema operativo | **Windows** |  
    | VM | **50** |
    | Virtualizaci�n | **Hyper-V** |
    | N�cleo(s) | **8**|
    | RAM (GB) | **16** |
    | Optimizar por | **CPU** |
    | Windows Server 2008/2008 R2 | **Apagado** |
    | | |

3. Seleccione **+�A�adir carga de trabajo del servidor** para hacer una fila para una definici�n de cargas de trabajo del servidor nueva. 

    | Configuraci�n | Valor |
    | -- | -- |
    | Nombre | **Servidores: VM de Linux** |
    | Carga de trabajo | **Servidor Windows/Linux** |
    | Entorno | **Virtual Machines** |
    | Sistema operativo | **Linux** |  
    | VM | **50** |
    | Virtualizaci�n | **VMware** |
    | N�cleo(s) | **8**|
    | RAM (GB) | **16** |
    | Optimizar por | **CPU** |
    | Windows Server 2008/2008 R2 | **Apagado** |
    | | |

4. En el panel **Almacenamiento**, haga clic en **Agregar almacenamiento**.

    | Configuraci�n | Valor |
    | -- | -- |
    | Nombre | **Almacenamiento del servidor** |
    | Tipo de almacenamiento | **Disco local/SAN** |
    | Tipo de disco | **HDD** |
    | Capacidad | **60�TB** |  
    | Copia de seguridad | **120�TB** |
    | Archivo | **0�TB** |
    | | |

5. En el panel **Redes**, agregue el ancho de banda. 

    | Configuraci�n | Valor |
    | -- | -- |
    | Ancho de banda de salida | 15�TB|
    | | |

6. Haga clic en **Siguiente**.

7. Explore las opciones y realice los ajustes que necesite. 

    | Configuraci�n | Valor |
    | -- | -- |
    | Divisa | **Euro** |
    | | |

8. Haga clic en **Siguiente**.

# Tarea�2: Revisar los resultados y guardar una copia

En esta tarea revisaremos las recomendaciones de ahorro de costes y descargaremos un informe. 

1. Revise las recomendaciones y visualizaciones de ahorro de Azure.

    | Configuraci�n | Valor |
    | -- | -- |
    | Per�odo| **3�a�os** |
    | Regi�n | **Norte de Europa** |
    | | |


2. Para modificar la informaci�n que proporcion�, vaya al final de la p�gina y haga clic en **Atr�s**. 

3. Para guardar o imprimir una copia en PDF del informe, haga clic en **Descargar**.

    ![Captura de pantalla del panel de informes de la calculadora de TCO en Azure. Los campos de entrada resaltados y completados indican c�mo establecer el per�odo de la calculadora de TCO en tres�a�os y la regi�n en el Norte de Europa. Un gr�fico muestra el costo de la infraestructura local y las cargas de trabajo compensadas frente al costo reducido de usar Azure.](../images/2001.png)

�Enhorabuena! Ha utilizado la Calculadora de TCO para generar un informe de comparaci�n de costos para un entorno local.

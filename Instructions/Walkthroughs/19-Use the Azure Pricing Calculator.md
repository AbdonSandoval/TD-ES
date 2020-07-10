---
wts:
    title: '19: Uso de la calculadora de precios de Azure'
    module: 'M�dulo 4: precios y soporte t�cnico de Azure'
---
# 19 - Usar la calculadora de precios

En este tutorial, utilizaremos la Calculadora de precios de Azure para generar una estimaci�n de costes para una m�quina virtual Azure y recursos de red relacionados.

# Tarea�1: Configurar la calculadora de precios

En esta tarea, calcularemos el coste de una infraestructura de muestra con la Calculadora de precios de Azure. 

**Nota**: Para crear una estimaci�n de la Calculadora de precios de Azure, este tutorial ofrece configuraciones de ejemplo para la VM y recursos relacionados. Use estas configuraciones de ejemplo, o bien proporcione a la Calculadora de precios de Azure detalles de sus requisitos de recursos *reales*.

1. En el explorador, navegue hasta la p�gina web [Calculadora de precios de Azure](https://azure.microsoft.com/es-es/pricing/calculator/).

2. Para a�adir detalles de la configuraci�n de su VM, haga clic en **Maquinas virtuales** en la pesta�a **Productos**. Despl�cese hacia abajo para ver los detalles de la m�quina virtual. 

3. Reemplace el texto **Su estimaci�n** y **Virtual Machines** por nombres m�s descriptivos de su estimaci�n de la Calculadora de precios de Azure y de la configuraci�n de su m�quina virtual. El ejemplo de este tutorial usa **Estimaci�n de mi calculadora de precios** para la estimaci�n y **Windows VM** para la configuraci�n de la m�quina virtual.

   ![Captura de pantalla del �rea de configuraci�n de la m�quina virtual en la p�gina web de estimaci�n de la calculadora de precios de Azure. El nombre de la estimaci�n y el nombre de la configuraci�n de VM resaltados indican c�mo agregar un nombre de estimaci�n y un nombre de configuraci�n de VM a una estimaci�n de la calculadora de precios de Azure.](../images/1901.png)

4. Modifique la configuraci�n de VM predeterminada.

    | Regi�n | Sistema operativo | Tipo |
    |------|----------------|----|
    | Norte de Europa | Windows | (Solo sistema operativo) |
    | | |

    | Nivel | Instancia |
    |----|--------|
    | Est�ndar | A2: 2 n�cleos, 3,5 GB de RAM, 135 GB de almacenamiento temporal |
    | | |

   ![Captura de pantalla del �rea de configuraci�n de la m�quina virtual en la p�gina web de estimaci�n de la calculadora de precios de Azure. Los ejemplos resaltados de los valores de propiedad de configuraci�n de VM escritos por el usuario indican c�mo especificar una configuraci�n de VM dentro de una estimaci�n de la calculadora de precios de Azure.](../images/1902.png)

    **Nota**: Las especificaciones y los precios de la instancia de VM pueden ser diferentes a los de este ejemplo. Siga este tutorial eligiendo una instancia que coincida lo m�s posible con el ejemplo. Para ver los detalles sobre las diferentes opciones de productos de VM, elija **Detalles del producto** en el men� **M�s informaci�n** de la derecha.

5. Ajuste la **Opci�n de facturaci�n** en **Paga por uso**.

   ![Captura de pantalla del �rea de opciones de facturaci�n de VM en la p�gina web de estimaci�n de la calculadora de precios de Azure. La opci�n de facturaci�n de pago por uso resaltada indica c�mo especificar una opci�n de facturaci�n para una m�quina virtual dentro de una estimaci�n de la calculadora de precios de Azure.](../images/1903.png)

6. En Azure, un mes se define como 730 horas. Si su VM necesita estar disponible el 100 por ciento del tiempo cada mes, establezca el valor de horas por mes en `730`. El ejemplo de este tutorial necesita que una VM est� disponible el 50 por ciento del tiempo cada mes.

    Deje el n�mero de m�quinas virtuales establecido en `1` y cambie el valor de las horas por mes a `365`.

   ![Captura de pantalla del �rea de opciones de facturaci�n de VM en la p�gina web de estimaci�n de la calculadora de precios de Azure. El n�mero resaltado de instancias de m�quinas virtuales y las opciones de horas por mes indican c�mo especificar el n�mero de instancias y horas por mes para una m�quina virtual dentro de una estimaci�n de la calculadora de precios de Azure.](../images/1904.png)

7. En el panel **Discos de sistema operativo administrados**, modifique la configuraci�n del almacenamiento de VM predeterminada.

    | Nivel | Tama�o del disco | N�mero de discos | Instant�nea | Transacciones de almacenamiento |
    | ---- | --------- | --------------- | -------- | -------------------- |
    | HDD est�ndar | S30: 1024 GiB | 1 | Apagado | 10.000 |

   ![Captura de pantalla del �rea de opciones de Discos de SO administrados dentro de la p�gina web de estimaci�n de la calculadora de precios de Azure. Las opciones destacadas de tipo de nivel, tama�o de disco, cantidad de discos y cantidad de transacciones de almacenamiento indican c�mo especificar una configuraci�n de almacenamiento para una VM dentro de una estimaci�n de la calculadora de precios de Azure.](../images/1905.png)

8. Para a�adir el ancho de banda de red a su estimaci�n, vaya a la parte superior de la p�gina web de la Calculadora de precios de Azure. En el men� de productos que se encuentra a la izquierda, haga clic en **Redes** y luego en el icono de **Banda ancha**. En el cuadro de di�logo de mensaje **Ancho de banda a�adido**, haga clic en **Ver**.

   ![Captura de pantalla del �rea de productos de redes dentro de la p�gina web de la calculadora de precios de Azure. Los iconos resaltados de redes, a�adir ancho de banda y ver ancho de banda indican c�mo a�adir y ver detalles de la configuraci�n de ancho de banda de redes en una estimaci�n de la calculadora de precios de Azure.](../images/1906.png)

9. A�ada un nombre para la configuraci�n de ancho de banda de su m�quina virtual. Este ejemplo de tutorial utiliza el nombre **Ancho de banda: Windows VM**. Modifique la configuraci�n de ancho de banda predeterminada a�adiendo los siguientes detalles.

    | Regi�n | Cantidad de transferencia de datos salientes de la Zona 1 |
    | ------ | -------------------------------------- |
    | Norte de Europa | 50 GB |

   ![Captura de pantalla del �rea de configuraci�n del ancho de banda de la red dentro de la p�gina web de estimaci�n de la calculadora de precios de Azure. Los ejemplos resaltados de valores de propiedad de ancho de banda ingresados por el usuario indican c�mo especificar una configuraci�n de ancho de banda para una m�quina virtual dentro de una estimaci�n de la calculadora de precios de Azure.](../images/1907.png)

10. Para agregar una Application�Gateway, regrese a la parte superior de la p�gina web de la Calculadora de precios de Azure. En el men� de productos **Redes**, haga clic en el icono de **Application Gateway**. En el cuadro de di�logo de mensaje de **Application�Gateway**, haga clic en **Ver**.

    ![Captura de pantalla del �rea de productos de redes dentro de la p�gina web de la calculadora de precios de Azure. Los iconos resaltados de Redes, Agregar Application�Gateway y Ver Application�Gateway, indican c�mo agregar y ver detalles de la configuraci�n de Application�Gateway en una estimaci�n de la Calculadora de precios de Azure.](../images/1908.png)

11. Agregue un nombre para la configuraci�n de su Application�Gateway. Este tutorial utiliza el nombre **App�Gateway: Windows VM**. Para modificar la configuraci�n predeterminada de Application�Gateway, agregue los siguientes detalles.

    | Regi�n | Nivel | Tama�o |
    | ------ | ---- | ---- |
    | Norte de Europa | Basic | Peque�o |
    | | |

    | Instancias | Horas |
    | ------- | ------- |
    | 1 | 365 |
    | | |

    | Datos procesados |
    | -------------- |
    | 50 GB |
    | | |

    | Zona 1: Norteam�rica, Europa |
    | ----------------------------- |
    | 50 GB |
    | | |

    ![Captura de pantalla del �rea de configuraci�n de la puerta de enlace de aplicaciones dentro de la p�gina web de estimaci�n de la calculadora de precios de Azure.](../images/1909.png)


# Tarea�2: Revise el presupuesto de precios

En esta tarea, revisaremos los resultados de la Calculadora de precios de Azure. 

1. Despl�cese hasta la parte inferior de la p�gina web de la Calculadora de precios de Azure para ver el **Coste mensual estimado** total.

    **Nota**: Explore las diversas opciones disponibles en la Calculadora de precios de Azure. Por ejemplo, este tutorial requiere que actualice la divisa a euro.

2. Cambie la divisa a euro y luego seleccione **Exportar** para descargar una copia de la estimaci�n y as� poder verla sin conexi�n en formato Microsoft Excel (`.xlsx`).

    ![Captura de pantalla de los costes mensuales estimados totales dentro de la p�gina web de estimaci�n de la calculadora de precios de Azure. La opci�n de divisa en euros resaltada indica c�mo modificar la divisa utilizada en una estimaci�n de la calculadora de precios de Azure. La opci�n de exportaci�n resaltada ilustra c�mo descargar una copia de una estimaci�n para verla sin conexi�n.](../images/1910.png)

    ![Captura de pantalla de un ejemplo de estimaci�n de la calculadora de precios de Azure en Microsoft Excel.](../images/1911.png)

�Enhorabuena! Descarg� un presupuesto de la Calculadora de precios de Azure.
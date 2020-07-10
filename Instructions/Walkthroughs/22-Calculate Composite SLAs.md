---
wts:
    title: '22: C�lculo del Acuerdo de nivel de servicio compuesto'
    module: 'M�dulo 4: precios y soporte t�cnico de Azure'
---
# 22 - Calcular el Acuerdo de nivel de servicio compuesto


En este tutorial determinaremos el Acuerdo de nivel de servicio disponible de los servicios de Azure y luego calcularemos la disponibilidad basada en el Acuerdo compuesto de la aplicaci�n esperada.

Nuestra aplicaci�n de ejemplo consta de estos servicios de Azure. No entraremos en configuraciones ni consideraciones arquitect�nicas en detalle. La intenci�n aqu� es dar un ejemplo de alto nivel.

+ **App service**: Para alojar la aplicaci�n.
+ **Azure AD B2C**: Para autenticar inicios de sesi�n de usuarios y administrar perfiles.
+ **Application Gateway**: Para administrar el acceso a la aplicaci�n y la escala. 
+ **Azure SQL Database**: Para almacenar datos de la aplicaci�n. 

# Tarea�1: Determinar los valores de porcentaje de tiempo de actividad del Acuerdo de nivel de servicio para nuestra aplicaci�n

1. En un explorador, vaya a la p�gina [Resumen del Acuerdo de nivel de servicio de Azure](https://azure.microsoft.com/es-es/support/legal/sla/summary/).

2. Localice el valor de tiempo de actividad del Acuerdo de nivel de servicio de **App�Service**, **99,95�%**. Haga clic en **Ver detalles completos** y luego expanda los **detalles del SLA**. Observe los **Porcentajes mensuales del tiempo de actividad** y los **Cr�ditos de servicio**.

3. Regrese a la p�gina web del Acuerdo de nivel de servicio, localice el servicio **Azure Active Directory B2C** y determine el valor de tiempo de actividad del acuerdo (SLA), **99,9 %**. 

4. Localice el valor de tiempo de actividad del Acuerdo de nivel de servicio de **Application Gateway**, **99,95 %**. 

5. La base de datos de Azure SQL usa niveles premium, pero no est� configurada para implementaciones con redundancia de zona. Localice el valor de tiempo de actividad del SLA de **Azure SQL Database**, **99,99%**. 

    **Nota**: Existen diferentes valores de tiempo de actividad para diferentes configuraciones e implementaciones de Azure SQL Database. Es importante que tenga claros los valores de tiempo de actividad requeridos al planificar y calcular el costo de su implementaci�n y configuraci�n. Peque�os cambios en el tiempo de actividad pueden tener un impacto en los costes del servicio, as� como aumentar potencialmente la complejidad en la configuraci�n. Otros servicios que pueden ser de inter�s en la p�gina web de resumen del Acuerdo de nivel de servicio de Azure incluir�an las **Maquinas virtuales**, **Cuentas de almacenamiento** y **Cosmos DB**.

# Tarea�2: Calcular el tiempo de actividad del porcentaje del Acuerdo de nivel de servicio compuesto de la aplicaci�n

1. Si alguno de los servicios que comprende nuestra aplicaci�n no est� disponible, tampoco lo estar� la aplicaci�n para que los usuarios inicien sesi�n y la usen. Como tal, el tiempo de actividad total para nuestra aplicaci�n consiste en lo siguiente:

    **% de tiempo de actividad de App Service** X **% de tiempo de actividad de Azure AD B2C** X **% de tiempo de actividad de Azure Application Gateway** X **% de tiempo de actividad de Azure SQL Database** = **% de tiempo de actividad total**

    que en t�rminos de porcentaje es:

    **99,95 %** X **99,9 %** X **99,95 %** X **99,99 %** = **99,79 %**

    Esta es la disponibilidad esperada basada en el Acuerdo de nivel de servicio (SLA) de nuestra aplicaci�n con los servicios y la arquitectura actuales.

�Enhorabuena! Ha determinado el tiempo de actividad basado en el Acuerdo de nivel de servicio (SLA) para cada uno de los servicios en nuestra aplicaci�n de muestra y luego ha calculado la disponibilidad esperada compuesta basada en el Acuerdo de nivel de servicio para la aplicaci�n.
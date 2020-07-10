---
wts:
    title: '15: Administrar el acceso con RBAC'
    module: 'M�dulo 03: Seguridad, privacidad, cumplimiento y confianza'
---
# 15: Administrar el acceso con RBAC

En este tutorial asignaremos roles y veremos registros de actividad. 

# Tarea�1: Vea y asigne roles

En esta tarea, asignaremos el rol de colaborador de la m�quina virtual. 

1. Inicie sesi�n en [Azure Portal](https://portal.azure.com).

2. Desde la hoja **Todos los servicios**, busque y seleccione **Grupos de recursos**, luego haga clic en **+ A�adir**.

3. Cree un grupo de recursos nuevo. Haga clic en **Crear** cuando haya acabado. 

    | Configuraci�n | Valor |
    | -- | -- |
    | Suscripci�n | **Elija su suscripci�n** |
    | Grupo de recursos | **miRGRBAC** |
    | Regi�n | **Este de EE. UU.** |
    | | |

4. Cree con **Revisar + crear** y luego haga clic en **Crear**.

5. Use **Actualizar** en la p�gina del grupo de recursos y haga clic en la entrada que representa el grupo de recursos reci�n creado.

6. Haga clic en la hoja **Control de acceso (IAM)** y luego cambie a la pesta�a **Roles**. Despl�cese por la gran cantidad de definiciones de rol disponibles. Use los iconos informativos para tener una idea de los permisos de cada rol. Tambi�n hay informaci�n sobre el n�mero de usuarios y grupos asignados a cada rol.

    ![Captura de pantalla de la hoja de roles de IAM. Se muestran los roles de propietario, colaborador y lector.](../images/1501.png)

7. Cambie a la pesta�a **Asignaciones de roles** en la hoja **miRGRBAC - Control de acceso (IAM)**, haga clic en **+ Agregar** y, luego, haga clic en **Agregar asignaci�n de roles**. Asigne el rol de colaborador de la m�quina virtual a su cuenta de usuario y, luego, haga clic en **Guardar**. 

    | Ajuste | Valor |
    | -- | -- |
    | Rol | **Colaborador de la m�quina virtual** |
    | Asignar acceso a | **Usuario de Azure AD, grupo o entidad de servicio** |
    | Seleccionar | su cuenta de usuario |
    | | |

    **Nota:** El rol de colaborador de la m�quina virtual le permite administrar m�quinas virtuales, pero no acceder a su sistema operativo ni administrar la red virtual ni la cuenta de almacenamiento a la que est�n conectadas.

    ![Captura de pantalla de la p�gina Agregar asignaci�n de roles completada con la informaci�n necesaria.](../images/1502.png)

8. Haga clic en **Actualizar** en la p�gina de asignaciones de roles y aseg�rese de que ahora est� incluido como colaborador de la m�quina virtual. 

    **Nota**: Esta asignaci�n en realidad no le concede ning�n privilegio adicional, ya que su cuenta ya tiene el rol Propietario, que incluye todos los privilegios asociados al rol Colaborador.

# Tarea�2: Supervisar asignaciones de roles y quitar un rol

En esta tarea, veremos el registro de actividad para comprobar la asignaci�n de roles y luego quitaremos el rol. 

1. En la hoja del grupo de recursos myRGRBAC, haga clic en **Registro de actividad**.

2. Haga clic en **Agregar filtro**, seleccione **Operaci�n** y luego haga clic en **Crear asignaci�n de roles**.

    ![Captura de pantalla de la p�gina Registro de actividad con el filtro configurado.](../images/1503.png)

3. Compruebe que el registro de actividad muestre su asignaci�n de roles. 

    **Nota**: �Sabe c�mo quitar su asignaci�n de roles?

�Enhorabuena! Ha asignado roles y ha visto registros de actividad. 

**Nota**: Para evitar costes adicionales, puede eliminar este grupo de recursos. Busque grupos de recursos, haga clic en su grupo de recursos y, a continuaci�n, haga clic en **Eliminar grupo de recursos**. Compruebe el nombre del grupo de recursos y luego haga clic en **Eliminar**. Supervise las **Notificaciones** para ver c�mo se realiza la eliminaci�n.



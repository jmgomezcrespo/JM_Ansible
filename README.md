# ROLES

* despuppet: Usado para eliminar la configuración de puppet para Telvent

* userdiscover: Generación de usuario para autodescubrimeinto en ServiceNow

* Check: Generación de listado de paquetes a actualizar por motivos de seguridad

* Notification: Envio de listado de máquinas a actualizar y paquetes

* Program: Programación de ventanas para la realización de updates

* Update: Tareas de updates para los diferentes entornos
	* main.yml > Filtro por entornos
	* mysql.yml > Acciones sobre el cluster MySQL
	* rac.yml > Acciones sobre el RAC de Oracle
	* static.yml > Acciones sobre los static
	* general.yml > Acciones osbre el resto de nodos

# VARIABLES

* Conexion
En el fichero de hosts se pueden añadir variables por grupo de maquina
        [<grupo_maq>:vars]
        ansible_user=user
        ansible_password=password

* Salida internet
Debido a que necesita descargar paquetes si la máquina no tiene acceso a internet se puede hacer un tunel ssh si tenemos acceso a un proxy

Añadimos en la variable de host la opcion de ssh
        ansible_ssh_extra_args="-R 3128:localhost:3128"

En el playbook definimos las variables que se pasaran a los nodos.
  environment:
    http_proxy: "http://localhost:3128"
    https_proxy: "https://localhost:3128"


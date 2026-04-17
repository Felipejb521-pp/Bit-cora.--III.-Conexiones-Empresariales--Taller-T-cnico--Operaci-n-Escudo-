**Fundamentos de Seguridad y Auditoría**

**Reto de Investigación 1**
 	Syslog : Es el protocolo que se usa para transmitir mensajes de notificación de eventos. El mensaje está formado por tres partes .
		La cabecera(header), que representa la información del archivo de registros, por ejemplo, prioridad del registro, versión del
		protocolo, marca de tiempo, nombre del servidor, nombre de la aplicación, id del proceso e id del mensaje

		Ej:Mensaje de inicio de sesión de usuario correcto
LEEF:2.0|Check Point|Linux OS|1.0|Log In|cat=Linux OS devTime=1539878943	usrName=cpaction=Log In ifdir=inbound loguid={0x5bc8b020,0x3,0x6a9610ac,0xee29cd8} origin=172.16.150.106 sequencenum=4 version=5	application=su default_device_message=<86>su: pam_unix(su:session):session opened for user cp_postgres by (uid\\=0)	facility=security/authorization messages login_status=succeeded product_category=OS	syslog_severity=Informational

		Variables : 
		
		♦ El valor Facility permite determinar qué proceso de la máquina generó el mensaje. Los Facilities reflejan los nombres de los procesos y demonios de UNIX.
		

		♦ Cada mensaje de Syslog incluye un valor de prioridad al principio del texto. El valor de prioridad oscila entre 0 y 191 y no se rellena con espacios ni 		ceros iniciales.


		¿Por qué es una negligencia grave que el archivo /var/log/auth.log tenga permisos de lectura para usuarios no privilegiados?
		Es el log de autorizaciones (programas como su, passwd, login, shutdown, sshd) para Debian y Ubuntu . Es una negligencia porque es el fichero que almacena los
		eventos relacionados con mecanismos de autorización.

		¿Qué información específica (como PIDs, nombres de usuario o direcciones IP) diferencia un intento fallido de conexión remota SSH de un simple fallo de 		contraseña de un usuario local frente a la pantalla?
		El protocolo SSH(Secure Shell) utiliza una arquitectura cliente-servidor para establecer conexiones seguras. El cifrado simétrico es una técnica en la que se 		utiliza la misma clave tanto para cifrar como para descifrar los datos entre el cliente y el servidor además el log incluirá obligatoriamente la dirección IP 		y el puerto de origen.
		Ej:... sshd[1234]: Failed password for root from 192.168.1.50 port 45678 ssh2


**Reto de Investigación 2**

		¿Qué ventajas vitales ofrece enviar y custodiar los logs en un servidor externo seguro en lugar de mantenerlos dispersos e indefensos en la propia máquina que 			podría ser vulnerada?
		A nivel empresarial si el servidor principal sufre un fallo de hardware crítico o un ataque de Ransomware que cifra todo el disco, perderás los logs junto con 			el sistema. Al tener todos los logs en un solo punto, puedes ver patrones , estos patrones nos pueden alertar sobre un ataque.

**Bibliografía**
		
		♦Servidores syslog externos en StorageGRID.https://docs.netapp.com/es-es/storagegrid/monitor/considerations-for-external-syslog-server.html
		♦Arsys.SSH: qué es y cómo funciona este protocolo | Blog de Arsys.https://www.arsys.es/blog/ssh
		♦What are Syslog Facilities and Levels?.https://success.trendmicro.com/en-US/solution/KA-0017337

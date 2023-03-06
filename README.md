# Configuraciones Previas
Primero recordad que hay que hay que tener instalado ansible para hacer un aprovisionamiento:  
- [Guia de como instalarlo y pre](https://github.com/AlvaroAMGX/Aprovisionamiento_con_Ansible/blob/main/Instalación.md)
# Aprovisionamiento con Ansible
## Conectar el maestro con el cliente
Primero vamos a instalar el servidor ssh en las dos maquinas con este comando:  
```bash
sudo apt install openssh-client openssh-server
```
Ahora generaremos la clave con el comando ssh-keygen:  
![keygen](https://github.com/AlvaroAMGX/Aprovisionamiento_con_Ansible/blob/main/imagenes/ansible2.png)  
Ahora vamos a ir a la carpeta .ssh y veremos que hay dos archivos llamados id_rsa y id_rsa,pub les cambiaremos los permisos con este comando:
```bash
chmod 600 id_rsa
chmod 600 id_rsa.pub
```
Por ultimo copiaremos nuestra clave al cliente con este comando:
```bash
ssh-copy-id -i ~/.ssh/id_rsa.pub usuario_del_cliente@ip_Cliente
```
Nos pedira la contraseña y ya habremos añadido nuestra key correctamente:
![copiar key](https://github.com/AlvaroAMGX/Aprovisionamiento_con_Ansible/blob/main/imagenes/ansible3.png)
Ahora vamos a editar el fichero /etc/ansible/hosts y añadiremos esta linea:
```bash
sudo nano /etc/ansible/hosts
-----------------------------
[Client]
node1 ansible_ssh_host=usuario_del_cliente@ip_Cliente
```
Si usamos este coamndo podremos ver si lo hemos realizado correctamente:
```bash
ansible-inventory --list -y
```
En esta captura es lo que nos tendria que salir:
![copiar key](https://github.com/AlvaroAMGX/Aprovisionamiento_con_Ansible/blob/main/imagenes/ansible4.png)
Por ultimo para comprobar que hemos echo todo correctamente vamos a hacer un ping con ansible:
```bash
sudo ansible -m ping Client
```
Nos deberia responder de esta manera si lo hemos realizado todo correctamente:
![copiar key](https://github.com/AlvaroAMGX/Aprovisionamiento_con_Ansible/blob/main/imagenes/ansible5.png)
## Configuración del Playbook e instalación de wordpress
Primero vamos a clonar un github de playbooks de ansible con este comando:
```bash
git clone https://github.com/do-community/ansible-playbooks.git
```
Vamos a editar el archvio de default.yml y añadiremos estas lineas:
```bash
sudo nano ansible-playbooks/lamp_ubuntu1804/vars/default.yml
------------------------------------------------------------
# Dentro añadiremos estas lineas
---
#System Settings
php_modules: [ 'php-curl', 'php-gd', 'php-mbstring', 'php-xml', 'php-xmlrpc', 'php-soap', 'php-intl', 'php-zip' ]

#MySQL Settings
mysql_root_password: "usuario"
mysql_db: "wordpress"
mysql_user: "usuario"
mysql_password: "usuario"

#HTTP Settings
http_host: "usuario.local"
http_conf: "usuario.local.conf"
http_port: "80"
```
Por ultimo nos moveremos con este comando a esta ruta:
```bash
 cd ansible playbooks/wordpress-lamp_ubuntu1804/
```
Y haremos este comando para que empiece a instalarlo todo:
```bash
sudo ansible-playbook playbook.yml -u usuario --ask-become-pass
```
Aqui una captura de lo que nos tendria que salir:
![instalacion LAMP](https://github.com/AlvaroAMGX/Aprovisionamiento_con_Ansible/blob/main/imagenes/ansible6.png)

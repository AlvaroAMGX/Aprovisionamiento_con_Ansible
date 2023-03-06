# Configuraciones Previas
Primero recordad que hay que hay que tener instalado ansible para hacer un aprovisionamiento:  
- [Guia de como instalarlo y pre](https://github.com/AlvaroAMGX/Aprovisionamiento_con_Ansible/blob/main/Instalación.md)
# Aprovisionamiento con Ansible
Primero vamos a instalar el servidor ssh en las dos maquinas con este comando:
```bash
sudo apt install openssh-client openssh-server
```
Ahora generaremos la clave con el comando ssh-keygen:  
![keygen](https://github.com/AlvaroAMGX/Aprovisionamiento_con_Ansible/blob/main/imagenes/ansible2.png)  
Ahora vamos a ir a la carpeta ssh y veremos que hay dos archivos llamados id_rsa y id_rsa,pub les cambiaremos los permisos con este comando:
```bash
chmod 600 id_rsa
chmod 600 id_rsa.pub
```

# Configuraciones Previas
Primero recordad que hay que hay que tener instalado ansible para hacer un aprovisionamiento:  
- [Guia de como instalarlo y pre](https://github.com/AlvaroAMGX/Aprovisionamiento_con_Ansible/blob/main/Instalación.md)
# Aprovisionamiento con Ansible
Primero vamos a instalar el servidor ssh en las dos maquinas con este comando:
```bash
sudo apt install openssh-client openssh-server
```
Ahora generaremos la clave con el comando ssh-keygen:

# Instalación y configuración básica de Ansible
Para empezar a instalar deberemos tener dos ubuntus limpios uno sera el cliente y otro sera el maestro ,para empezar la instalación usaremos estos comandos en el maestro:
```bash
sudo apt-add-repository ppa:ansible/ansible
sudo apt update
sudo apt install ansible
```
Luego configuraremos el archivo host de ansible para añadir a nuestra maquina cliente

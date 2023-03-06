# Instalación y configuración básica de Ansible
Para empezar a instalar deberemos tener dos ubuntus limpios uno sera el cliente y otro sera el maestro ,para empezar la instalación usaremos estos comandos en el maestro:
```bash
sudo su
apt install software-properties-common
apt-add-repository --yes --update ppa:ansible/ansible
sudo apt install ansible
```
Para comprobar que lo hemos instalado simplemente pondremos este coamndo:
```bash
ansible --version
```
Aqui podeis ver la respuesta que os deberia dar para comprobar que todo esta instalado correctamente:  
![version ansible]()

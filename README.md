
## Pasos para instalar docker y docker compose (comandos dentro de la máquina virtual):
- Instalar Docker https://docs.docker.com/engine/install/ubuntu/
- Instalar docker compose https://docs.docker.com/compose/install/linux/

## Pasos para que no sea necesario usar sudo para docker compose (comandos dentro de la máquina virtual):
- sudo groupadd docker;
- sudo usermod -aG docker $USER;
- newgrp docker;

## Crear carpeta para el proyecto (comandos dentro de la máquina virtual):
- cd;
- mkdir nuevas_tecnologias;
- ~/nuevas_tecnologias;

### Comandos en máquina física para subir los archivos:
- sudo rsync --ignore-existing -avz --progress --stats /ruta/a/web1 estudiante@10.43.103.16:/home/estudiante/nuevas_tecnologias

### Levantar web (comandos dentro de la máquina virtual):
- cd ~/nuevas_tecnologias/web1;
- docker compose up --build -d;

## Exponer el puerto para poder exponer el balanceador fuera de la red:
- ssh -N -L 0.0.0.0:55556:localhost:55556 estudiante@10.43.103.16

Se accede desde el navegador usando http://localhost:55556/

# Ver tráfico de red
## Instalar tshark
- sudo apt update
- sudo apt install tshark
- tshark -v
- ip a

sudo tshark -i wlp0s20f3 -f "src host 192.168.1.6 and (dst host 44.228.249.3 or dst host 10.43.103.16)" -c 100
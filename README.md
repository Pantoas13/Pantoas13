- 👋 Hi, I’m @Pantoas13
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
Pantoas13/Pantoas13 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
import os
from binance.client import Client
from binance.enums import *

# Obtén las claves API de las variables de entorno
api_key = os.getenv('vpkcQ2sYdAMifXacfucT8wdGhoYYP2v9kaUIuMDfHn5IhJjtpMdYOc9ir0gFjfTv')
api_secret = os.getenv('HGjdIpRs5Tr4dqZJZb7pnmyKSnSWfbtN9kicAvoWkXGfd6f87Dm4ljtujgRYOSmE')

# Crear cliente de Binance
client = Client(api_key, api_secret)

# Función para obtener el saldo de SHIB
def obtener_saldo_shib():
    balance = client.get_asset_balance(asset='SHIB')
    return balance

# Función para comprar SHIB
def comprar_shib(cantidad):
    try:
        order = client.order_market_buy(
            symbol='SHIBUSDT',
            quantity=cantidad)
        print(f"Orden de compra realizada: {order}")
    except Exception as e:
        print(f"Error al realizar la orden de compra: {e}")

# Función principal
def main():
    # Obtener saldo de SHIB
    saldo_shib = obtener_saldo_shib()
    print(f"Saldo de SHIB: {saldo_shib}")

    # Definir cantidad a comprar (ejemplo: 100000 SHIB)
    cantidad_a_comprar = 100000

    # Comprar SHIB
    comprar_shib(cantidad_a_comprar)

if __name__ == "__main__":
    main()cd \ruta\del\minero
minerd -a scrypt -o stratum+tcp://ltc.poolbinance.com:3333 -u camilo13 
#!/bin/bash

# Configurar variables
POOL1="stratum+tcp://ltc.poolbinance.com:3333"
POOL2="stratum+tcp://ltc.poolbinance.com:443"
POOL3="stratum+tcp://ltc.poolbinance.com:25"
WALLET="0x02adee104dda90bc6a7500d673fa9cf022eea4bf"
WORKER="camilo13.001"
MINER_PATH="/home/ubuntu/bfgminer"

# Actualizar paquetes
echo "Actualizando paquetes..."
sudo apt-get update
sudo apt-get upgrade -y

# Instalar dependencias necesarias
echo "Instalando dependencias..."
sudo apt-get install -y build-essential libcurl4-openssl-dev git libevent-dev

# Crear el directorio del minero si no existe
if [ ! -d "$MINER_PATH" ]; then
  echo "Creando el directorio para bfgminer..."
  mkdir -p "$MINER_PATH"
fi

# Eliminar el directorio bfgminer si ya existe
if [ -d "$MINER_PATH" ]; then
  echo "Eliminando el directorio bfgminer existente..."
  rm -rf "$MINER_PATH"
fi

#!/bin/bash

# Configurar variables
POOL1="stratum+tcp://ltc.poolbinance.com:3333"
POOL2="stratum+tcp://ltc.poolbinance.com:443"
POOL3="stratum+tcp://ltc.poolbinance.com:25"
WALLET="0x02adee104dda90bc6a7500d673fa9cf022eea4bf"
WORKER="camilo13.001"
MINER_PATH="/home/ubuntu/bfgminer"

# Actualizar paquetes
echo "Actualizando paquetes..."
sudo apt-get update
sudo apt-get upgrade -y

# Instalar dependencias necesarias
echo "Instalando dependencias..."
sudo apt-get install -y build-essential libcurl4-openssl-dev git libevent-dev

# Crear el directorio del minero si no existe
if [ ! -d "$MINER_PATH" ]; then
  echo "Creando el directorio para bfgminer..."
  mkdir -p "$MINER_PATH"
fi

# Eliminar el directorio bfgminer si ya existe
if [ -d "$MINER_PATH" ]; then
  echo "Eliminando el directorio bfgminer existente..."
  rm -rf "$MINER_PATH"
fi

# Clonar el repositorio de bfgminer
echo "Clonando bfgminer..."
git clone https://github.com/luke-jr/bfgminer.git "$MINER_PATH"

# Cambiar al directorio del proyecto
cd "$MINER_PATH"

# Actualizar submódulos
echo "Actualizando submódulos..."
git submodule update --init --recursive

# Construir el proyecto
echo "Construyendo bfgminer..."
./autogen.sh
./configure
make

# Crear un script para ejecutar bfgminer con la configuración adecuada
echo "Creando script para iniciar la minería..."
cat <<EOL > start_mining.sh
#!/bin/bash
while true; do
    ./bfgminer -o $POOL1 -u $WALLET.$WORKER -p x \
               -o $POOL2 -u $WALLET.$WORKER -p x \
               -o $POOL3 -u $WALLET.$WORKER -p x \
               --api-listen --api-allow W:127.0.0.1 --no-submit-stale
    sleep 10
done
EOL

# Hacer el script ejecutable
chmod +x start_mining.sh

# Crear un servicio de systemd para asegurar que el minero se inicie al arrancar y se reinicie en caso de fallo
echo "Configurando servicio en systemd..."
sudo bash -c 'cat <<EOL > /etc/systemd/system/miner.service
[Unit]
Description=BFGMiner Service
After=network.target

[Service]
ExecStart=/home/ubuntu/bfgminer/start_mining.sh
Restart=always
User=ubuntu
Group=ubuntu

[Install]
WantedBy=multi-user.target
EOL'

# Recargar systemd y habilitar el servicio
echo "Habilitando y arrancando el servicio..."
sudo systemctl daemon-reload
sudo systemctl enable miner.service
sudo systemctl start miner.service

# Proporcionar feedback al usuario
echo "Configuración completa. El servicio de minería está en ejecución y se reiniciará en caso de fallo."



    
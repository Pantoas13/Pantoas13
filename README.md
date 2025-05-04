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
minerd -a scrypt -o stratum+tcp://ltc.poolbinance.com:3333 -u camilo13 -p 123456
# Recargar systemd y habilitar el servicio 
echo "Habilitando y arrancando el servicio..." 
sudo systemctl daemon-reload 
sudo systemctl enable miner.service 
sudo systemctl start miner.service 
  
# Proporcionar feedback al usuario 
echo "Configuración completa. El servicio de minería está en ejecución y se reiniciará en caso de fallo."

    # Proporcionar feedback al usuario 
echo "Configuración completa. El servicio de minería está en ejecución y se reiniciará en caso de fallo."
# Proporcionar feedback al usuario 
echo "Configuración completa. El servicio de minería está en ejecución y se reiniciará en caso de fallo."
E1

# Proporcionar feedback al usuario 
echo "Configuración completa. El servicio de minería está en ejecución y se reiniciará en caso de fallo."

<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Promoción de Servicios Fiverr</title>
  <meta name="description" content="Descubre mis mejores servicios en Fiverr y contrátame directamente desde aquí.">

  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f5f5f5;
      margin: 0;
      padding: 0;
      text-align: center;
    }
    .container {
      max-width: 600px;
      margin: 50px auto;
      background: #fff;
      padding: 30px;
      box-shadow: 0 0 15px rgba(0,0,0,0.1);
      border-radius: 10px;
    }
    h1 {
      color: #1dbf73;
    }
    p {
      font-size: 18px;
    }
    a.cta-button {
      display: inline-block;
      margin-top: 20px;
      padding: 15px 25px;
      background-color: #1dbf73;
      color: #fff;
      font-size: 18px;
      text-decoration: none;
      border-radius: 5px;
    }
    a.cta-button:hover {
      background-color: #17a865;
    }
    .whatsapp-button {
      display: inline-block;
      margin-top: 20px;
      padding: 15px 25px;
      background-color: #25d366;
      color: #fff;
      font-size: 18px;
      text-decoration: none;
      border-radius: 5px;
    }
    .whatsapp-button:hover {
      background-color: #128c7e;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>¡Contrata mis servicios en Fiverr!</h1>
    <p>Ofrezco soluciones profesionales en diseño, marketing, redacción y más. Visita mi perfil completo y descubre todo lo que puedo hacer por ti.</p>
    <a href="https://www.fiverr.com/users/TrendPulseShop" class="cta-button" target="_blank">Ver mis servicios en Fiverr</a>

    <a href="https://wa.me/573181550264" class="whatsapp-button" target="_blank">Contactar por WhatsApp</a>
  </div>
</body>
</html>

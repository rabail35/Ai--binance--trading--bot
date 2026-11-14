# Ai--binance--trading--bot
Ai binance trading bot

import requests
import time

print("AI BINANCE MARKET SCANNER STARTED")

URL = "https://api.binance.com/api/v3/ticker/price"

coins = [
    "BTCUSDT", "ETHUSDT", "BNBUSDT", "SOLUSDT",
    "XRPUSDT", "DOGEUSDT", "ADAUSDT", "AVAXUSDT",
    "LINKUSDT", "DOTUSDT", "SUIUSDT", "NEARUSDT",
    "INJUSDT", "LTCUSDT", "TRXUSDT", "APTUSDT",
    "ARBUSDT", "OPUSDT", "PEPEUSDT", "RENDERUSDT"
]

while True:
    print("\n========== LIVE MARKET ==========")

    for coin in coins:
        try:
            response = requests.get(
                URL,
                params={"symbol": coin},
                timeout=10
            )
            response.raise_for_status()
            data = response.json()

            print(f"{coin}: ${float(data['price']):,.8f}")

        except Exception as error:
            print(f"{coin}: Data unavailable")

    print("Next scan in 30 seconds...")
    time.sleep(30)

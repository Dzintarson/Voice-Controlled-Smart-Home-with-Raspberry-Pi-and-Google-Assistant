# Voice-Controlled-Smart-Home-with-Raspberry-Pi-and-Google-Assistant
Managing a smart home through voice commands via Google Assistant and Raspberry Pi.
from flask import Flask, request
import requests

app = Flask(__name__)

@app.route('/webhook', methods=['POST'])
def webhook():
    data = request.get_json()
    command = data['queryResult']['intent']['displayName']

    if command == 'turn_on_lights':
        # Code to turn on lights
        response = "Lights are now on."
    elif command == 'turn_off_lights':
        # Code to turn off lights
        response = "Lights are now off."
    else:
        response = "Sorry, I don't understand that command."

    return {'fulfillmentText': response}

if __name__ == '__main__':
    app.run(port=5000)

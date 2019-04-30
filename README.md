# tie-api-example-twilio-whatsapp
Make your Teneo bot available on WhatsApp or SMS using the Twilio Programmable SMS api.

This node.js example connector allows you to make your Teneo bot available on Twilio IVR (Interactive Voice Response). The connector acts as middleware between Twilio IVR API and Teneo to establish a phone call with a Teneo bot. This guide will take you through the steps of setting a new Twilio phone number and deploying the connector to respond to events sent by Twilio.


## Prerequisites
### Https
Making the connector available via https is preferred. Ngrok is recommended for this.

### Teneo Engine
Your bot needs to be published and you need to know the engine url.


## Setup instructions
### Download, install and start connector
1. Download or clone the connector source code:
    ```
    git clone https://github.com/artificialsolutions/tie-api-example-twilio-whatsapp.git
    ```
2. Install dependencies by running the following command in the folder where you stored the source:
    ```
    npm install
    ``` 
3. Start the connector with the following command (replacing the environment variable with the appropriate value):
    ```
    TENEO_ENGINE_URL=<your_engine_url> node server.js
    ```

### Make the connector available via https
When using ngrok, make the connector available via https:

1. Make sure your connector is available via https. When running locally you can for example use [ngrok](https://ngrok.com) for this. Run the connector on port 1337 by default.
    ```
    ngrok http 1337
    ```
2. Running the command above will display a public https URL, copy it, we will use it as a `Webhook URL` for the following steps.


### Setup a Twilio WhatsApp phone number
1. Setup a free [Twilio](https://www.twilio.com/try-twilio) account, which comes with free credit money you can spend on buying a number.
2. Go to the left pane menu and click the **Programmable SMS** item, then from the submenu choose **WhatsApp**.
3. Follow the instructions in the 'Learn' submenu to set up your testing sandbox by sending a specific WhatsApp message provided on the page to the phone number provided on the page. 
4. Next, in the 'Sandbox' submenu add your Webhook URL to the "When a message comes in" field. Hit save to save your changes.


That's it! Now you can use WhatsApp to interact with your bot!


## Running the connector on Heroku

Click the button below to deploy the connector to Heroku:

[![Deploy](https://www.herokucdn.com/deploy/button.svg?classes=noborder)](https://heroku.com/deploy?template=https://github.com/artificialsolutions/tie-api-example-twilio-ivr)

In the 'Config Vars' section, add the following:
* **TENEO_ENGINE_URL:** The engine url


Next, follow the Twilio Setup instructions above. Make sure that in the step 4 you set the Webhook URL to the url of the Heroku app.


> The Twilio API for Whatsapp is currently in beta. For more details, visit the Twilio website: [Twilio API for WhatsApp](https://www.twilio.com/docs/sms/whatsapp/api)


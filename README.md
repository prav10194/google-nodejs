# google-nodejs
A simple example of integrating google actions with our Node.js application running locally.

Setting up your action in Google
-------

1. Visit the following link - https://console.dialogflow.com/api-client/#/login.

2. Click Sign in with Google.

![alt text](https://github.com/prav10194/google-nodejs/blob/master/screenshots/sign-in.png "Watson")

3. Click Create Agent on the top left.

![alt text](https://github.com/prav10194/google-nodejs/blob/master/screenshots/create-agent.png "Watson")

4. Type in MiniHome and click Create

5. Now create an intent. Type in as shown. Put intent name also as HomeMini.

![alt text](https://github.com/prav10194/google-nodejs/blob/master/screenshots/intent.png "Watson")

6. Double tap on whatever you typed in User says and chose the option as @sys.geo-state-us. 

![alt text](https://github.com/prav10194/google-nodejs/blob/master/screenshots/double-click.png "Watson")

7. It will look like this -

![alt text](https://github.com/prav10194/google-nodejs/blob/master/screenshots/final-screen.png "Watson")

8. Go to fulfillment tab on the left.

![alt text](https://github.com/prav10194/google-nodejs/blob/master/screenshots/fulfillment.png "Watson")

9. Enable the webhook.

![alt text](https://github.com/prav10194/google-nodejs/blob/master/screenshots/webhook.png "Watson")

10. Enter your ngrok domain followed by /weather. It will look something like - https://xxxx.ngrok.io/weather
Setting up ngrok has been explained down.  

11. Click Save at the bottom of the page.

12. Go to your MiniHome Intent.

13. At the bottom you will see Fulfillment. Click on it.

![alt text](https://github.com/prav10194/google-nodejs/blob/master/screenshots/fulfillment-option.png "Watson")

14. Enable Use Webhook option.

![alt text](https://github.com/prav10194/google-nodejs/blob/master/screenshots/webhook-option.png "Watson")

15. Go to Integrations Tab on left.

![alt text](https://github.com/prav10194/google-nodejs/blob/master/screenshots/integration.png "Watson")

16. Click on Google Assistant.

17. Select What in implicit invocation.

![alt text](https://github.com/prav10194/google-nodejs/blob/master/screenshots/whats-the-weather-intent.png "Watson")

18. Click Test.

19. Keep the new screen open and set up the nodejs application.


Setting up the Node.js application
-------

1. Clone/Download zip of repository.

2. Extract content of the zip.

3. Open cmd to run the following code -
```cmd
cd "folderpath where zip is extracted"
npm install
```

4. After the installation, run -  
```cmd
npm start
```

Setting up the .env file
-------

1. You need to register for google geoencoder api from here - https://developers.google.com/maps/documentation/geocoding/get-api-key?authuser=1

Copy the API KEY in the .env file.

2. You also need to have a bluemix account and should have credentials for the Weather API. You can get it from here - https://console.bluemix.net/catalog/services/weather-company-data

Copy the Username and Password of the SERVICE (as shown in image) in the .env file.

![alt text](https://github.com/prav10194/alexa-integration-with-watson/blob/master/screenshots/weather.png "Weather Service in Bluemix")

Setting up the ngrok
-------

1. In Google Actions, you need an endpoint so that it can connect to your app locally. For this we will install ngrok. Download from here - https://ngrok.com/download

2. Run your app using npm start as explained above in Setting up the Node.js application.

3. Open another terminal and run the following command -

```cmd
ngrok http 8080
```
8080 is the port number on which your Nodejs app is running.

4. Copy the Forwarding domain from the ngrok terminal. E.g. Your domain would look something like - https://c90db8b2.ngrok.io

Paste it in the Fulfillment Webhook Configuration.

The final endpoint will be - https://c90db8b2.ngrok.io/weather

Testing
-------

Here is a sample conversation flow using Google Actions -

![alt text](https://github.com/prav10194/google-nodejs/blob/master/screenshots/testing-gif.gif "Watson")

You can also test it on your Google Assistant app on your phone.

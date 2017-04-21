# StockPots
A simple TJBot application that recognises, and converses on, different Knorr Stockpots based on Watson Cognitive capabilities

This application will let you converse with a TJBot.  At each interaction it will also wave, and will change the colour of the LED when listening or replying.

 # Pre-requisites
 
 This has been developed on a TJBot built with a Raspberry Pi model 3
 I have added in a Pi camera, a speaker (via the 3.5mm port), and a USB microphone
 
 For Software, I have used node-red for the development on the Raspberry Pi, as follows:
 
 -  Node-RED v0.16.2
   
 -  Node.js v7.7.3
 
 I have added in the following:
 
 -  node-red-contrib-camerapi
   
 -  node-red-contrib-micropi
   
 -  node-red-contrib-play-audio
   
 -  node-red-contrib-speakerpi
   
 -  node-red-node-watson
   
 You will also need to install 'curl' if you dont already have it in order to manage the visual recognition classifier
 
 For the server end, I am using Bluemix with an application that uses Watson capabilities for:
 
 -  speech to text
 -  text to speech
 -  visual recognition
 -  conversation
   
 # Assembly
 
 To build the Raspberry Pi connectivity, refer to the TJBot assembly instructions here: https://github.com/ibmtjbot/tjbot
 
 The pins I am using are 11 (GPIO17),15 (GPIO22) for the LED and 32 (GPIO12) for the servo attached to the arm.
 
 # Node-red flows
 
 Clone or download the repository to get the sample flow:

    git clone git@github.com:StuartArnell/StockPots.git
    cd StockPots
 
 Copy the content of the flows_raspberrypi.json file to clipboard. Go to http://localhost:1880 on the RaspberryPi and import the flow.  In the upper right corner click on the menu bar, then Import > Clipboard to import the flow:
 
 
# Bluemix configuration

Log in to your Bluemix account, and create a new application.
You will then need some services to your application.

 -  speech to text
 -  text to speech
 -  visual recognition
 -  conversation
 
 You will need to go through each of these and make a note of the credentials as you will need to use these in your node-RED Watson nodes.
 
 
# WATSON service configuration

While teh text/speech conversions need no custom specifiers, both the Visual Recognition and Conversation services will need to be customized.





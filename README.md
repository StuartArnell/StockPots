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

While the text/speech conversions need no custom specifiers, both the Visual Recognition and Conversation services will need to be customized.

For the Conversation, once you have added the Conversation service to your app, you need to double click on it, and then 'Launch Tool'.  From the tool you can import a JSON file that describes a conversation.  The 'Conversation_Workspace.json' file in the git repository describes the conversation for this application and can be imported 'as-is'.

For the Visual recognition capability, you can also import files into the service.  Again, double clisck on the service and then Launch the tool (Beta).  You can then import the three files provided in the git repository.

-   ChickenStock_positive_examples.zip
-   VegetableStock_positive_examples.zip
-   Negatives.zip

Take a look a the documentation to understand what the Negatives.zip file is for.

Note that it may take a few minutes for Watson's 'learning' to complete once you import the files.

# Further node-red configuration

You now need to configure the Watson nodes in node-RED to use the service instances that you have created.

For each of the text-to-speech (Flow 4), speech-to-text (Flow 3), conversation (Flow 6), and visual recognition (Flow 5) nodes in the node-RED application, double click on the node and enter the relevant credentials from teh Bluemix services.

Finally, on Flow 5 there is a javascript node called 'Use the custom classifier'.  You will need to update this code sippet to refer to the Visual Recognition custom classifier that you created when you imported the photographs (in my case it is 'StockPots_2027870576'.

# Using the application

The application as provided recognises Knorr Vegetable and Chicken Stockpot (4x packs).  You can obviously train it for more, or change the products.

Note that, at present, for each iteration of the conversation you need to initiate the flow thru the 'Start Flow' injection node to get the TJBot to listen.  I need to find a way to fix that!

The commands are:

-   Hello, Hi There (or similar) .... starts the conversation
-   I need some help with a product (or similar - look at the Conversation intents for options) to ask for info about a product
-   Show the bot (hold up to the camera) your product package and say 'Ready' as instructed.
-   Once TJ has verified that the product has been recognised ( saying it is either vegetable or chicken stock ) you can ask questions about the product.  See the Conversation Intents for details - but try 'Where is it made?  What is in it?  Is it suitable for vegetarians?' as examples

# Whats Next?

Obviously, you may want to trai your bot in different products.  Bear in mind that you will need to change the conversation intents and dialogs appropriately aswell as training the visual recognition.







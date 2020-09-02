# GODOT mobile rpg tutorial     

## We started by installig GODOT and creating a new project
go to scene box and create custom node      
name node *Battle*      

## We first setup our import settings for our textures                
now since we are going to be using 2D pixel graphics        
we will need to adjust our settings accordingly     
so first try to bring the default godot sprite and go to import tab (top left)      
then set the preset as 2D pixel as default for textures     
just don't forget to reimport       

## Now we try to import resources 
now we open up the folder location for the project and simply cut/copy paste the resources in   

## Now we basically save the scene (the scene we just named battle)        
then press on the play button and select battle as the scene to show        
after this the debugging dialog box will open but nothing will happpen      
to make this work properly for a mobile game we will have to setup more settings        

## Now we configure our actual project settings 
so just go to project-> general tab-> display-> window-> size     
now we set the Width and Height of our display window along with the test Width and test Height     
here the *Width* and *Height* are the actual Width and Height of our game   
this Width and Height are measured in pixels by the way     
set Width: 90, Height: 160, test Width: 360, test Height:640        
test Width and test Height are how many pixels the game-window will take                
we need to set the above values so that the canvas gets scaled up otherwise it'll look tiny          
save these values and press play, you'll see that the game canvas has changed       
now however we need to scale the mockup image when we change the size of the game-window        
so we got to project-> general tab-> display-> window-> Stretch and change mode to 2D       
this doesn't change the fact that the mockup image doesn't retain its aspect ratio, so we need to change that too       
again go to project-> general tab-> display-> window-> Aspect and change it to keep     
what this will do is, it will add black bars to the image helping maintain aspect ratio     

## Now we need to add an enemy to the game 
so we create a new child node of the battle node of the type node 2D        
and simply name it enemy    
Now we need to add a sprite to our enemy    
- do this by clicking on the newly made enemy node and dragging & dropping the sprite at the origin       
- to check that the sprite is on the origin, double click on it in the canvas and check its transform properties      
- set the x and y values to zero      
- also rename the image representing the enemy to sprite      
- now however, when we select the rat sprite & move it, it will move the rat sprite but not the enemy     
- therefore, to solve this we click on the enemy node and on the canvas toolbar we click on the icon next to the lock     
- this makes it so that the nodes children aren't selectable      

## Now we move on to positioning and setting of the game scene
here we basically want to use the mockup image as a sort of outline/placeholder to make our game scene      
we basically change the visibility of the mockup and make it sort of transparent   
- to do so, we select the mockup image then go to its visibility setting and in modulate, adjust its alpha(A) property     

then we place the enemy on top of where the enemy is in the mockup      
and just like that we add other resources too like the dungeon (just remember to keep the Battle node selected)         
*Do try to keep things well aligned*        

**The order of importing resources also determines which asset is on top**  
this is why when we import dungeon after enemy the enemy gets hidden    
to fix this we basically move the dungeon up in the scene dialog box to just underneath the Battle scene node   

**you can hide each layer/node by clicking on the eye icon on the right of the node**   

## Moving on to adding the enemy HP 
to do so we click on the enemy node and add new child node  
then we choose label from the node dialog box 
*remember to change the settings to be able to select childern nodes*   
after that we now have to add some values to this label 
- move the label to its position while referencing the mockup
- then add some text by typing into the textbox in the inspector panel of the label node    
- also rename label to "HPLabel"    
    *we will fix the look of the text/value later*

After we hide our mockup and run the game it looks slightly better  

## Now we start working on the UI
for this we add a new node *control node*   
this will be our base UI node which holds all of our UI nodes inside of it  
- now make this new control node and click layout and change it to *full rect* to encompass the whole game-window   
- rename this UI    
    - now we create our first button 
        - select the UI node and create child node of type *Button* 
        - position this button wherever you want and add some text to it from under the inspector panel     
        - after this you'll get a screen with a rat and a clickable button labeled sword    

## We begin writing our first scripts
for this we select Battle node and click on the script+ icon right next to the search bar       
- a dialog box opens up we confirm everything and click create      
- clear away the pre-existing code      

How is the parent node (Battle) supposed to know when the SwordButton has been pressed?
- it knows via signalling
- the moment the node is pressed SwordButton sends a signal to the Battle node

>It is a good rule that whenever a child needs to communicate with a parent node it will send a signal,       
>whenever a parent needs to control a child it'll just directly access it     
>**Basically signal up but call down**

Now to setup the signal that SwordButton sends to Battle:
- select SwordButton and go to inspector panel and change tab to node
- you'll see a whole host of signa functions
- under basebuttons double click pressed()
- this opens a connect signal:pressed() dialog box
- on the left box in dialog box its all our nodes, select Battle
- now at the bottom we have the path and the method in node (which is basically going to be the name of your function)  
- remember to have make function check marked   
- now click create      

*My version of GODOT does not show the same looking dialog box but does the same thing*     

Now to check if the signaling function is working, under the function print some string to be displayed on the console      
Try saving then run the game (F5), the console should print your string     

## Now we try to update health when we attack
Now to change the HP we need access to the HPLabel
Since HPLabel is a child of Battle we simply need to access it  
- go to the script and setup a var and assign it the node we need like: `var hpLabel = $Enemy/HPLabel`
- but a problem here is that we can't really assign the variable anything until the node gets rendered so we might be shown an error        
- to fix this just use the *onready* keyword like this: `onready var hpLabel = $Enemy/HPLabel`      
- *onready* is only really used when a var needs access to a node in the scene      
- now instead of print we just access the text of the hpLabel and try setting it to some value, to see how it works     




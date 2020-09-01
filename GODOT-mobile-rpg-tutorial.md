# GODOT mobile rpg tutorial     

### We started by installig GODOT and creating a new project    
go to scene box and create custom node      
name node *Battle*      

### we first setup our import settings for our textures                
now since we are going to be using 2D pixel graphics        
we will need to adjust our settings accordingly     
so first try to bring the default godot sprite and go to import tab (top left)      
then set the preset as 2D pixel as default for textures     
just don't forget to reimport       

### now we try to import resources      
now we open up the folder location for the project and simply cut/copy paste the resources in   

### now we basically save the scene (the scene we just named battle)        
then press on the play button and select battle as the scene to show        
after this the debugging dialog box will open but nothing will happpen      
to make this work properly for a mobile game we will have to setup more settings        

### now we configure our actual project settings    
so just go to project-> general tab-> display-> window     
now we set the Width and Height of our display window along with the test Width and test Height     
here the *Width* and *Height* are the actual Width and Height of our game   
this Width and Height are measured in pixels by the way     
set Width: 90, Height: 160, test Width: 360, test Height:640        
test Width and test Height are how many pixels the game will take in windows        
we need to set the above values so that the canvas gets scaled up otherwise it'll look tiny          
save these values and press play, you'll see that the game canvas has changed       



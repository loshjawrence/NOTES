CURRENT: crypt raider 94

### BLUEPRINT TO C++
 * Section 3: Obstacle Assault 42. Compiling a C++ Project
 * Tools -> New C++ Class -> Actor
 * UPROPERTY a macro to decorate a c++ class member variable
 so that it is seen in the editor and editable
## BLUEPRINT CHILD CLASSES
 * drawer->C++ Classes->rclick class->create blueprint based on classname

### DERIVE BLUEPRINT FROM EXISTING
* if in the scene select in window or outliner
and go to details on the rhs click on the node icon
click "derive child blueprint class"
* if in drawer then rclick and "create child blueprint class"

### APPLY CHANGES TO ALL BLUEPRINT INSTANCES
* if in the scene select in window or outliner
and go to details on the rhs click on the node icon
click "apply instance changes to blueprint"

### ADD C++ COMPONENT
Go to C++ Classes folder in contnet drawer and
rclick in file area (or the green + add button)
then select create C++ class.
Or in the detail tab of the scene element,
click add (green plus) then create new c++ component
NOTE: Doesnt add it yet
need to add again and search for you new component then
it will show up in the list of compoents for the scene element

### WORLD OBJECT
* type is UWorld
* map and ULevel is synonymous
* load ULevel's in to the UWorld

### SHERE TRACE
* Can find channels in
<projectRoot>/Config/DefaultEngine.ini
* search "ChannelResponse"
* grab the "Channel=" string
(something like ECC_GameTraceChannel2)
This is the c++ name
* pass that auto generated channel name to GetWorld()->SweepSingleByChannel(...)



### CREATE BLUEPRINT NODES IN C++

### TRACE CHANNEL COLLISION
Creates a filter for scene traversal
so that you only are testing against things
in the "channel"
can do line or geometry(sphere) trace
can keep going or stop on first hit
Settings->Project Settings
->Engine->Collision
->new trace channel
->objects in scene that want that filter
need to say they are attaching collision trace channel
Go to Details panel
Collision->Collision Presets(set to Custom...)
Collision Responses and set to Block
so that it "hits" against the ray
i.e. block the line of sight
* The file where to get the name to use in the code is <repo>/Config/DefaultEngine.ini
 then look for "CollisionResponses"

### INPUT MAPPINGS
## EVENTS WAY:
Project Settings Cog-> Input -> Action Mappings(Press/Release) or Axis Mappings (Continuous/Toggle sticks)
Delete Primary action
Click the + button next to action mappings
Call it Grab(or whatever)
Click the icon and press a button or click a mouse button
Or you can click the drop down and select the gamepad or whatever
To use it go to the player's BP (Probably BP_Player)
Rclick in the blueprint event graph and look for Grab

### BLUEPRINT CALLABLE
## CALL C++ FROM BLUEPRINT
Example
// .h
UFUNCTION(BlueprintCallable)
void Release()
// .cpp
void Grabber::Release()
{
    UE_LOG(LogTemp, Display, TEXT("Grabber Released!"))
}
* Then in the blueprint get a Grabber object, drag off it and search for Release
and link up an event trigger to it (the action mapping)

### ASSETS
After you've made your project go to the
Epic Games launcher->library->find the content and add to project
->show all-> find you project-> select latest version if red->add to project

### LEVEL
* file -> new level

### OPEN VISUAL STUDIO
* tools->visual studio 2022

### 4 VIEW WINDOWS MODE
* the upper right in render window has 4 pane window button
* middle mouse click will measure
* rclick in the ortho views will draw around the view
* upper right box button in any of the 4 windows will maximize the window to full render view

### MOVE/ORGANIZE SCENE/OUTLINER ELEMENTS TO FOLDER
Go to Outliner window-> select elements-> move to-> create new folder

### GRID SNAP
* upper right there are move,scale, rotation snappings
* for move, 100 is a 1 meter snap since 1 unit is 1 cm in unreal

### UNLIT
* Upper left in render window can select various rendering styles

### SKY LIGHT
* quickly add to scene (cube with green plus)
-> lightbulb icon
-> skylight
-> content drawr 
-> upper right settings cog-> show engine content
->engine folder: search bp sky sphere
-> goto skylight in outliner
-> go to "skylight" property and click recapture scene
-> goto bp sky shere and link it to your directional light
with prop "Directional light actor"
then refesh material on the bp sky sphere when ever you rotate
the directional light

### Shortcuts
    * Eject during play:        F8
    * Content Drawer:           Ctrl+Space
    * Play:                     Ctrl+p
    * cursor during play:       shift+F1
    * wireframe:                F1
    * shader cost:              F5
    * move,rot,scale:           w,e,r
    * clone in place:           alt+click move gizmo and drag
    * new level:                ctrl+n
    * box select:               ctrl+alt+lmouse drag

visual scripting nodes
MoveUpdatedComponent - use character movement rules to move the character around
GetActorRotation

Game Mode - An actor that controls game rules for a specific mode
* Go to Main window, go to node icon (list of world blueprints)
* Go to GameMode: New... create then search for "Game Mode Base"
which is the most minimal mode to derive from
* got to class defaults data, go to the classes Section
* change the default pawn class to your player's class
* go back to the node icon menu and make sure None is the world override
* delete the character and drag in  player start actor from the place actors or "quickly add to project" (green plus and cube) 

/////////////////////////////////
////// WRITING TO THE LOG ///////
/////////////////////////////////
uelog
UE_LOG(LogTemp, Display, TEXT("Test log"))
* first is the catagory, log level, finally your text
* For log level see: https://docs.unrealengine.com/4.26/en-US/API/Runtime/Core/Logging/ELogVerbosity__Type/

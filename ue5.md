### Blueprint to C++
 * Section 3: Obstacle Assault 42. Compiling a C++ Project
 * Tools -> New C++ Class -> Actor
 * UPROPERTY a macro to decorate a c++ class member variable
 so that it is seen in the editor and editable
## Blueprint child classes
 * drawer->C++ Classes->rclick class->create blueprint based on classname

Visual Studio
tools->visual studio 2022

### Shortcuts
  * Content Drawer:         Ctrl+Space
  * Play:                   Ctrl+p
  * cursor during play:     shift+F1
  * wireframe:              F1
  * shader cost:            F5
  * move,rot,scale:         w,e,r
  * clone in place:         alt+click move gizmo and drag

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

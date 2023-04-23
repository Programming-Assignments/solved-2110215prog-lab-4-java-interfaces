Download Link: https://assignmentchef.com/product/solved-2110215prog-lab-4-java-interfaces
<br>
<strong>Lab 4: Java Interfaces</strong>

<strong> </strong>

<h1>Instruction</h1>

<ol>

 <li>Click the provided link on CourseVille to create your own repository.</li>

 <li>Open Eclipse and then “File &gt; new &gt; Java Project” and set project name in this format</li>

</ol>

<strong>2110215_Lab4_2021_1_{ID}_{FIRSTNAME}</strong>

<ul>

 <li>Example:<strong> 2110215_Lab4_2021_1_6331234521_Baba</strong>.</li>

</ul>

<ol start="3">

 <li>Initialize git in your project directory ○ <strong>Add .gitignore. </strong>

  <ul>

   <li>Commit and push initial codes to your GitHub repository.</li>

  </ul></li>

 <li>Implement all the classes and methods following the details given in the problem statement file which you can download from CourseVille.

  <ul>

   <li><strong>The provided files contain two folders: </strong>src<strong> and </strong>res<strong>. make sure to add both into your project. (And use both of them as Source Folder)</strong></li>

  </ul></li>

</ol>

○ You should create commits with meaningful messages when you finish each part of your program.

○ Don’t wait until you finish all features to create a commit.

<ol start="5">

 <li>Test your codes with the provided JUnit test cases, they are inside package <strong>grader</strong>

  <ul>

   <li>If you want to create your own test cases, please put them inside package <strong>student</strong></li>

  </ul></li>

</ol>

○ Aside from passing all test cases, your program must be able to run properly without any runtime errors.

○ There will be additional test cases <strong>THAT YOU DO NOT SEE</strong> to test your code after you submit the final version. <strong>Make sure that, not only must your program pass the test cases, it must also follow the specifications in this document closely</strong>.

<ol start="6">

 <li>After finishing the program, create a UML diagram using <strong>ObjectAid or any UML drawing tool (create only all interfaces and the classes that you write the code) </strong>and put the result image at the root of your project folder.</li>

 <li>Export your project into a jar file called <strong>Lab4_2021_1_{ID}</strong> and place it at the root directory of your project.

  <ul>

   <li>Example: <strong>jar</strong></li>

  </ul></li>

 <li>Push all other commits to your GitHub repository.</li>

</ol>










<h1>1. Problem Statement : Prog Meth is You</h1>

<strong> </strong>

You are very famous now, the card game you created is very successful and brings a huge amount of income to the Toy Company. In order to pursue a higher career, you decided to quit the company and become an indie developer.

By sheer coincidence, you come across a veteran indie game developer in a deep mountain. You ask him that you wanted to be trained. However, he said that you must prove that you are worthy by creating a small indie game first.

<h2><strong>1.1</strong>Gameplay</h2>




This game is partially based on <strong>Baba Is You (2019) </strong>by<strong> Hempuli. </strong>However, the rules and elements are stripped down to basic level to make it easier to understand. You are placed in a 2D Grid where you can walk in 4 cardinal directions (Left-Right-Up-Down). You navigate the maze and can push around boxes (only push!) and make the way to the Flag.







<h2>1.2 Prerequisite</h2>

In this assignment, you need to have JavaFX in order to run the project. Don’t worry, you don’t need to do anything with them yet. We will learn more about JavaFX in the following lecture.

For now, if you already have any JavaFX version 11 to 15, you can use them for this assignment. <strong>DO NOT USE version 16 or more since it may not draw our screen correctly</strong>. If you don’t have any JavaFX, however, you can get the latest version from <a href="https://gluonhq.com/products/javafx/">https://gluonhq.com/products/javafx/</a>

Please download the latest release SDK of your OS version. Make sure you tick “include older versions” to make all versions available.




Once extracted the file, move it to somewhere that you think is easily accessible.

The recommended location is “C:Program FilesJava”







To add JavaFX to the project, follow this step.

<ol>

 <li>Right-Click your project &gt; Build Path… &gt; Configure Build Path</li>

 <li>In the Libraries Tab, under Classpath, click <strong>Add External JAR…</strong></li>

 <li>Navigate to the previously extracted JavaFX folder, go to the folder <strong>lib</strong>, and select every jar file in there and click Open.</li>

</ol>







Almost there! You still need to do one last thing before we can run the program.

You need to modify <strong>Run Configurations</strong>.

This can be done by right clicking Main.java &gt; Run As &gt; Run Configurations…

Under Arguments tab, in the VM arguments section, place this command in




–module-path “&lt;path to your JavaFX folder&gt;lib” –add-modules javafx.controls,javafx.graphics,javafx.media,javafx.fxml




For example,

–module-path “C:Program FilesJavajavafx-sdk-12.0.2lib” -add-modules javafx.controls,javafx.graphics,javafx.media,javafx.fxml




Afterwards, click Run and you will be able to run the program from now on.

<ol start="2">

 <li><strong> Implementation Details: </strong></li>

</ol>

<strong> </strong>

To complete this assignment, you need to understand about <strong>Interfaces</strong>.

This assignment gives you more freedom over how you can implement the solution. There are <strong>more than one</strong> possible ways that the final class diagram could look like, so we will <strong>not</strong> provide a class diagram.

There are <strong>four</strong> packages in the provided files: application, entity, logic and test.

You will be implementing most of the class in the entity package (Only a few classes are provided, you need to implement the rest from scratch)

You will also need to modify some of the code in the Main.java under application package. The details will be specified later in the document.

There are some test cases given in package test.grader. These will help test your code whether it will be able to run or not. However, <strong>some conditions are not tested </strong>in these test cases. If you need to test more conditions, please create your own test case in test.student package. However, Your own test cases are optional, and won’t be graded.

<strong>You can define any additional number of <u>private</u> (but not public, protected or package) fields and methods</strong> in addition to the fields and methods specified below. You are encouraged to try to group your logic into private methods to <strong>reduce duplicate code as much as possible</strong>.




Do note that only relevant methods related to logic will be explained.

Anything else such as Rendering is already handled for you in this Exercise.




<em>* Noted that Access Modifier Notations are listed below      <strong>             </strong></em>

+ (public)

# (protected)

– (private) <u>Underline</u> (static) <em>Italic (abstract)</em>




<h2><strong>2.1</strong> package logic</h2>

This package’s content is already provided for you. You do NOT need to edit anything to complete this assignment. However, you might need to use these methods to help with your implementation.







<h3>2.1.1 Enum Direction</h3>

This enum represents direction. It contains the following values: LEFT, RIGHT, UP, DOWN and NONE.

Example Usage:

Direction dir = Direction.LEFT; //This represent the value of left direction.

<h3>2.1.2 Class GameController</h3>

This class is the game system. Most of the game’s global variable are kept here. 2.1.2.1 Methods

<table width="624">

 <tbody>

  <tr>

   <td width="312"><u>+ void IntializeMap()</u></td>

   <td width="312">Load the data and initialize he sample map, as well as resets all the global variables.</td>

  </tr>

  <tr>

   <td width="312"><u>+ GameMap getCurrentMap()</u></td>

   <td width="312">Get the active map</td>

  </tr>

  <tr>

   <td width="312"><u>+ void movePlayer(Direction dir)</u></td>

   <td width="312">Move the player with the direction dir. (It just call method move(Direction dir) of the Player object) This also calls method update() on the Entity that implements the interface Updatable.</td>

  </tr>

  <tr>

   <td width="312"><u>+ int getCoinCount()</u><u>+ void setCoinCount(int coin_count)</u><u>+ void addCoinCount(int coin_count)</u></td>

   <td width="312">Getter/Setter/Add for the field coin_count, which is the amount of the Coin player has collected.</td>

  </tr>

  <tr>

   <td width="312"><u>+ boolean isGameWin()</u><u>+ void setGameWin(boolean is_win)</u></td>

   <td width="312">Getter/Setter for the field is_win, which is the status if the player has won or not.</td>

  </tr>

  <tr>

   <td width="312"><u>+</u><u> boolean getGameSwitchStatus()</u><u>+ </u><u>void setGameSwitchStatus(boolean game_switch)</u></td>

   <td width="312">Getter/Setter for the field game_switch, which is the status of the in-game Switch object.</td>

  </tr>

 </tbody>

</table>

<strong> </strong>

<h4><strong>2.1.3 Class </strong><strong>GameMap</strong></h4>

This class represent Map, which is a grid that contains many Cells.

<h5>2.1.3.1 Constructors</h5>

<table width="624">

 <tbody>

  <tr>

   <td width="310">+ GameMap(int column,int row)</td>

   <td width="314">Intialize an empty map with the specified size.</td>

  </tr>

  <tr>

   <td width="310">+ GameMap(String[][] map)</td>

   <td width="314">Initialize a map with the content loaded fromString[][] map</td>

  </tr>

 </tbody>

</table>

<h5>2.1.3.2 Methods</h5>

<table width="624">

 <tbody>

  <tr>

   <td width="341">+ boolean addEntity(Entity e,int x, int y)</td>

   <td width="283">Adds Entity e into the cell at position (x,y) This will trigger Cell’ssetEntity(Entity e) method</td>

  </tr>

  <tr>

   <td width="341">+ Entity getEntity(int x,int y)</td>

   <td width="283">Get Entity of the cell at the position (x,y)</td>

  </tr>

  <tr>

   <td width="341">+ void removeEntity(int x,int y)</td>

   <td width="283">Removes Entity from the cell at the position (x,y)</td>

  </tr>

  <tr>

   <td width="341">+ isMovePossible(int targetx,int targety,Entity e)</td>

   <td width="283">Check if it is possible or not to moveEntity e to the target position(targetx,targety) If the target position is empty, it returns true.Otherwise, return false unless the Entity at the target cell implements the interface Interactable, in which it triggers and check the result of the interaction using  interact(Entity e) instead. It is guaranteed that this method will return false if the target position is outside the map.</td>

  </tr>

  <tr>

   <td width="341">+ ArrayList&lt;Entity&gt; getAllEntity()</td>

   <td width="283">Get the list of all Entity in the map</td>

  </tr>

 </tbody>

</table>

<strong> </strong>







<h4><strong>2.1.4 Class </strong><strong>Cell</strong></h4>

This class represents a cell, which is a single square in a map grid. Only one Entity can be in one cell at a time.

<h5> 2.1.4.1 Methods</h5>

<table width="624">

 <tbody>

  <tr>

   <td width="312">+ boolean IsEmpty()</td>

   <td width="312">Returns true if the cell is empty</td>

  </tr>

  <tr>

   <td width="312">+ boolean setEntity(Entity e)</td>

   <td width="312">Set the Entity e to this cell.If the cell is empty, then the Entity e will be assign as the Entity for this cell and returns true Otherwise, return false and trigger method consume(Entity e) if the Entity that occupied this cell implements the interface Consumable.</td>

  </tr>

  <tr>

   <td width="312">+ Entity getEntity()</td>

   <td width="312">Get the current Entity that occupied this cell.</td>

  </tr>

  <tr>

   <td width="312">+ void removeEntity()</td>

   <td width="312">Remove the current Entity from this cell.</td>

  </tr>

 </tbody>

</table>

<strong> </strong>

<h4><strong>2.1.5 Class </strong><strong>Sprites</strong></h4>

This class contains the constant using for rendering.  It is only for organization purpose. Usage for this class will be specified later.







<strong>2.2 </strong>package entity.base

<h5>2.2.1 Abstract Class Entity</h5>

This class is the base class for all Entity in the map. This class ensures that every Entity has enough methods to work.

You do NOT need to modify this class to complete the assignment.

<h6>2.2.1.1 Constructor</h6>

<table width="624">

 <tbody>

  <tr>

   <td width="294">+ Entity ()</td>

   <td width="331">Initialize the private fields.</td>

  </tr>

  <tr>

   <td width="294">2.2.1.2 Methods</td>

   <td width="331"></td>

  </tr>

  <tr>

   <td width="294">+ <em>int getSymbol()</em></td>

   <td width="331">This method returns the index symbol that</td>

  </tr>

  <tr>

   <td width="294"></td>

   <td width="331">represent the Entity during rendering. Do not worry about this one as the value for each type will be specified below.</td>

  </tr>

  <tr>

   <td width="294">+ boolean move(Direction dir)</td>

   <td width="331">Move the current Entity one unit in the specified direction. This also calls isMovePossible (targetx, targety,this)on the current game map to check if it can move or not. This method returns true if the move is successful, false if not. It is guaranteed that the result is always correct if you are implemented other stuff correctly.</td>

  </tr>

  <tr>

   <td width="294">+ void remove();</td>

   <td width="331">Remove this Entity from the board</td>

  </tr>

  <tr>

   <td width="294">+ int getDirection()+ void setDirection(int direction)</td>

   <td width="331">Getter/Setter for the field directionWhich is the direction that the Entity currently facing. It is always set each time it moves.</td>

  </tr>

 </tbody>

</table>

<strong> </strong>

<h5>2.2.2 Interface Interactable</h5>

This interface defines methods for Entity that can be interacted with.

<h6>2.2.2.1 Method</h6>

<table width="624">

 <tbody>

  <tr>

   <td width="296">+ <em>boolean interact(Entity e)</em></td>

   <td width="328">This method is called when the Entity e checks for moveable space. It returns true if the results of the interaction let the Entity e pass through.Otherwise, return false. <strong>Note:</strong> Anything that occur during the moment of the interaction should be placed here as well.More detail will be provided in each Object.</td>

  </tr>

 </tbody>

</table>

<strong> </strong>

<strong> </strong>

<strong> </strong>

<strong> </strong>

<strong> </strong>

<strong> </strong>

<h5>2.2.3 Interface Consumable</h5>

This interface defines methods for Entity that consumes another Entity when it overlapped.

<h6>2.2.2.1 Method</h6>

<table width="624">

 <tbody>

  <tr>

   <td width="296">+ <em>boolean consumes(Entity e)</em></td>

   <td width="328">This method is called when the Entity e is being added onto the same space. It returns true if the main Entity can consumeEntity e.Otherwise, return false. <strong>Note:</strong> Anything that occur during consuming should be placed here as well. More detail will be provided in each Object.</td>

  </tr>

 </tbody>

</table>

<strong> </strong>

<h5>2.2.4 Interface Updatable</h5>

This interface defines methods for Entity that is can update itself once every player action.

<h6>2.2.2.1 Method</h6>

<table width="624">

 <tbody>

  <tr>

   <td width="296">+ <em>void update() throws </em><em>IllegalValueException</em></td>

   <td width="328">This method is called when the player made a move. Do note that it is possible that this method can throws an exception. <strong>Note:</strong> Do not add or remove (including move) any Entity during this step. As it can cause a problem when iterating through Entity list. It is guaranteed that you will not do that during this assignment.</td>

  </tr>

  <tr>

   <td width="296">+ <em>void valueCorrection()</em></td>

   <td width="328">This method should be called to reset the incorrect value when encountering an exception.</td>

  </tr>

  <tr>

   <td width="296"></td>

   <td width="328"> <strong>You need to modify code inside Main.java so that this method is called when handling an exception from update() </strong><strong> </strong><strong>Hint: </strong>Use try…catch</td>

  </tr>

 </tbody>

</table>

<h2><strong>2.3 </strong>package entity</h2>




This package contains implementation of the <strong>concrete </strong>Entity. Only the class that you need to create will be listed here. All classes must be created from scratch.

<h3>2.3.1 Class Box</h3>

Implements: Interactable

This class represent Box type Entity, which can be pushed around.

<h4>2.3.1.1 Methods</h4>

<table width="624">

 <tbody>

  <tr>

   <td width="293">+ int getSymbol()</td>

   <td width="331">return the value Sprites.BOX Which contains the correct value of the subimage used to render the box.</td>

  </tr>

  <tr>

   <td width="293">+ boolean interact(Entity e)</td>

   <td width="331">Move the box in the same direction as Entity e Returns the result of the move</td>

  </tr>

 </tbody>

</table>

<h3>2.3.2 Class Coin</h3>

Implements: Interactable

This class represent Coin type Entity, which can be collected by either player or pushing

things to it.

<h4>2.3.2.1 Methods</h4>

<table width="624">

 <tbody>

  <tr>

   <td width="293">+ int getSymbol()</td>

   <td width="331">return the value Sprites.COIN Which contains the correct value of the subimage used to render the coin.</td>

  </tr>

  <tr>

   <td width="293">+ boolean interact(Entity e)</td>

   <td width="331">Remove the Coin and increment coin counts in GameController by 1. This method returns true because the coin is passable after it has been collected.</td>

  </tr>

 </tbody>

</table>

<strong> </strong>

<h3>2.3.3 Class Flag</h3>

Implements: Interactable

This class represent Flag type Entity, which can be collected by player only. Player cannot push anything on top of it to collect, unlike Coins.

<h4>2.3.3.1 Methods</h4>

<table width="624">

 <tbody>

  <tr>

   <td width="293">+ int getSymbol()</td>

   <td width="331">return the value Sprites.FLAG Which contains the correct value of the subimage used to render the flag.</td>

  </tr>

  <tr>

   <td width="293">+ boolean interact(Entity e)</td>

   <td width="331">If the Entity e is Player, then remove the Flag and set win status of the game inGameController. Then returns true afterward. For other type of Entity e, returns false. To make them not be able to pass through.</td>

  </tr>

 </tbody>

</table>

<h3>2.3.4 Class Door</h3>

Implements: Interactable, Consumable

This class represent Door type Entity, it blocks anything for the most part. Except if it collide with the key, it disappear.

<h4>2.3.4.1 Methods</h4>

<table width="624">

 <tbody>

  <tr>

   <td width="293">+ int getSymbol()</td>

   <td width="331">return the value Sprites.DOOR Which contains the correct value of the subimage used to render the door.</td>

  </tr>

  <tr>

   <td width="293">+ boolean interact(Entity e)</td>

   <td width="331">Returns true if Entity e is Key. Otherwise returns false. This is because it needs to be overlapped with Key to trigger consume() method.</td>

  </tr>

  <tr>

   <td width="293">+ boolean consume(Entity e)</td>

   <td width="331">Since this Entity can only consumes Key, it returns true if Entity e is Key, and then remove itself.Otherwise returns false.</td>

  </tr>

 </tbody>

</table>

<h3>2.3.5 Class Switch</h3>

Implements: Interactable, Updatable

This class represent Switch type Entity. It is a solid object that flips switch every time the player interacts with it. If there are multiple switches on the screen, all switches should be updated to match the global Game Switch state.

<h4>2.3.5.1 Fields</h4>

<table width="624">

 <tbody>

  <tr>

   <td width="293">– boolean isActive</td>

   <td width="331">A boolean to keep track if the switch has been flipped or not.</td>

  </tr>

  <tr>

   <td width="293">2.3.5.2 Constructor</td>

   <td width="331"></td>

  </tr>

  <tr>

   <td width="293">+ Switch()</td>

   <td width="331">Initialize the isActive with the value from the GameController.</td>

  </tr>

 </tbody>

</table>

<h4>2.3.5.3 Methods</h4>

<table width="624">

 <tbody>

  <tr>

   <td width="293">+ int getSymbol()</td>

   <td width="331">return the value Sprites.SWITCH_ON if the switch is active or Sprites.SWITCH_OFF otherwise. These contains the correct value of the subimage used to render the switch.</td>

  </tr>

  <tr>

   <td width="293">+ boolean interact(Entity e)</td>

   <td width="331">If the Entity e is Player, then flip the game switch state in GameController. This method always returns false. As this is solid object.</td>

  </tr>

  <tr>

   <td width="293">+ void update()</td>

   <td width="331">Update the switch’s own isActive field value to match global game switch state inGameController.</td>

  </tr>

  <tr>

   <td width="293">+ void valueCorrection()</td>

   <td width="331">Since there is no Exception being thrown here, this method can be left empty.</td>

  </tr>

  <tr>

   <td width="293">+ boolean isActive()+ void setActive(boolean isActive)</td>

   <td width="331">Getter/Setter for isActive</td>

  </tr>

 </tbody>

</table>

<h3>2.3.6 Class ColorBox</h3>

Implements: Interactable

This class represent Colored Box type Entity. It is a solid object that can be pushed around like Box, but only when the game’s global switch matched their internal value.

<h4>2.3.6.1 Fields</h4>

<table width="624">

 <tbody>

  <tr>

   <td width="293">– boolean activeBool</td>

   <td width="331">A boolean contains the game switch state that the box can be pushed.</td>

  </tr>

  <tr>

   <td width="293">2.3.6.2 Constructor</td>

   <td width="331"></td>

  </tr>

  <tr>

   <td width="293">+ ColorBox (boolean activeBox)</td>

   <td width="331">Initialize activeBool</td>

  </tr>

 </tbody>

</table>

<h4>2.3.6.3 Methods</h4>

<table width="624">

 <tbody>

  <tr>

   <td width="293">+ int getSymbol()</td>

   <td width="331">return the value Sprites.BOX_RED if the box active on the switch value true orSprites.SWITCH_BLUE otherwise. These contains the correct value of the subimage used to render the colored box.</td>

  </tr>

  <tr>

   <td width="293">+ boolean interact(Entity e)</td>

   <td width="331">If the game’s global switch matches the activeBool, move the box in the same direction as Entity e and returns the result of the move. Otherwise, returns false.</td>

  </tr>

  <tr>

   <td width="293">+ boolean getActiveBool()+ void setActiveBool(boolean activeBool)</td>

   <td width="331">Getter/Setter for activeBool</td>

  </tr>

 </tbody>

</table>




<h3>2.3.7 Class TrashCompactor</h3>

Implements: Interactable, Consumable, Updatable

This class represent Trash Compactor type Entity. It is a solid object. However, it can consume any type of Box (Box, ColoredBox) if pushed into it, and then entering cooldown mode. During the cooldown mode, it cannot consume any Box.  The cooldown timer ticks down once the player made a movement.

<h4>2.3.7.1 Fields</h4>

<table width="624">

 <tbody>

  <tr>

   <td width="293">– int cooldown</td>

   <td width="331">A cooldown time, the Trash Compactor is only functional if the cooldown time is 0.</td>

  </tr>

 </tbody>

</table>

<h4>2.3.7.2 Constructor</h4>

<table width="624">

 <tbody>

  <tr>

   <td width="293">+ TrashCompactor ()</td>

   <td width="331">Initialize cooldown with 0</td>

  </tr>

 </tbody>

</table>

<h4>2.3.7.3 Methods</h4>

<table width="624">

 <tbody>

  <tr>

   <td width="305">+ int getSymbol()</td>

   <td width="319">return the value Sprites.COMPACTOR_ON if the Trash Compactor is usable. ReturnsSprites.COMPACTOR_OFF otherwise These contains the correct value of the subimage used to render the Trash Compactor.</td>

  </tr>

  <tr>

   <td width="305">+ boolean interact(Entity e)</td>

   <td width="319">Returns true if the Entity e is a type of box and the Compactor is active to allow them to pass. Returns false otherwise to block them. <strong>Tip:</strong> You can use Entity.isBox(Entitye) to check if Entity e is a type of box or not.</td>

  </tr>

  <tr>

   <td width="305">+ boolean consume(Entity e)</td>

   <td width="319">Returns true if the Entity e is a type of box and the Compactor is usable to consume the Entity, as well as setting the cooldown time to the value ofGameController.MAX_COOLDOWN_TIME. Returns false otherwise. <strong>Tip:</strong>  You can use Entity.isBox(Entitye) to check if Entity e is a type of box or not.</td>

  </tr>

  <tr>

   <td width="305">+ void update() throws IllegalValueException</td>

   <td width="319">Decrease its cooldown value by 1 if it’s more than 0 If cooldown is          less    than    0,      throwsIllegalValueException</td>

  </tr>

  <tr>

   <td width="305">+ void valueCorrection()</td>

   <td width="319">Set cooldown to 0</td>

  </tr>

  <tr>

   <td width="305">+ int getCooldown()+ void setCooldown(int cooldown)</td>

   <td width="319">Getter/Setter for cooldown</td>

  </tr>

 </tbody>

</table>




<strong> </strong>

<strong> </strong>



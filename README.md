# AR-whack-a-mole
This repo holds a project for Cornell Tech IDD class in Fall 2021

Jiahao Dong(jd787), Shenxin Jiang(jians10)


## Abstract:

After a semester studying all kinds of sensers that can be used in an interactive devices, we would like to introduce a new way to play the classic Whac-A-Mole Game. Two players can now play against each other on an Arduino Gameboy and a web browser! One player will be placing the mole on the board, while the other controlling the hammer and try to hit the mole. In a simulated AR setting, the player will be able to "whack" a mole using his/her own hand as a hammer. Player will still have a hit feedback without any pysical contact. In the end, we implement the game using pygame and utilize Pyautogui to let the user control the cursor by simply waving their hands to a camera. After setting up the server, we find its too hard for a Raspeberry Pi to handle OpenCv and pygame at the same time while host a server. After several experiment, we finally reached a solution while we didn't use the game we created and implement the game elements and logic right into a OpenCv script. 

## Initial Plan and Design of the Game:

### State Graph:
![Screen Shot 2021-12-13 at 1 13 10 PM](https://user-images.githubusercontent.com/61925885/145865967-265af52a-0b59-4219-8bec-2153f0c89762.png)

### The structure of the interaction:
![Screen Shot 2021-12-13 at 1 14 20 PM](https://user-images.githubusercontent.com/61925885/145866138-4fcb48c6-d354-4307-a83b-02878c5d5347.png)

### How to Play:

#### Player on Arduino
Controls the snake, chases the food.
The person playing on the Arduino will see a real-time game view on the screen and control the position of the hammer use the position of their own hand and use gesture control to manipulation hammer’s movement.

#### Player on the Computer
Places foods, challenges the snake.
The person playing on the computer will see a real-time game view on the webpage and can place the mole (in green) anywhere on the board. Also, the position of the hammer will also be synchronized on the screen.

#### Rules
Only one mole can be present on the board at any moment. If the time run up then the game end

#### Starting the Game
Both the Arduino and the web client need to be connected to play. As soon as the player on Arduino presses the joystick, the game will start.

#### Restarting the Game
The game can simply be restarted by refreshing the webpage on the browser.






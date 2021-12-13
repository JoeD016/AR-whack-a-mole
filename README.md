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

### Player on Arduino
Controls the snake, chases the food.
The person playing on the Arduino will see a real-time game view on the screen and control the position of the hammer use the position of their own hand and use gesture control to manipulation hammer’s movement.

### Player on the Computer
Places foods, challenges the snake.
The person playing on the computer will see a real-time game view on the webpage and can place the mole (in green) anywhere on the board. Also, the position of the hammer will also be synchronized on the screen.

### Rules
Only one mole can be present on the board at any moment. If the time run up then the game end

### Starting the Game
Both the Arduino and the web client need to be connected to play. As soon as the player on Arduino presses the joystick, the game will start.

### Restarting the Game
The game can simply be restarted by refreshing the webpage on the browser.


## Functioning project:

### Set up:
Our set up is fairly simple, a Raspeberry Pi with a connected camera and a display (monitors, tvs, projecters)

![IMG_5692](https://user-images.githubusercontent.com/61925885/145867526-39345ca1-41ca-494d-bbe6-51d80676cd4e.jpg)

![IMG_5691](https://user-images.githubusercontent.com/61925885/145867534-d2696f39-6692-4dcb-9345-4ebb7ae52dc2.jpg)

### Design Process and Issue Solving:

The first demo video documenting our process can be found [here](https://www.youtube.com/watch?v=FOm_WkcUAoI).

In the game part, we manualy designed our "mole" in pixels and we tricked its position in the gameplay once it get hits to achieve the hit feedback. In the OpenCv part, we use Pyautogui to move the cursor along with the detected hand-pose. 

All components functions well in the video but if we combine them together, the GPU inside the Raspberry Pi will just crash.

### Chenge the Design:

Since the multiplayer version of the Whack-a-Mole actually reduces game’s playability(due to limited GPU power in Pi). We decided to remove the multiplayer part in this game.

The attack animation is removed because raspberry cannot run PYGAME and OpenCV at the same time. In comparison, a ubuntu computer can successfully run our game smoothly with animation and attack effect). Maybe we need better device.

## Final video Demo can be found [here]().

## Reflections on process:
We should've think more thoroughly about the capability of our device, what we want to create is, in the first place, limited by the device we have on hand. We found it out after we have already code the game in Pygame and draw our attack animation tick by tick. Overall we wouldn't say this is a wast of time, but it does not contribute to our project. If we would know it sooner, we will have more time adding other sensors to make a more interesting interaction.


## Group work distribution:

Jiahao Dong: Enviroment setup, algorithm optimization and debugging.

Shenxin Jiang: Game design, implementation of game state machine and UI element.



# Unity_Coding_Summit
Hello!

## **Create New Project**

Open Unity and create a new Project by clicking the "New" button.

## **Game**

**1. Assets**

You can get download the needed assets from [here](https://drive.google.com/drive/folders/1atnrjGfaNKNqSvXR9pbFD1vw5IOXK9C7?usp=sharing)

**2. Character Prefab**

Create a prefab of our main character by dragging the "spaceship item" into the scene and then back to the project panel.
       
**3. Player Movement**

Create an empty game game object in the hierarchy and call it "codeHolder". Go to the inspector menu while your new object is selected and click AddComponent --> New Script and name it Game. In your Game script, create a public GameObject called "player". In the Update() method, we are going to create our spaceship's movement by getting the keyboard input, and "transforming", moving rather, our object's Rigidbody2D. 

Once the code is written, go back into Unity and while your spaceship is selected click AddComponent --> Rigidbody2D. Change Gravity Scale to 0 and Linear Drag to 5. 

**4. Spaceship Animation**

Right-click on the project panel and click Create --> Animation. Drag your animation to your "spaceship" object in the scene to create an animation controller. Go to the animation panel at the bottom and click the red record button while the spaceship is selected from the hierarchy. Click on the button next to the Sprite option in the SpriteRenderer component in the inspector and change it to "player". You will see that a frame is formed at time 0:00. Next, click on the 0:10 time-frame and do the same process in the sprite renderer, this time changing it to "move big". Click on the 0:20 time frame and change the sprite back to "player". Once you are done, stop recording and click on the play button in the animation tab to see the animation running. CLick on the animation in the project panel and clikc "Loop Time" on the inspector. When you start the game, the animation should be running infinitely.

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

Right-click on the project panel and click Create --> Animation. Drag your animation to your "spaceship" object in the scene to create an animation controller. Go to the animation panel at the bottom and click the red record button while the spaceship is selected from the hierarchy. Click on the button next to the Sprite option in the SpriteRenderer component in the inspector and change it to "player". 

<img width="258" alt="d" src="https://user-images.githubusercontent.com/24539923/37401748-24d095ce-279a-11e8-8805-67ef8fd68304.png">

You will see that a frame is formed at time 0:00. Next, click on the 0:10 time-frame and do the same process in the sprite renderer, this time changing it to "move big". Click on the 0:20 time frame and change the sprite back to "player". Once you are done, stop recording and click on the play button in the animation tab to see the animation running. 

<img width="713" alt="e" src="https://user-images.githubusercontent.com/24539923/37401930-c811abc4-279a-11e8-9a1c-4b91a523bb56.png">

CLick on the animation in the project panel and clikc "Loop Time" on the inspector. 

<img width="192" alt="c" src="https://user-images.githubusercontent.com/24539923/37401624-bd3a5f4e-2799-11e8-819c-ef964e642510.png">

When you start the game, the animation should be running infinitely.

<img width="137" alt="b" src="https://user-images.githubusercontent.com/24539923/37401580-94250ece-2799-11e8-8e1f-b41ac8d14a4d.png">

**5. Bullet**

Go back into your Game script and create a new public GameObject called "bullet". Also, create a public staticc boolean called "can_spawn_bullet" and set it to true. Next in the Update() method, we are going to write a code block that shoots a bullet when we press the space bar. We write an if statement which checks if we get input from the space bar. Inside a that if, write another if, this time writing can_spawn_bullet as the conditional. If can_spawn_bullet is true, so if we can shoot, shoot the bullet. However, the shooting mechanic is basically spawning our bullet object inside our player and making it move toward the right side of the screen. We can do this using the Instantiate method. After we spawn the desired object in the desired position with the desired rotation, we give it a veloicty so it can move. But if when we spawn the bullet inside the spaceship, they might collide and bug out. So we use the IgnoreCollision method so that we prevent this from happening. Then, we set our can_spawn_bullet boolean to true.

When we go back to Unity, we create a bullet prefab by dragging it to the scene and back to the project panel and assign that prefab to the bullet slot in the Game script Then, we add BoxCollider2D components to both our bullet prefab and spaceship prefab. We also add a Rigidbody2D component to our bullet prefab, setting Gravity Scale and Angular Drag to 0. When we run the game, we can see that it is working, but it fires infinitely. To prefent this, we are going to create a basic timer. Go back to your Game script and create a public static float bullet_start and set it to 0. In the if statement where we spawn our bullets, set bullet_start to Time.time, the time that passes since we started running the game. Create a new if statement setting the conditional as Time.time-bullet_start >= 0.2, meaning that shoot the bullet every 0.2 seconds. Inside this if, set out can_spawn_bullet boolean to true. When we go back to unity and run the game, we see that it works perfectly

<img width="351" alt="screen shot 2018-03-16 at 12 15 32" src="https://user-images.githubusercontent.com/24539923/37512690-e4738718-2913-11e8-85a6-690aef8db03c.png">

<img width="984" alt="screen shot 2018-03-16 at 12 16 08" src="https://user-images.githubusercontent.com/24539923/37512697-e8b16d7c-2913-11e8-9cfe-6ab8a9324224.png">

**6. Screen Limits**

Right now, if you continue to go up, down, left or right with the spaceship, it is possible to go out of the screen. To prevent this we are going to manually create invisible walls. In the hierarchy create an empty game object and a box collider component. Alter the collider's size so that it is equal to or larget than the camera's vertical component. Repeat this same process for the other sides of the camera. Then create another emppty game objects and call it "walls". Drag the other four objects into it (just to make our hierarchy more clean .) )

<img width="194" alt="screen shot 2018-03-16 at 12 33 22" src="https://user-images.githubusercontent.com/24539923/37513515-5a40f230-2916-11e8-8919-3dfc98552056.png">

<img width="318" alt="screen shot 2018-03-16 at 12 33 32" src="https://user-images.githubusercontent.com/24539923/37513517-5a633ffc-2916-11e8-8a34-32b2d0f10b17.png">

**7. Esthetics, Life Icons and Background**

Let's start with the background color. Click on the main camera and in the inspector, change the color next to "Background". For now, let's change it to black. Next, let's scale down our spacehip a bit. In the inspector, change the X and Y components of "Scale" to 3. Now, let's create our icons for our health. Right click in the hierarchy and create UI --> Text. A canvas along with the text will form. Drag the text to the top-left corner in the canvas and change its color to white. From the inspector, change "Text" to "Lives:". Next, drag a "health full" from the project panel to the hierarchy. Duplicate it twice and put them side by side next to the lives text. Now, we have our UI for our health ready. Later, we are going to link the UI with the damage that the spaceship takes.

<img width="167" alt="screen shot 2018-03-16 at 12 57 20" src="https://user-images.githubusercontent.com/24539923/37514731-c1236b60-2919-11e8-9d13-c252569a9df6.png">

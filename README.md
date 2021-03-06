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

Go back into your Game script and create a new public GameObject called "bullet". Also, create a public static boolean called "can_spawn_bullet" and set it to true. Next in the Update() method, we are going to write a code block that shoots a bullet when we press the space bar. We write an if statement which checks if we get input from the space bar. Inside a that if, write another if, this time writing can_spawn_bullet as the conditional. If can_spawn_bullet is true, so if we can shoot, shoot the bullet. However, the shooting mechanic is basically spawning our bullet object inside our player and making it move toward the right side of the screen. We can do this using the Instantiate method. After we spawn the desired object in the desired position with the desired rotation, we give it a veloicty so it can move. But if when we spawn the bullet inside the spaceship, they might collide and bug out. So we use the IgnoreCollision method so that we prevent this from happening. Then, we set our can_spawn_bullet boolean to true.

When we go back to Unity, we create a bullet prefab by dragging it to the scene and back to the project panel and assign that prefab to the bullet slot in the Game script Then, we add BoxCollider2D components to both our bullet prefab and spaceship prefab. We also add a Rigidbody2D component to our bullet prefab, setting Gravity Scale and Angular Drag to 0. When we run the game, we can see that it is working, but it fires infinitely. To prefent this, we are going to create a basic timer. Go back to your Game script and create a public static float bullet_start and set it to 0. In the if statement where we spawn our bullets, set bullet_start to Time.time, the time that passes since we started running the game. Create a new if statement setting the conditional as Time.time-bullet_start >= 0.2, meaning that shoot the bullet every 0.2 seconds. Inside this if, set out can_spawn_bullet boolean to true. When we go back to unity and run the game, we see that it works perfectly

<img width="351" alt="screen shot 2018-03-16 at 12 15 32" src="https://user-images.githubusercontent.com/24539923/37512690-e4738718-2913-11e8-85a6-690aef8db03c.png">

<img width="984" alt="screen shot 2018-03-16 at 12 16 08" src="https://user-images.githubusercontent.com/24539923/37512697-e8b16d7c-2913-11e8-9cfe-6ab8a9324224.png">

**6. Screen Limits**

Right now, if you continue to go up, down, left or right with the spaceship, it is possible to go out of the screen. To prevent this we are going to manually create invisible walls. In the hierarchy create an empty game object and a box collider component. Alter the collider's size so that it is equal to or larget than the camera's vertical component. Repeat this same process for the other sides of the camera. Then create another empty game objects and call it "walls". Drag the other four objects into it (just to make our hierarchy more clean .) )

<img width="194" alt="screen shot 2018-03-16 at 12 33 22" src="https://user-images.githubusercontent.com/24539923/37513515-5a40f230-2916-11e8-8919-3dfc98552056.png">

<img width="318" alt="screen shot 2018-03-16 at 12 33 32" src="https://user-images.githubusercontent.com/24539923/37513517-5a633ffc-2916-11e8-8a34-32b2d0f10b17.png">

**7. Aesthetics, Life Icons and Background**

Let's start with the background color. Click on the main camera and in the inspector, change the color next to "Background". For now, let's change it to black. Next, let's scale down our spacehip a bit. In the inspector, change the X and Y components of "Scale" to 3. Now, let's create our icons for our health. Right click in the hierarchy and create UI --> Text. A canvas along with the text will form. Drag the text to the top-left corner in the canvas and change its color to white. From the inspector, change "Text" to "Lives:". Next, drag a "health full" from the project panel to the hierarchy. Duplicate it twice and put them side by side next to the lives text. Now, we have our UI for our health ready. Later, we are going to link the UI with the damage that the spaceship takes.

<img width="167" alt="screen shot 2018-03-16 at 12 57 20" src="https://user-images.githubusercontent.com/24539923/37514731-c1236b60-2919-11e8-9d13-c252569a9df6.png">

<img width="218" alt="screen shot 2018-03-16 at 12 58 00" src="https://user-images.githubusercontent.com/24539923/37514732-c144a42e-2919-11e8-810f-40b5184a7147.png">

**8. Bullet Collision and Spawn Time**

Create a new script called "BulletScript" and add it to your bullet prefab. Create a private float called spawn_time and set it to 0. In the Start() method, reset it to Time.time. In the Update() method, write an if statement, setting the conditional to Time.time - spawn_time > 1, meaning that the bullet will only appear in the game for 1 second. In the if statement, write Destroy(gameObject), meaning that the bullet will destroy itself.

Create a new void called OnCollisionEnter2D with the paramatet "Collision2D col". Create an if statement and give it the conditional col.gameObject.tag == "wall", meaning that if the bullet collides with our wall, the bullet will be destroyed. For this, write the same destroy method in the if statement. Save the code and return to unity. Go to our wall objects and create and add a new tag called "wall" from the inspector. Now when we shoot, the bullet is destroyed when it collides with the walls.

<img width="116" alt="screen shot 2018-03-16 at 13 09 10" src="https://user-images.githubusercontent.com/24539923/37515261-48bcdef2-291b-11e8-9415-fdc26969221d.png">

<img width="360" alt="screen shot 2018-03-16 at 13 09 24" src="https://user-images.githubusercontent.com/24539923/37515262-48dfe80c-291b-11e8-9570-52f6736704c5.png">

**9. Enemies and Health**

Create a new script called Enemy and add it to the enemy prefab. Add 4 new floats called wanted_x, wanted_y, x and y. Create a int called health and set it to 2 (or 1 if you want to). Add two GameObjects named player and enemy_bullet and go to the inspector and add these prefabs. (You must duplicate the bullet and name it to enemy_bullet. Add a boolean called hard_enemy and set it to false. (If you want to make 2 types of enemies, easy and hard.) To let the enemy shoot, add a float named bullet_start and set it to 0; add a boolean named can_spawn_bullet and spawn it to true and add a Quaternion named rotation and set it to new Quaternion(0,0,0,0). In the Start() void, increment Game.enemies_on_screen by 1.

Lets get in to the Update() void. Set x and y to 0. Write an if statement and write transform.position.x (get the enemy object's current x position) > wanted_x (the place where we want it to be at). In the if statement, set x to -0.1f and wanted_x to -5. Create an else if and make its condition transform.position.x < wanted_x and inside it set x to 0.1f and set wanted_x to 5. Create another if/else if statement and make the same for the y value, but this time set wanted_y to -4 and 4 instead. After that write transform.Translate(x,y,0). Create an if statement and make its condition can_spawn_bullet. Inside it create a bullet with instatiation and give it the velocity -transform.right * 10f. You will also want an IgnoreCollision between the bullet spawned and the enemy object. Also write an if with the condition hard_enemy and make it shoot another bullet so the hard enemy spawns 2 bullets. Set bullet_start to Time.time and can_spawn_bullet to false. Outside of the if create another if and if Time.time -1 is bigger than bullet_start, set can_spawn_bullet to true so it can spawn bullets everry 1 second.

Now go on an create a new void named OnCollisionEnter2D and put "Collision2D col" as the parameter. Inside it create a switch statement and make its condition col.gameObject.tag. The first case is "bullet" tag so inside the "bullet" case decrement the health by one and if the health is equal to zero, decrement Game.enemies_on_screen, decrement Game.max_enemies and increment Game.kill_count. Also Destroy(gameObject). Put a break at the end of the case and create a new case with the condition "player". Inside it call Game.TakeDamage() function.

Get back to the Game.cs script. Add two GameObjects named enemy1 and enemy2 (if you have a hard enemy.) Add three RawImages called h1,h2 and h3, for 3 hearts in the game UI. Create a new boolean name difficultMode and set it to false. Create public static ints called enemies_on_screen and max_enemies. Create an int named loop. Create a public static int called kill_count to take track of the kills. Create a Vector3 named enemy_spawn and create a Quaternion called rotation and set it to new Quaternion(0,0,0,0). Create a floats called tame_damage_start set it to 0 and can_take_damage, set it to true. We do this so the character will have a timeframe where he is immune after taking damage. In the Start() void, set kill_count to 0, enemies_on_screen to 0, max_enemies to 0, loop to 0 and difficultMode to false.

Get to the Update() void. Increament the loop by one. If loop % 50 is equal to zero and max enemies <= 5, increment max_enemies by one. If Time.time >= 20, set difficultMode to true. If enemies_on_screen <= max_enemies, set enemy_spawn to new Vector3(6, Random.Range(-4,4)) so the enemy will spawn at a random location. Create an if and make the condition difficultMode. Inside it create a new int called random and set it to Random.Range(0,2). If random is equal to 0, instantiate enemy1, else, instantiate enemy2. Get out of the if(enemies_on_screen <= max_enemies) block. If Time.time - take_damage_start >= 5, set can_take_damage to true and set the color variable in player objects SpriteRenderer to Color.white. If !can_take_damage, set it to Color.grey instead. Call UpdateLives() function at the very end of the Update() void.

Create a new void and call it UpdateLives(). Inside it create a switch statement with the parameter lives. In case -1, write SceneManager.LoadScene("Scenes/Lose") and break out the the case. In case 0, set the texture variable in the RawImage component of h1 to the empty heart GameObject and break out of the case. For case 1 and case 2 do the same for h2 and h3.

Create a public static void called TakeDamage(). In it create an if statement with the parameter can_take_damage. In the if statement, set take_damage_start to Time.time, decrement the lives and set can_take_damage to false. Go to the Inspector and fill in the required GameObjects.

You have finished the game!

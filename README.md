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

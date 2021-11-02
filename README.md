# ObjectsPickUp

In this tutorial we will be able to pick up items around our game. We will need to follow the next steps:

## 1. Open the previous Unity Project

Open the last project and create a new Scene called PickUp. To this Scene, add a ``3D Object > Plane``,  ``3D Object > Capsule`` (called Player) and a ``3D Object > Cylinder``, which we will shape to look like a coin, add as many as you want to the scene.
You can create materials for each one of them and add colors as you like.

To the Hierarchy, go to ``UI > Text`` and write "Coins:". Make this text larger and drag it to the top-left corner of the canvas until you are happy with it.

Create a new tag called ``coin``, add it to every coin object and tick ``Is trigger`` every coin collider.

![22](https://user-images.githubusercontent.com/91539042/139861713-d30e84f5-440d-4158-ac55-024161aa120a.PNG)

## 2. Script ScoringSystem

Create a new script called ``ScoringSystem``. We will be using UI components for the text, so we will need to add ``UnityEngine.UI;`` at the top of the script. We will add a ``public GameObject coinText;`` which refers to the text ``Coins:`` in the game. And a ``public static int theScore``, which will allow the text change every time we get a coin.

On ``Update``, we will need to add ``coinText.GetComponent<Text>().text = "Coins:" + theScore;`` which means that when playing the game, the text will change to "Coins:". It should look like this:

![11](https://user-images.githubusercontent.com/91539042/139861548-12fd7cdc-3945-493e-a86c-bbc45709538f.PNG)

Go back to the game, in the Hierarchy add an ``Empty`` object and attach this script to it. In ``Coin Text``, from the script, drag the ``Text`` from the ``Canvas``.

![Capture](https://user-images.githubusercontent.com/91539042/139861573-eb5aac8f-95b1-4ed4-8b90-0c7681a93a78.PNG)

## 3. Script PickUp

Create a new script and call it ``PickUp``. Delete ``Start`` and ``Update``. We will need to indicate that when the object collides with another collider, the score system will add one point and this object will be destroyed, to do this, create a new void called ``private void OnTriggerEnter(Collider other)`` and inside of it, write: ``ScoringSystem.theScore += 1;`` and ``Destroy(gameObject);``. It should look like this:

![3](https://user-images.githubusercontent.com/91539042/139862664-4cd83be6-7c75-4ccd-993b-008179c83c0e.PNG)

This should work, making your player be able to collect coins and adding them to your score. 


src -

Player

```cs
...
public class Player : MonoBehaviour{
  [SerializeField]
  private float moveForce = 10f;
  
  private flaot movementX;
  
  private Rigidbody2D myBody;
  private SpriteRendered sr;
  
  private Animator anim;
  private string WALK_ANIMATION = "Walk";

}
```

`Awake` method runs before `Start` method. Used to assign components
```cs
  private avoid Awake() {
    myBody = GetComponent<Rigidbody2D>();
  }
```

auto generated functions
```cs
    // Start is called before the first frame update
    void Start()
    {

    }

    // Update is called once per frame
    void Update()
    {
    
    }
```

# move player 
```cs 
  void Update()
    {
      PlayerMoveKeyboard();
    }

  void PlayerMoveKeyboard() {
    movementX = Input.GetAxisRaw("Horizontal");
    transform.position += new Vector3(movementX, 0f, 0f) * Time.deltaTime * moveForce;
  }
```

# Collision Handle
maintain Groud. select one ground in `groud holder` and goto `Tag` and click `Add Tag`. Then under `Tags` click on the `+`. Create a `New Tag Name` as `Ground` and save. Then select all ground objects in `groud holder`  goto `Tag` and select `Ground` tag. 

updates need to be done on the `Player` script.
```cs
  ...
  private boolean isGroundded;
  private string GROUND_TAG = "Ground";
  ...
  // new method 
  private void OnCollisionEnter2D(Collision2D collision) {
    // collision obj is the 2nd obj which this obj collid with
    if (collision.gameObject.CompareTag(GROUND_TAG) {
      isGrounded = true;
      Debug.Log("Landed on the ground");
    }
  }
```

# Create Main Menu
need to create a new scene. under `File` click `New Scene` then click `Basic 2D`. Save it as `MainMenu`. In hierarchy, right click go to `UI`. every UI element must be child of `canvas`. 
`EventSystem` is there to detect clicking things. 

click `canvas`, tick `canvas` in inspector. `screen space overlay` means it overlays the screen. 

tick `canvas scalar`. change `UI scale mode` to `Scale with screen size`. Change `reference resolution` as needed. in video it is set to 1920x1080. `Match` put to `0.5`. This will change this sizes accordingly for different resolutions. 

`Render mode`, `World Space` is not mainly used in 2D games. 

Select `image` in hierarchy. In appearing window it will indicate it as a `Rect Transform`. Using the left side box (anchor), you set where it need to be anchored.

how to change image?
- select image in hierarchy. go to inspector. go to image tab. drag and drop the image to `source image`.you can resize it as well. 

you can add UI text as well. You can use that to display game name.
You can add button as well. 

then create a script `MainMenuController`. inside `MainMenu` in hierarchy, create an empty object `Main Menu Controller`

click button in hierarchy. go to `OnClick` tab click `+`. then for drop down `Runtime Only` drag and drop the `Main Menu Controller`. then go to `No Function` dropdown. then select the function `PlayGame`. then on clikc that function will be executed. 

inside the script. 
```
public class MainMenuController : MonoBehaviour {
  public void PlayGame() {
    Debug.Log("button pressed");
  }
} 
```

if there are more buttons and one function is attached to all, how to know which button is pressed? 
- name the game objects in a pattern.

change  `Main Menu Controller` script to move scene.
```
...
using UnityEngine.SceneManagement;

public class MainMenuController : MonoBehaviour {
  public void PlayGame() {
    SceneManager.LoadScene("Gameplay");
  }
} 
```
when you click, if it pops an error saying game scene can't be loaded. then goto File>Build Setting> tick the scene. Now it should work. Any scene should be available in the Build. 

how to know which player is selected?
- create a new script `GameManager`


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

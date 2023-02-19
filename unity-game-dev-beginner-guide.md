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

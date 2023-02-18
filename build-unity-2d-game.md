src - https://www.youtube.com/watch?v=4BD3y0NYNqk

create a unity project

create 2d icons with paint and drag and drop to scene tab. 

select player, goto inspector and add component. physics 2D > rigidbody2d

drag camera to player.

play and see.

select player, goto inspector and add another component. physics 2D > box collider 2D

after doing that do copying.

goto assets folder and create a folder `Script`. Inside click to create C# script `PlayerControl`.

update script
```
public class PlayerControl : MonoBehaviour {
  public Rigidbody2D rb;
  
  void Start() {
    rb = GetComponent<Eigidbody2D>();
  }
  
  void Update() {
    rb.velocity = new Vector(1, rb.velcoity.y);
  }
}
```
select player. add component > scripts > PlayerControl.

play and see. 

update script.
```
  ...
  void Update() {
    rb.velocity = new Vector2(1, rb.velcoity.y);
    
    if (Input.GetMouseButtonDown(0)) {
      rb.velocity = new Vector2(rb.velocity.x, 3);
    }
  }
```
play and see. 

mouse click is equivalent to touching in any place.

update script
```
public class PlayerControl : MonoBehaviour {
  public Rigidbody2D rb;
  public Transform groundCheck;
  public float groundCheckRadius;
  public LayerMask whatIsGround;
  private boolean onGround;
  
  ...
  void Update() {
    rb.velocity = new Vector2(1, rb.velcoity.y);
    onGround = Physics2D.overlapCircle(groundCheck.position, groundCheckRadius, whatIsGround);
    
    if (Input.GetMouseButtonDown(0) && onGround) {
      rb.velocity = new Vector2(rb.velocity.x, 3);
    }
  }
  
```

create invisible game object `check ground`.
in player, for `ground check` drag and drop `check groudn`.

click a platform. click `add layer` add a layer `ground`. then select it as the layer. 

select player and select `what is ground` to `ground` layer. 

play and see. 

Last Step: Simple scripts that you need to create
-------------------------------------------------

You are required to write skill trigger script to trigger your active
skill nodes.

For Example, below is the skill trigger used in the Samples.

.. code:: c#

       private SkillEquipManager mgr;
       private AttributeTable table;
       private Animator anim;
       private Rigidbody rb;

       private Vector3 endPos;
       // Use this for initialization
       void Start () {
           mgr = GetComponent<TheSkill> ().equip;
           table = GetComponent<TheSkill> ().table;
           anim = GetComponent<Animator> ();
           rb = GetComponent<Rigidbody> ();
       }
       
       // Update is called once per frame
       void FixedUpdate () {
           if (mgr != null) {
               if (Input.GetMouseButtonDown (1)) {
                   mgr.PlaySkill ("Move", null);
               }
               if (Input.GetKeyDown(KeyCode.Q)){
                   SetMousePos ();
                   Hashtable skillData = new Hashtable ();
                   skillData ["endPos"] = endPos;
                   mgr.PlaySkill ("JumpAttack", skillData);
               }
               if (Input.GetKeyDown(KeyCode.W)){
                   SetMousePos ();
                   Hashtable skillData = new Hashtable ();
                   skillData ["endPos"] = endPos;
                   mgr.PlaySkill ("Roar", skillData);
               }

               if (Input.GetKeyDown (KeyCode.H)) {
                   Hashtable skillData = new Hashtable ();
                   skillData ["value"] = 300;
                   mgr.PlaySkill ("Hurt", skillData);
               }
           }
           if ((rb.velocity.magnitude > 0)) {
               anim.SetFloat ("Movement", table.movement);
           } else {
               anim.SetFloat ("Movement",0);
           }

       }
       private void SetMousePos () {
           RaycastHit rayHit;
           Ray ray = Camera.main.ScreenPointToRay (Input.mousePosition);
           if (Physics.Raycast (ray, out rayHit)) {
               endPos = rayHit.point;
           }
       }
   }
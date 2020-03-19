Description: AttributeTable
==============================

AttributeTable just works as its name, it’s a table of numerical
properties that your skills may concern.

It’s totally open to be self-defined.

For example, you can define as follows:

.. code:: c#

   using System.Collections;
   using System.Collections.Generic;
   using UnityEngine;
   public class AttributeTable:ScriptableObject {
       [ReadOnly]public string TAG;
       public string Owner;
       public TheSkill system;

       private GameObject target;
       public void init(TheSkill system){
           this.TAG = system.TAG;target = system.gameObject;
       }
       //Above should not be modifield.
       
       //Below are examples of customization
       public int health;
       public int mana;
       public int movement;
       public float manaRegenSpeed;
       public float healthRegenSpeed;
       public float attackSpeed;
       ...
   }

Notice that there are two properties reserved as **TAG** and **Owner**,
it’s tag to distinguish this object from other tables.

E.g.

====== ===== ======
Table  TAG   Owner
====== ===== ======
table0 Human Mark
table1 Human Julier
table2 Demon Satan
====== ===== ======

**TAG** totally has no conflict with unity’s tag system, it’s just a
string field to classify these objects.While **Owner** has no more usage
than giving a note for users to know the exact attribution of one
``AtrributeTable`` object,you can even set it as empty.

In this way you can clearly know the attribution of one
``AttributeTable`` object. Notice that changing *TAG* is not expected
after the object’s generation, though it’s public (just for the
convenience of tag checking).

Also there’s is a reference for ``TheSkill`` and you **should not**
modify that.(it will be auto assigned).

The ``GameObject`` **target** is for the reference of the gameobject
which haves the system(based on the considerations that you may make use
of some components of the gamobject such as ``RigidBody`` and
``Collider``).

Also, you **should not** modify it as it will be auto assigned by other
scripts.

Your self-defined skillnode can get the object reference only in this
way:

.. code:: c#

    node.attributes.target

In one word, you can add any properites (and functions) into the script
``AttributeTable.cs`` and they will appear in the inspector as expected.
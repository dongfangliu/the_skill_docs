Expected acts and Notes
================================

Expected
~~~~~~~~

-  Leave nodes under the folder
   ``Assets\The Skill\TAG\Nodes\instances\`` completely blank.
-  Modify nodes under the skill node library and take skill trees for
   testing.
-  That is, use different instances of skill library as a version
   history of skill nodes.
-  Make full use of *TAG+NickName+Icon* to distinguish nodes with
   similar names.
-  Make use of ``BodyEffects`` to takes FXeffects on the characters.
-  Use Prefabs of ``particleSystem`` as ``EmitObjPrefabs``.
-  If you have only an lifetime requirement for ``EmitObjTemps``, set
   ``emitTime`` in the function ``EmitObjTempsWithItween()``.
-  Set ``endPos`` for ``EmitObjTemps`` ’s component ``EmitObj``\ in the
   function ``EmitObjTempsWithItween()`` attached on them if it’s a
   ``PositionBoot`` Skill.
-  If it’s a ``CollionBoot`` Skill , set ``EmitObjTemps`` ’s component
   ``Collider`` ,\ ``ISTrigger = true`` for a better performance.
-  Add ``Collider`` and ``EmitObj.cs`` for each GameObject in
   ``EmitObjPrefabs``.

Notes
~~~~~

-  for ``singTime,PlayTime,InterruptTime,ExitTime`` , if any is greater
   than 0 , please use branches (if else sentences) in corresponding
   functions (e.g.\ ``OnSkillPlaying()``) to avoid repeated (redudant)
   operations for same object.

If not ,there may lead to a great decent on the framerate.

-  The normal way to debug why does a skill not react to the call:

1. Is it a passive node?
2. Has it cooled down?
3. Is the skill activated?
4. Does it statisfy its ``triggerCondition()``?
5. ``EmitObjTemps`` are not triggerd in last call? not setting the
   ``emitTime`` or ``endPos`` in the ``EmitObj`` script attached on the
   ``EmitObjTemps``?

-  If use ``PositionBoot``, set the Collider on the ``EmitObjTemps`` as
   Trigger(``isTrigger = true``). Or else, it may never arrives the
   ``endPos`` you setted due to unexpected collision.

-  Please set your character and the enemies you want to affect in
   different layers. Or else, the Input of
   ``OnSkillPlaying(List<GameObject> objs)`` may contains the character
   itself.

-  Under most situations, set ``RenderTriggers = Collide``.

-  You can use Skill Icon as a part of your UI interface.

-  Use the code ``SkillEquipManager.getProperty<Texture2D>("Icon")``.

-  Further use this system as part of your AI logic.u have only an
   lifetime requirement for ``EmitObjTemps``, set ``emitTime`` in the
   function ``EmitObjTempsWithItween()``.

-  Set ``endPos`` for ``EmitObjTemps`` ’s component ``EmitObj``\ in the
   function ``EmitObjTempsWithItween()`` attached on them if it’s a
   ``PositionBoot`` Skill.

-  If it’s a ``CollionBoot`` Skill , set ``EmitObjTemps`` ’s component
   ``Collider`` ,\ ``ISTrigger = true`` for a better performance.

-  Add ``Collider`` and ``EmitObj.cs`` for each GameObject in
   ``EmitObjPrefabs``
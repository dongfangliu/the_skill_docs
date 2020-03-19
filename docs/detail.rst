Detailed description
========================

The Skill is a node-based visual skill development framework that provides Unity game developers complete and automated character skills process management, CoolDown control, skill statusquerying (Playing, NonExist, NonActived, Free) and acquisition and setting ofskill-dependent variables.

In The Skill, you can customize the composition of the character attribute table you need. Another advantage of TheSkill is that it enables the association and mutual referencing of character attributes and character skills.

In addition to that, The Skill offers agreat deal of freedom in key-value pairs over skill code calls (*i.e. playSkill (string skillName, HashtableskillData*), skillData can be referenced and retrieved directly in code with the same name as the skill.

In The Skill each skill is a node, passive skills will be automatically managed and triggered, and active skills requirethe developer to write additional trigger script for skills call. In addition,each skill is divided into both directional and non-directional skills.

Each skill, inherited from the parent class SkillNode, and SkillNode inherited from Scriptableobject, so it is an entitydata, but also can have its own member variables and member functions.

This setting allows the skill node to dothe integration of data and code. In this plugin, some member variables of the base class SkillNode will appear in the Inspector, you need to set them to make the skills perform as expected. The extra variables you need should be declared in the code with the same name as the skill, which will also appear under the ChildProperties in the Inspector.

You will also need to rewrite 6 functions in order to achieve the skills effect you want.

Therefore, skill nodes have a very high degree of freedom, and those small limitations (such as setting some base variables) maintain the normal operation of the node.

More interestingly, since each node is data, you can delete, copy, or move just like any Prefab does. The advantage isthat, combined with our ``SkillNodeLib`` (that is, the template library), you can freely combine these nodes in accordance with your needs into the collection you want, such as human skills template library, or divided according to occupation, magician Skill template library 1, magician skills template library2, warrior skills template library 1 ......

All these operations are visual. 

**The only code you need to cover throughout the system is the node code which has the same name with the skill and the skill invocation script**.

Of course, for each specific character, their skill tree may come from the same template, but the specific skill progress may not be the same. So in The Skill, the last thing important is ``SkillLearningTree (skill tree)``.To generate a skill tree from the ``SkillNodeLib(skill lib)``,all you have to do is to click a button.

However, such a skill tree does not have any parent-child relationship between nodes, and each node is independent. By right-clicking on the node, you can easily establish the relationship between the nodes.

This parent-child relationship has only one effect. When a childnode is not activated, the parent node will also be forcibly deactivated and will not respond to code calls.

In practice, a character can only invoke the skill normally if it has both a ``attribute table`` and a ``skill tree``.
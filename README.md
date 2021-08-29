# ThrowJoint

A throw joint for avatars 3.0 that uses rigidbody physics instead of particle physics, and is free so.

# How it works

Basically, It's just the [World Physics](https://github.com/VRLabs/VRChat-Avatars-3.0#world-physics) prefab from VRLabs, that I slapped a spring joint with a parent constraint onto.<br>

Swap the joint between hands by pointing on the respective hand, and throw it point not pointing on both hands.

That's essentially it. 

If you want to go into the nitty gritty, I set up a rigidbody with a parent constraint, that constrains it to the `ThrowJointRightTarget` and `ThrowJointLeftTarget`.<br>
Then, on the container, there's another rigidbody, and a spring joint. The spring joint is connected to the rigidbody that is constrained to the left and right targets.<br>
This creates the ability to swap the ball between hands. To add the ability to drop the ball, you not so simply disconnect the spring joint. To do so, you have to set the min distance super high. There is no way to just disable the spring joint.<br>
And that is essentially it. Everything else on the throw off and on animations are just to improve the physics.

# Installation

1. Throw the prefab into your avatar at the root.
2. Unpack it.
3. Put the `ThrowJointRightTarget` and `ThrowJointLeftTarget` on the right and left hand bones of your avatar respectively.
4. Merge the included FX and Gesture layers and 3.0 params to your existing ones using [this](https://github.com/VRLabs/VRChat-Avatars-3.0#avatars-30-manager) tool.
5. Put whatever you want to be as the thing on the joint as children in the `Container` GameObject. 
6. Add a toggle for the `OrbToggle` parameter to one of your 3.0 menus.
7. Make sure to run the [Fix Order](https://github.com/VRLabs/VRChat-Avatars-3.0#fix-order) script before you upload each time.
8. Smack upload!

A couple things to note here:
1. If you want to change the physics of the rigidbodys or spring joint, change the physics of the rigidbody and spring joint on the `Container` GameObject. Do not touch anything other joints or rigidbodys. Also, make sure that if the property you changed is controlled by the `OrbThrowOff` or `OrbThrowOn` animations, that you change the values in the animation as well.
2. If you want to change the type of collider, or what GameObject it's located on, make sure to change the `FixColliders` animation on the `World Physics` animator. 
3. The collider CANNOT be on by default.
4. DO NOT change the name of any of the GameObjects in the prefab. Only the `Container` GameObject should have any GameObjects added as children.
5. The collider on the joint will act as a collider for your avatar. I have no idea why it does this, and no idea how to fix it.
6. The collision on the rigidbody is discrete, so it may phase through things. It doesn't usually pose an issue but on thing surfaces it does. You can change the collision type, but it will cause lag. The Unity manual isn't lying when it says the other collision types have a performance hit. Even if there is just one.
   
Essentially, you must follow the constraints detailed in [this](https://github.com/VRLabs/VRChat-Avatars-3.0#world-physics) prefab.

# Demonstration
[Video of Throw Joint](https://i.imgur.com/g0QgUpt.mp4)<br>
*The avatar in the video is a highly modified [Sephira](https://mk22.booth.pm/items/2953001) also the ball in the video is not included

# Contact

Please direct any questions you may have to the issues page on this Github, or if you cant make an issue for some reason, my Discord, `loukylor#0001`.<br>
You will have to DM me through the VRChat Discord. If you are banned from it, then too bad.<br>

# Credits

Huge credits to the people who work on the [avatar 3.0 prefbs](https://github.com/VRLabs/VRChat-Avatars-3.0) as without those prefabs this would not have been possible.<br>
Huge thanks as well to [lindesu](https://github.com/oofdesu), who helped me with various issues I had while making this.
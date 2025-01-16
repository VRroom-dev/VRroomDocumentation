Avatars will use Playables system but props and worlds will not.
The AnimatorControllerPlayable allows us to use the existing animation controller with little work.

The Playables system is much more powerful and can support more than what animation controllers can, but making a different system from animator controllers is bad right now as everything is built on them.

It should be built to coexist along side some future system to replace it though.
This future system would likely be built for use in worlds and props first before being a secondary method, then primary method for avatar animations, but it would always coexist.
AvatarController Scriptable Object is where your avatars controllers, menu entries, and parameters are configured

The AvatarController contains:
- Animation controller dependencies
- Parameter list
- Menu entries

The animation controller dependencies is a list of controllers that menu needs to work and what controller type they are (user, locomotion, ik pose, tpose). this is optional though as long a dependent controller is listed in atleast one menu on the avatar. some controller types will be merged (user and locomotion type controllers) and others not (ik pose, tpose). the ones that arnt merged are only used in specific scenarios. you will also configure controller priority here.

The Parameter list allow you to configure if a parameter is synced or not in this menu or override its configuration from a submenu. you should also be able to apply a override to all submenus aswell. you do not define a parameter here, you only configure it. this will also show what entry types it is and the entries its used in.

The menu entries is where you define a entries type, name, parameter, and default value. if the type is submenu you can embed another AvatarController.

The animation controller dependencies and parameter list is shown followed by the list of nested menu entries. nested menus do not show the animation controllers and parameter list as the top most one shows them and what submenu they come from.


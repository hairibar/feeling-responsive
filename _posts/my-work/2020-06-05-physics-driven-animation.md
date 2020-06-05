---
layout: page
header: no

title:  "Hairibar.Ragdoll: Physics-Driven Animation"
teaser: "A Unity package that drives ragdolls and makes them play keyframed animations while keeping physics behaviour."

image:
    thumb: Tongued\Tongued_Thumbnail_1280x720.png
    title: Tongued\Tongued_Thumbnail_1280x720.png

breadcrumb: false
show_meta: false

category: my-work
tags:
    - featured

look-at-code-button:
    text: Look at the code
    url: https://github.com/hairibar/Hairibar.Ragdoll
---

## It's versatile.
- Free your animators from the tedious labour of hand-animating secondary motion.
- Use it with tight settings to get realistic characters that react to collisions.
- Use it with loose settings to get silly, physicsy motion.

## It's transparent.
The system lets the existing animation tech do its work, reads the resulting pose and then drives the ragdoll towards that pose. This means that it is inherently compatible with any system that modifies animation, such as IK. 

## It's easy to use.
Most configuration is done through artist-friendly ScriptableObjects. Their editors have been heavily customized to make them easy and safe to use.
Most parameters are sliders that go from 0 to 1, with clearly explained effects.

## It's generic
Unlike with many of Unity's animation features, all rig types are supported, not just humanoids. The available bones are listed in a RagdollDefinition asset. After that, per-individual-bone parameters can be set in other assets, such as RagdollAnimationProfile and RagdollWeightDistribution.

## It's expandable.
Writing scripts that modify the ragdoll's behaviour is supported. You can implement IBoneProfileModifier to dynamically affect the way the ragdoll matches the animation, or you can implement ITargetPoseModifier to post-process the pose that the regular animation system has provided before the ragdoll follows it. Many of the built-in features have been implemented through these interfaces!

You can also make your own data types that work with specific RagdollDefinitions, in case your modifiers need to be easily-configurable. Just inherit RagdollProfile!

## It's integrated with Mecanim.
Hairibar.Ragdoll comes with StateMachineBehaviours like SetRagdollAnimationProfileOnEnter and SetRagdollPowerProfileOnEnter. These behaviours allow you to easily tie specific sets of parameters to specific animation states.

## How do I get it?
It's publicly hosted in GitHub, and distributed via Unity's Package Manager. You can add it to your projects by adding the following lines to your manifest.json:
```
{
  "dependencies": {
    ...
    "com.hairibar.naughtyattributes": "https://github.com/hairibar/NaughtyAttributes.git#v2.2.1",
    "com.hairibar.engineextensions": "https://github.com/hairibar/Hairibar.EngineExtensions.git#v1.1.0",
    "com.hairibar.ragdoll": "https://github.com/hairibar/Hairibar.Ragdoll.git#upm"
    ...
  }
}
```
More detailed instructions (and possibly more up to date ones, too) can be found at the [repository itself](https://github.com/hairibar/Hairibar.Ragdoll).

## How does it work?
I'm currently writing the thesis, which will, once finished, explain the inner workings in detail. Sorry for keeping you waiting. 
For now, you can go through the code if you like!

{% include GuideButton.html button=page.look-at-code-button %}

---
layout: page
sidebar: left_fact-sheet

header: no

permalink: /tale-of-jade

title:  "Tale of Jade"
teaser: "A 2.5D metroidvania set in the age of the Three Kingdoms."
image:
    thumb: ToJ\ToJ_Thumbnail_1280x720px.png
    title: ToJ\ToJ_Thumbnail_1280x720px.png

breadcrumb: false
show_meta: false

category: My Work
tags:
    - featured

facts:
    role: Lead Programmer, Sound Designer.
    platforms: Windows
    engine: Unity
    release-date: 05/11/2020
    play-at: 
        url: https://ke-studio.itch.io/tale-of-jade
        text: Play it
    

screenshots: 
    - ToJ\ToJ_Screenshot_Dungeons_01.jpg
    - ToJ\ToJ_Screenshot_Ability.png
    - ToJ\ToJ_Screenshot_Boss.jpg
    - ToJ\ToJ_Screenshot_Map.jpg
    - ToJ\ToJ_Screenshot_Dungeons_02.jpg
    - ToJ\ToJ_Screenshot_Dialogue.jpg

final-play-button:
    text: Play it
    url: https://ke-studio.itch.io/tale-of-jade
---

Tale of Jade was bigger than any other project I'd worked on previously. It was also what kept me busy during the pandemic most of the way through 2020.

## What did I do in it?
- [I developed a custom 2D physics system.](#custom-2d-physics)
- [I developed a pipeline for exporting Blender renders and importing them as animations in Unity.](#blender-spritesheet-pipeline)
- [I built procedural spline-based mesh tools on top of SpriteShape.](#procedural-spline-based-mesh-tools)
- I designed and the developed the listened sequence UI.
- I designed and implemented all audio through FMOD.
- I developed an easy to use wrapper for poolable FX.
- I wrote almost all of the gameplay code. 
- I wrote documentation so that the art team could use my tools and the designer could build the gameplay out of reusable components.

## Custom 2D physics
While the game was prototyped with Box2D, it soon became obvious that we had to fight against its realism with every mechanic. I decided to take a step back and write my own physics system, named KE.Physics, achieving total control and making things much easier in the long run.

In KE.Physics, a KEBody casts a set of rays horizontally and vertically every step. These rays determine how far the body will move in each axis. This approach means that, unlike in Box2D, where interpenetrations are allowed and then corrected through forces, KEBodies at no point penetrate other colliders. This is extremely important for the high accelerations that appear in the game.

![]({{site.urlimg}}/ToJ/ToJ_KEPhysics_Inspector.png)

A core feature of KE.Physics is its support for sloped surfaces. KEBodies have a simulationVelocity member, which, while the body is grounded, behaves relative to the ground. With a simulationVelocity of (1, 0), the body will go right, which may include going up a slope if it's shallow enough. 

Abstracting slopes in this way made implementing common platformer mechanics (such as pushing an object) much easier, as it removes the need to take slopes into account.

KE.Physics also allows a handy API for querying collision on each side of the character's collision box. For example, the `IsGrounded` property simply uses `keBody.GetCollisionData(CardinalDirection.Down)`.

## Blender spritesheet pipeline
We went for a mixed 2D and 3D art-style. After some time, we found that 2D rigs significantly limited the animation quality. 

We decided to use 3D models for the characters, and then render the animations as spritesheets so that they would look like 2D sprites in the game. This process required an automated pipeline.

The pipeline consists of two pieces. 
1. A Blender plugin that exports the animation as a spritesheet.
2. A custom asset importer for Unity that imports the exporter's result as an animation clip.

For the exporter, I used [an existing plugin](https://github.com/theloneplant/blender-spritesheets) as a foundation. I heavily expanded upon it, adding a lot of configuration, a normal map pass, the ability to export marker positions...

![]({{site.urlimg}}/ToJ/ToJ_KESpritesheet_Exporter.png)

The importer was built from the ground up, and behaves just like Unity's built-in importers, including a preview. The generated animation clip behaves just like any other imported animation too.

![]({{site.urlimg}}/ToJ/ToJ_KESpritesheet_Importer.png)

The final pipeline looks like this:
1. **Animation authoring**
    1. The animator animates the character in Blender.
    2. The animator adds marker objects to track points of interest, such as the feet.
2. **Export as spritesheet**
    1. The animator configures the render window.
    2. All frames are rendered twice, once with the assigned materials, and once with a material that renders world-space normals. We found that when our 2D artist hand-drew normal maps, they would be exaggerated in the horizontal axis. To mimic this, the shader slightly rotates normals towards the outside in the X axis.
    3. The frames are consolidated into two spritesheets (albedo and normals).
    4. A JSON file containing metadata (such as marker positions) is generated.
    5. The three files are zipped into a .kespritesheet file.
3. **Animation import**
    1. The .kespritesheet is imported into the Unity project.
    2. A custom importer unzips the file.
    3. The textures are loaded and sliced as spritesheets, following the sizes defined in the metadata.
    4. An animation clip is created with the frames keyframes with the correct timing.
    5. Marker positions are added as child object animations.



## Procedural spline-based mesh tools
I built two similar tools on top of SpriteShape. Both use SpriteShape's curve editor and generated mesh, and create an additional mesh with a particular shape.

The first tool was used for the darkness that surrounds most levels. SpriteShape's mesh is completely dark. To achieve a gradient from black to transparent, the tool generates an extruded mesh. The UVs of this mesh are then used to gradually approach an alpha of 0.

The second tool was used to make grounds and walls. An extrusion of SpriteShape's mesh is made along the Z axis, creating a ground that follows the curve. To avoid perfectly straight grounds, the vertices of this extrusion are offset in the Y direction with some perlin noise.

{% include VideoEmbed.html video="ToJ/ToJ_SplineMeshes.mp4"  type="mp4" autoplay = false %}

Most levels use the second tool as a foundation, which enabled the designer to quickly build and edit level geometry. 


## The team
This game was made by [KEStudio](https://twitter.com/KEStudio_es), composed of the following people:
- **Diego "Jusi" Sánchez Ramírez** - 3D Artist
- **Pablo Martínez Domingo** - Game Designer, Additional Programming
- **Ignacio José Díaz Polleiro** - Concept Artist, UI Designer
- **Daniel Dávila Pérez** - VFX Artist
- **Jaime Rodríguez Aguado** - Animator
- **Aitor Iribar** - Lead Programmer, Sound Designer

<div class="row t30">
    <ul class="small-block-grid-2" style="padding: 30px">
        <il>{%include GuideButton.html button=page.final-play-button %}</il>
    </ul>
</div>

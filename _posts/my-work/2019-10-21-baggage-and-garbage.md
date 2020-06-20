---
layout: page
sidebar: left_fact-sheet

header: no

permalink: /baggage-and-garbage

title:  "Baggage & Garbage"
teaser: "A casual, mobile oriented puzzle game about sorting baggage at airport security by building conveyor belts."
image:
    thumb: B&G/B&G_Thumbnail_492x277.png
    title: B&G/B&G_Logo_1416x542.png

breadcrumb: false
show_meta: false

category: My Work

facts:
    role: Programmer, Designer, Sound Designer, Musician
    platforms: Web
    engine: Phaser
    release-date: 21/10/2019
    play-at: 
        url: https://fresisuis-hunters.itch.io/baggage-garbage
        text: Play it
    

screenshots: 
    - B&G\B&G_Gameplay_01.png
    - B&G\B&G_LevelSelect.png
    - B&G\B&G_Gameplay_02.png
    - B&G\B&G_EndScreen.png
    - B&G\B&G_Gameplay_03.png

final-play-button:
    text: Play it
    url: https://fresisuis-hunters.itch.io/baggage-garbage

look-at-code-button:
    text: Look at the code
    url: https://github.com/FresisuisHunters/BaggageAndGarbage
---

Baggage & Garbage is a multiplatform HTML5 game made with Phaser. It can be played in wither desktop or mobile.

## What did I do in it?
### Player interaction with conveyor belts
I designed and programmed the way the player builds conveyor belts. This includes a snap distance that interprets the player's input and finds a nearby lane.

{% include VideoEmbed.html type="mp4" video="B&G/B&G_Snap.mp4" autoplay=true %}

### Conveyor belt rendering
The conveyor belts are made out of modular pieces. There are multiple variations for the sides, which are randomly chosen from. To get the conveyor belts to look good with any length, the sprites are dynamically resized to cover the belt's distance with a whole number of pieces.

![]({{site.urlimg}}/B&G/B&G_ConveyorSprites.png)

There was an additional problem to solve: intersections between conveyor belts. My solution was to use a mask that hides anything that overlaps the main lane's belt. 

![]({{site.urlimg}}/B&G/B&G_ConveyorIntersections.png)

### Production scalability
The game's art requirements presented a production challenge.
- Many different bag types where needed.
- There are scanners in the game that show the interior of a bag.
- Multiple variations of these interiors where needed.

Pablo (the other designer in the team) and I designed a system to maximize reuse and deal with this problem of scale:

- An individual bag sprite could be of one of three types: A (always safe), B (may or may not be safe) and C (never safe).
- Each bag shape was assigned an ID number. 
- Multiple interior sprites where made for each ID that had at least one B sprite. These were made by overlaying premade luggage items (trousers, bombs, shades...) over a shared silhouette of the bag shape.
- When an A or C bag enters a scanner, a generic icon is shown instead of showing an interior.

All of this information was encoded in the filenames themselves. That way, artists could make any amount of variations of the different types, and the game would correctly load and classify all of these sprites without any programmer intervention.

### Level design tooling
I made a system where the levels were defined as a JSON file. Everything could be tweaked in these files, including the bag speed, amount of lanes, scanner positions, bag type distribution...
This proved to be an extremely valuable decision, and made the level design process much easier, as it allowed us to iterate extremely quickly.

{% include alert text="Here's the game's first level as an example:" %}
{% highlight json %}
{
    "difficulty":2,
    "levelIndex":3,
    "bagSpeed": 90,
    "lanes": {
        "count": 5,
        "types": ["S", "D", "S", "D", "S"]
    },
    "waves": [
        {
            "numA": 1,
            "numB_Safe": 2,
            "numB_Danger": 2,
            "numC": 1
        },
        {
            "numA": 2,
            "numB_Safe": 2,
            "numB_Danger": 4,
            "numC": 1
        },
        {
            "numA": 2,
            "numB_Safe": 4,
            "numB_Danger": 4,
            "numC": 2
        }
    ],
    "scanners": [
        {
            "lane":0,
            "y":300
        },
        {
            "lane":4,
            "y":600
        }
    ],
    "starThresholds": [6, 4, 0]
}
{% endhighlight %}



### Music
There's nothing noteworthy about it, I just made the music and am pretty proud of the result.
<iframe width="100%" height="166" scrolling="no" frameborder="no" allow="autoplay" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/843647401&color=%23c6242f&auto_play=false&hide_related=false&show_comments=true&show_user=true&show_reposts=false&show_teaser=true"></iframe><div style="font-size: 10px; color: #cccccc;line-break: anywhere;word-break: normal;overflow: hidden;white-space: nowrap;text-overflow: ellipsis; font-family: Interstate,Lucida Grande,Lucida Sans Unicode,Lucida Sans,Garuda,Verdana,Tahoma,sans-serif;font-weight: 100;"><a href="https://soundcloud.com/hairibar" title="Aitor Iribar" target="_blank" style="color: #cccccc; text-decoration: none;">Aitor Iribar</a> · <a href="https://soundcloud.com/hairibar/baggage-garbage-gameplay" title="Baggage &amp; Garbage - Gameplay" target="_blank" style="color: #cccccc; text-decoration: none;">Baggage &amp; Garbage - Gameplay</a></div>


## The team
This game was made by [Fresisuis Hunters](https://twitter.com/FresisuisHunt), composed of the following people:
- **Pablo Velilla** - Game Designer, 2D Artist
- **Elena Chueca** - Producer, 2D Artist
- **Carmen Gómez** - 2D Artist, UI Designer
- **César Romero** - Programmer
- **Jorge López** - Programmer
- **Aitor Iribar** - Programmer, Game Designer, Sound Designer, Musician

<div class="row t30">
    <ul class="small-block-grid-2" style="padding: 30px">
        <il>{%include GuideButton.html button=page.final-play-button %}</il>
        <il>{%include GuideButton.html button=page.look-at-code-button%}</il>
    </ul>
</div>


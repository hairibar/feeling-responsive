---
layout: page
#
# Content
#
title: "Competition as a motivator"
teaser: "What is the point of competition?"

categories:
  - design

tags:
  - BBBB

image:
  thumb: Blog/tetris-99_plopping.png

header: no
---
We all know that competition can bring the worst out of people. Most of us have had a board game session soured by a friend getting angry, and we’ve all **definitely** been screamed at over voice chat by some teenager. 

Yet it is everywhere in games. Multiplayer games tend to be competitive by default, and even most traditional games are built around some kind of competition. It feels almost inherent to the medium; and I’m not entirely comfortable with that. If it can cause such ugliness, surely we can do better!

And so, I’ve been thinking about why all of this is. Why do we still fall back to competition in our game design? Can we reap its benefits without the toxicity? What even **are** the benefits?

## What's the point?
It once came up in conversation that, for all we know, *Tetris 99* may not actually be a multiplayer game, and we’d never notice. You don’t know anything about your opponents beyond their username and level, and it’s not like you’ve got the time to look at their screen hard enough to spot the difference. For all intents and purposes, they might as well be bots. But, the moment we assume they're bots, the game feels pointless. Might as well play normal Tetris at that point, right?

So there’s something there. My desire to play Tetris 99 comes, to some extent, from the fact that my opponents are humans. It’s not the only reason, of course. I love the mechanics of Tetris, and the moment to moment gameplay of this Battle Royale version doesn’t differ that much from the classic formula. What does change is the **motivator**; the trick that the game plays on my monkey brain to get it to care. 

The classic Tetris formula employs the equally classic technique of numbers going up. The score gets higher, the game gets faster. This feeling of progress is the excuse that my brain needs to engage with the game’s systems. I’m mainly here to plop straight pieces into straight holes and feel good about it, but just doing that feels pointless in the grand scheme of things. “Level 13”, says the game. “Level 14”. Suddenly there’s a point to the plopping: getting to level 15. 

![]({{site.urlimg}}/Blog/tetris-99_plopping.png)

Tetris 99 strips out all the numberwang and replaces it with a single number: 99 (minus one) other players for me to try and beat. I’m still fundamentally playing the same game (and doing the same plopping), but the role of motivator is now taken by competition against other players. That’s why playing against bots would feel pointless: it would remove the motivator, but put nothing in its place. After all, a man needs rhyme and reason to his plopping.

## Competition is a ridiculously effective motivator
With all of my single player designs, I’ve at one point faced the question: *“why does the player care?”* I've got an interesting, fun design (hopefully), but I need to get the player to care enough about it that they'll engage with the interesting stuff - and that you don't get that initial buy-in for free.

The typical solution to this question is content. "If you play and engage with the game, you'll get to see new stuff." This doesn't really work for small games, though.

My multiplayer competitive games, on the other hand, haven’t faced that same issue. Telling the players that whoever gets the most kills wins gives them all the motivation they need. *“Why does the player care?”* barely applies as a question when the answer is *“because they want to win”*.

It really is a fantastic shortcut. Your extrinsic reward related needs are dealt with by the allure of winning, which lets you focus almost entirely on the intrinsic reward, which is what I personally find more interesting. Suddenly, I don’t need to convince you to punch your opponents anymore, I can just make sure that it feels great when you do.

## The downsides
Competition is a double-edged sword. It’s a great shortcut, but it tends to force the game into an extremely specific structure – one that is rigid, repetitive, and that refuses to allow for other motivators.

A game being competitive means, almost by default, that it is match-based. This severely limits what we can do with it as designers. The consequence scope (a term coined and explained here by Tom Francis) must be tiny – an earlier match affecting your current one feels strange at best, and unfair at worst. However, this constraint makes matches inconsequent, which takes us back to feeling pointless. Avoiding that was the whole point!

There are two common solutions to this problem. One is an unlock system, where you might earn a currency for playing that you can then spend on different things. This isn’t a perfect solution, as mechanically significant unlocks (e.g. weapons) ignore the constraint and potentially make matches unfair, while mechanically insignificant unlocks risk not being very interesting.

The other typical solution is a ranked mode. These modes give a sense of progression, but rely on that progression being constant. It trains players to expect progression. When the progression inevitably stops – be it because the player got to the top or because they’ve reached the point where they face stronger opponents – so does the only source of extrinsic rewards. Many players get frustrated at this point, and end up turning toxic when they blame anything but themselves.

Moreover, ranked modes only fit deeply competitive games. Putting them in games that use competition as a motivator, but aren’t really **about** said competition, could result in a horrible experience. Just imagine a ranked mode in *Ultimate Chicken Horse*. A delightful game would become a rage inducing nightmare.

Competition doesn’t have to cause toxicity, it just risks doing so. How? It is, in a way, **too good** of a motivator. Let loose, it can become the whole point of the game and be a source of toxicity. When it’s just the motivator, though, the players enjoy the act of competing. Sure, winning feels better than losing, but the losing player still had an engaging experience.

## I want my cake, and I want to (b)eat it too!
To reap the benefits of competition without the downsides, winning must never overreach into *“The Whole Point of The Game”* territory. Let’s look at two examples, one more successful at this than the other.

The first example is the *Battle Royale* formula. The sheer number of opponents you face has a cool property: statistically speaking, you’re going to lose. This is also true for a 6-player deathmatch, but it rings stronger when you are 1 in 100. Most Fortnite players go into a match with barely any expectation of winning, and I believe that to be extremely important. When the default outcome is defeat, losing doesn’t feel like failure, because you didn’t really expect to win in the first place. 

In games like *Overwatch*, you should, in theory, lose 50% of your matches. However, losing half the games you play does not feel like you’re right where you should be. Your default expectation is success, and so your expectations are let down every other match. *Battle Royale* games manage to flip that expectation on its head, making losses feel like the norm and turning victories into special moments. **They have the feeling of success that comes from winning, without the feeling of failure that comes from losing.**


At the other side of the spectrum, we have the *Mario Party* series, a massive offender when it comes to making losing players angry. Why? We all know that winning doesn’t matter! The problem is, Mario Party constantly tells us that it does. 

![]({{site.urlimg}}/Blog/mario-party_ui.png)
This piece of UI stays on screen for most of the game. A constant reminder of who’s winning, and who’s not. Not only that, but most inter-player interactions in the game revolve around taking stars and coins (which determine the winner) from each other. The minigames handle this better, but the meta game itself is **so** directly about earning points to win that competing becomes the point of the game.

*Battle Royale* games manage to **downplay** the importance of winning, while *Mario Party* can't stop pointing at the score.

## My own take on all of this
I have thought a lot about this for [Bouncing Bass Brawl Bonanza](/bouncing-bass-brawl-bonanza). I wanted to avoid ruining friendships, both because it's the right thing to do, and because the its audience is so small that the only ruined friendships would be mine.
Here’s what I’ve done to that end:

{% include alert text="For context, BBBB is a team fight party game where all the players look identical. Some of the things that work in it may not work for other types of games." %}

The main idea is simple: the players can't see the scores during the match. Players can have an intuition of how well they’re doing, but they don’t receive confirmation until the end. You’re never really sure whether you’re winning or losing, so it doesn’t affect your mind state while you’re playing.

This in turn, almost downplays the competition **too** much, to the point where it risks losing its function as a motivator. To counteract that, the match is surrounded with the pretence that winning matters. Players divide themselves into teams. The teams spawn in different sides of the map. And when the match is over, the scores are finally revealed.

They don't just suddenly appear on screen, though. The game builds up to the end of the match. The timer starts shaking. Two extra timers appear, also shaking. The game pretends, quite obnoxiously, that everything that happens towards the end is more important, that the winner could be decided by any action. Since the scores aren't visible, it can pretend that every match is a close call.

Once the time ends, the players' controls are taken away, time slows down and the camera zooms. It keeps the players waiting just long enough that they build themselves up to the score reveal.

{% include VideoEmbed.html video="BBBB/BBBB_MatchEnd.mp4" type="mp4" autoplay = false %}

At first, this whole setup seems like a throwaway joke, but it's key to the game. It lets me have a 2-minute match where there are no losers, while still getting the excitement and motivation that the promise of winning provides. The game switches between pretending that competition doesn’t matter while in a match and making a big deal out of competition the rest of the time.
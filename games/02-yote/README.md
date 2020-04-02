# Week 2 ~ Yoté + gentrification

[Read the game analysis on Medium ↱](https://medium.com/10-game-hacks-in-10-weeks/week-2-yoté-gentrification-45c07806ea5b) 

### Experiment 1: randomised complexity

> Both players are property developers trying to maximise the value and rental income of their investments ~whilst avoiding the bursting of property bubbles~. Other social actors involved in the gentrification process are non-playing-characters.

Often board games simulate the **complexity** of a system with *chance*: you roll the die or pick an event card and something *unpredictable* happens. To model some of the complexity of *gentrification* processes I will first try and introduce an element of chance. Every time you place or move a piece you roll the die, which determines what happens next (to your [investment](#glossary) or the [area](#glossary) it moved into):

1. If you roll a `1` (I may prototype custom dice later on, but let's keep things simple for now) then a **public housing policy** makes the value of the area decrements (-1?).
2. **Rent cap policy** makes the value of the area not increase (what does this exactly mean? is there a difference between land value and rental income?)
3. **Residents protest**. Roll your move back (either by putting your investment back where it was before rolling the die, or take it out of the board if you were trying to place it).
4. **Residents pack up and move**. No consequences for you. 
5. **Early gentrifiers** move into the area. The investment value increments (+1?).  
6. **Infrastructure boost**. You can move the same investment once more. This can be quite a devastating move as you may be able to *kill* your opponent's investment if you're lucky to roll a 6 and be in the right place.

I playtested this briefly and it does indeed add a bit of complexity (and dare I say, some realism and suspense) to the game. 

#### Big question: what do all the market values going up and down count for? 

Maybe you collect *rent* at every turn, which you can use in some way to influence the game (for example: pay to get a *killed* investment back on the board). This could make the game more realistic, however a potential disadvantage could be that it dilutes the gameplay, breaking it up with `let me count how much rent I need to collect` moments. We need something speedier.

### Experiment 2: property bubbles

How can I simulate the mechanics of property bubbles?

Roll the die twice at the beginning of the game to determine the X and Y coordinates of a *profitable area*. 

Once you determined a *profitable area* there are two options I want to test:

1. This area could start with a higher value (2? 3?) and also influence the value of the surrounding areas (1?).
2. This area could start with a `$` marker on. Your goal is to try and put 4 of your investments around it (top-right-bottom-left, no diagonals). If you do that you win the game!

	Can you use the `$` as an empty area to [kill](#glossary) your opponent's investment? No.

Also, because of the mechanic above (roll die twice to get X and Y) let's make the board **6×6**. I don't really understand why Yoté is 6×5, maybe something to do with strategic positioning in the corners, bah...

#### Big question: does a property bubble ever *burst*? 

Maybe when you / your opponent completely surround an area (or when a 3×2 rectangle is filled) then that area bursts and you have to roll the die 2/3 times to work out the consequences: 2/3 investments go bust.

#### Kill 1 get 1 free?

Should I keep this peculiar mechanic from Yoté? 

It's quite a devastating one, as it can sway the course of a game. 

Also, I struggle to think of an urban gentrification parallel for it. Not that I'm trying to *gentrify* every aspect of the Yoté, but this is feels really jarring. 

Let's try and remove it.

### Experiment 3: property bubbles + randomised complexity

After some playtesting (key lesson: don't kill an idea until you've playtested it), I decided to combine some bits from the experiments above. 

Your goal is still to *kill* all your opponent's pieces (like in Yoté). You still *kill* them by jumping over them and you still move one space up-down-left-right (not diagonally). Now for the differences:

* You play on a **6×6** `city` (board). 
* Each player starts the game with 12 `investment` pieces (the ones you place on and move around the city) and 3 `million` (coins). The coins will be your `cash flow`
* There is a `bank` that holds 30 million (30 coins) at the beginning.
* Before the game starts, you need to place 3 `profitable areas` on the city. You roll the die twice to determine X and Y coordinate of each profitable area:

	1. Place 3 million (stack 3 coins) on the first profitable area
	2. 2 million on the second
	3. 1 million on the third
* Decide who is going to start first.
* Whenever you place / move an `investment` you need to roll the `events` die:

	1. If you roll a `1` then a **public housing policy** makes the value your investment decrease. Pay 2 million to the bank.
	2. A **rent-cap policy** is enforced by the local government, making your investment less profitable. Pay 1 million to the bank. 
	3. **Residents protest**. Roll your move back, either by putting your piece back where it was before rolling the die, or take it out of the board if you were trying to place it.
	4. **Residents pack up and move**. Your investment potential increases. Get 1 coin from the bank and put it under your piece.
	5. **Early gentrifiers** move into the area. They can't afford much rent, but they bring *cultural capital*. Coffee shops and higher-incomes will follow. Your investment is on the rise. Get 2 millions from the bank and put them under your piece.  
	6. **Infrastructure boost**. You can move the same investment once more. This can be quite a devastating move as you may be able to *kill* your opponent's investment if you're lucky to roll a 6 and be in the right place.  
* When you **kill** another piece, you `inherit` any money under it. Once killed, pieces cannot re-enter the game. *Killing* can happen only when your opponent's piece is between yours and an empty area. If there are coins on that area, then it's not empty.
* When you move an `investment` piece from one area to another, you can `cash in` any coins under it. This is useful if your `cash flow` is running low.
* What happens if **you run out of money**? You can exchange 1 investment for 6 millions (need to playtest this further to see if it's balanced).
* What happens if **the bank runs out of money**? Everyone has to pay an equal amount into it (you decide how much). 
* Here's the explosive stuff: **property bubbles**! When a 3×2 rectangle is filled (with any combination of investment pieces and coins) then it *bursts*. You have to roll the die twice to work out the consequences. For example if you roll a `2` then whatever is on the second area (counting from top-left to bottom-right) will **go bust**: any coins on that are return to the bank, and if there's an investment involved then it gets killed (and once killed, it cannot re-enter the game). This mechanic can be used to disrupt conglomerates of investments from the same player, or if you're desperate.   
* What if multiple bubbles are triggered at the same time? The player who moved the triggering investment decides which bubble to burst, then if the other bubble is still a bubble after you rolled the die twice, you burst than one too. 

#### Playtesting the above, round one

A very useful (and challenging) aspect of playtesting is when you have to **explain the rules of the game to a new player**. While doing this you can uncover flaws, and you get a sense of whether the overall logic makes sense, whether there are *too many rules* or conflicting ones. You also come up with ideas to simplify and clarify the wording of your rules.

My general impression is that you don't need to explain all the rules at once. It's easier to start with the fundamental mechanics through a **live tutorial**: people understand better by seeing the moving pieces. You can then introduce more complex rules or less likely scenarios by guiding the moves of the new player(s). After a few minutes they will feel more confident in their grasp of the game, so you can start playing competitively.

Now, back to this specific game. What we observed:

* The principle of `when you move into a new area you roll the events die` should be **consistent**. Eg, no matter whether you get there because you just rolled a 6 (extra move) or you just triggered a property bubble burst, first thing you do after moving is always rolling the `events` die
* The 3 coins you start the game with may run out quickly. I'm not too worried about this, as it forces you to give pieces away or to `cash in`
* To be brutal, the game feels like *Yoté with a bit of chance*, in the sense that the new mechanics don't seem strong enough to make you move much differently than if you were just playing the traditional version of the game. Running out of cash can have an impact on your game, but having a lot of it doesn't have any real consequences (apart from keeping you afloat). Maybe you can buy game pieces with a certain number of coins (6?)
 

## Glossary

* Game piece > `investment`?
* Board square > `area`?
* Capture / kill a piece > `kill the investment`? What's business lingo for destroying your competition? `undercut`? 



























<!--

> This experiment exploits the *buy low and sell high* mechanic, where profit is the goal of both players.



- [ ] First player tactics (occupying corners) vs second player tactics (reactive and aggressive positioning)?
- [ ] We could introduce some sort of currency. At first you occupy the land for free, but then (when?) you need money to place your pieces. Every time you kill a piece you could get money (price varies according to how crowded the board is) and with enough money you could price out your opponents. 
- [ ] As you play you learn to invest in the stubby ones near the rising ones as the wealth bubble infects its surroundings, then you start to see the height at which they become the most valuable in order to sell?

### Yoté

Clear game rules: http://www.di.fc.ul.pt/~jpn/gv/yote.htm

People playing it on sand in Senegal: https://www.youtube.com/watch?v=c9n4z2-C5oI

Yoté on BGG: https://boardgamegeek.com/boardgame/9385/yote


From this review: https://boardgamegeek.com/thread/653401/not-your-run-mill-game

> The corners are the most defensively strong positions on the board because they cannot be jumped in either direction. The edges of the board are the next most defensively strong because they can only be jumped in a single direction. Then the centre of the board is the weakest area. […] If one imagines a pair of pieces in the same row, one at a first space and the other at the fourth which both pieces protected from the outside either by another piece or an edge of the board. Any piece placed by the opponent on either position two or three would be immediately captured. Then pieces placed in the adjacent row are protected relatively in at least one direction.

> […] So if both players establish defensible positions from which to build out before going on the attack, the first player has a very strong advantage in that scenario.

> An alternate style of play is that style in which one concentrates from the beginning on placing one’s pieces on the board in such a manner so as to hem in one’s opponent. This style tends to initially place pieces diagonally next to the piece previously placed by the opponent. Clearly this style of play favours the second player both because he will have a tendency to have a piece in the reserve longer than the first player and because by responding to the play of the first player the second effectively goes on the attack and so puts the first player on the defensive. If both players take this style of approach to play, the second player has a strong advantage.

In short, the first player is encouraged to occupy the corners&edges and play defensively, whilst the second player is encouraged to place their pieces diagonally next to the first player’s ones, and so play with a more reactive and aggressive style.

> The lack of compulsory capture and the taking of an arbitrary second piece whenever a capture is made sets the game apart from any other draughts-like game. In particular, most draughts-style games are dominated by players trying to force the other player into unequal exchanges. Such a approach just does not work in this game because the first player simply captures an opponent’s piece and then selects as the second piece whichever piece threatens one of his own pieces. Only in rare case where a move creates two or more threatening pieces could such a sacrifice-based approach work; even then the first player is never compelled to make a capture in the first place.

This emphasises how the Kill-1-get-1-free and the killing-not-compulsory mechanics set this game apart from other draughts-style games (making it less predictable?)

#### The Fulani people

From https://en.wikipedia.org/wiki/Fula_people

> The Fulani people have held on to “a strict caste system”

> They herd cattle, goats and sheep across the vast dry hinterlands of their domain, keeping somewhat separate from the local agricultural populations. They are the largest nomadic ethnic group in the world, and inhabit several territories over an area larger in size than the continental United States.

> Recurrent droughts have meant that a lot of traditional herding families have been forced to give up their nomadic way of life, losing a sense of their identity in the process. Increasing urbanisation has also meant that a lot of traditional Fulani grazing lands have been taken for developmental purposes, or forcefully converted into farmlands. These actions often result in violent attacks and reprisal counterattacks being exchanged between the Fulani, who feel their way of life and survival are being threatened, and other populations who often feel aggrieved from loss of farm produce even if the lands they farm on were initially barren and uncultivated. 

> What makes a person Fulani is pulaaku (“Fulaniness”), which consists of four basic tenets.

	1. Munyal: Patience, self-control, discipline, prudence
	2. Gacce / Semteende: Modesty, respect for others (including foes)
	3. Hakkille: Wisdom, forethought, personal responsibility, hospitality
	4. Sagata / Tiinaade: Courage, hard work

### Gentrification 

- [ ] http://www.economist.com/blogs/blighty/2014/04/gentrification-london

-->

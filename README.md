Here are descriptions of recent software projects I'm allowed to discuss (i.e. non-professional work.)

## GM Trainer

[GM Trainer](https://github.com/maxwelljoslyn/gm-trainer) is a sandbox environment for RPG Game Masters (GMs) to realistically practice spontaneous creativity. It uses LLMs to simulate human players' responses to the GM's descriptive narration, giving GMs a training ground to exercise critical skills like improvising descriptions, decisively answering player questions, and giving logical game-world responses to player actions.

<img width="1372" alt="screenshot" src="https://github.com/maxwelljoslyn/maxwelljoslyn/assets/11641081/8df54159-4002-42bb-ae31-5d029cc03498">

## Master's Thesis: The Computer-Driven, Human-Controlled TTRPG

For my [MSc research thesis](https://escholarship.org/uc/item/0r9246gd), I researched, designed, and programmed ROLEPLAYINGGAME[^1], the first tabletop-RPG companion app to support runtime editing of game rules and content without stopping gameplay. My aims were to:
1) Combine the flexibility of traditional RPGs with the complex, real-time processing of videogames by **enabling game worlds and game rules to grow and change during use.**
2) Assess the viability of an all-in-one platform not only for playing and GMing RPGs, but also for designing them, because **game designers' needs aren't met by existing apps.**

ROLEPLAYINGGAME is a web application. To target the browser, I needed a way to evaluate game rules on the backend and frontend alike, for server-side validation and rule-sensitive UIs respectively. I avoided code duplication by implementing ROLEPLAYINGGAME in **Clojure**, which has production-grade compilers to both Java and JavaScript. This made >95% of my backend code portable to the frontend.

To efficiently make game state available to frontend clients, whenever a user action changed the game state, I sent a diff from the server to all clients. Having game state available on clients was necessary to keep information-rich UIs up to date. One of those UIs is shown below.

<img width="524" alt="The GM's Inspector, with a command and one parameter specified." src="https://github.com/maxwelljoslyn/maxwelljoslyn/assets/11641081/2d412f53-fa5d-420f-9586-f89c9bd6ba50">

*The Inspector, part of the Game Master's UI, affords rapid, context-aware interaction with all game entities.*

In this screenshot, a GM is using the Inspector: a context-sensitive menu for dispatching commands on in-game entities. For each command (like `dislocate`), the parameters for which the character Arvak can slot into (like `target-entity`) are dynamically discovered by introspection on Clojure functions. The GM can click any entity on any main UI screen to add it to the Inspector[^2].

## Computational TTRPG Tools

My master's thesis grew out of my long-standing interest in implementing tabletop RPG systems in software. Before starting my MSc, I had already developed several **Python** tools for my own custom game system, including a pricing simulator for over 1,000 17th-century items, a program that generates characters' life stories based on their stats, and CLI tools for rapidly updating the game world during live gameplay.

<img width="1048" alt="One vendor from a market price table from my homemade RPG app." src="https://github.com/maxwelljoslyn/maxwelljoslyn/assets/11641081/5c7ee7a2-5c72-4cc0-8bf2-e6de5f93ba0b">

*One of the tables created by the pricing simulator.*

The pricing simulator brings depth, granularity, and logic to an aspect of RPGs that has never progressed beyond numbers made up on the spot. As an example of my dedication, here's an explanation of how it works.

The simulator inputs are encyclopedia data on the relative abundance of raw materials at real-life cities. Every city "exports" some fraction of its resources everywhere else, using an all-pairs shortest path network. We then determine raw material prices for each city: the more abundant, the cheaper the unit price.

Tens of thousands of calculations specify how raw materials transform into purchasable tradegoods, specifying quantities like the length and radius of a spear haft, the thickness of a clay pot, and the amount of wood needed to build a half-timbered house. Each tradegood is defined by a "recipe," which I create by researching 17th-century manufacturing. A recipe consists of raw materials and other, simpler recipes, so the set of recipes forms a [directed forest](https://en.wikipedia.org/wiki/Tree_(graph_theory)#Polyforest). Summing the prices of a recipe's components gives the tradegoods's final player-facing price[^3].

## Ryan Quest

I made [the text adventure *Ryan Quest*](https://www.maxwelljoslyn.com/ryanquest) as a surprise birthday present for my best friend from college, Ryan Wright. The player controls Ryan in a parody of his real life. After doing all the writing, coding, and user testing, I flew out to surprise him with the game in person.

*Ryan Quest* was written in [Inform 7](https://www.inform7.com), an unusual programming language which is laser-focused on being good for creating interactive fiction.

[^1]:  An acronym for **R**PG **O**peration, **L**earning, and **E**xecution **P**latform **L**aden with **A**dvantages for **Y**ielding **I**nfinitely **N**itty-**G**ritty **G**ames that **A**llow **M**alleable **E**volution.

[^2]: For instance, the exploration hex grid (partially shown above) would let the GM operate on characters, items, and individual hexes just by clicking.

[^3]: This explanation glosses over some complexities relevant to game design, but not to engineering; I'd be happy to discuss my work (and yours!) in more detail [by email](mailto:maxwelljoslyn@gmail.com).

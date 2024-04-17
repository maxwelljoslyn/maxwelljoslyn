Here are explanations and screenshots for recent software work which I'm proud of.

## GM Trainer

I'm currently working on [GM Trainer](https://github.com/maxwelljoslyn/gm-trainer), a sandbox environment in which RPG Game Masters (GMs) can get focused practice with spontaneous creativity. It uses LLMs to simulate human players' responses to the GM's descriptive narration, giving budding GMs a way to exercise critical skills like improvising descriptions, decisively answering player questions, and giving logical game-world response to player actions.

Currently, most work at the intersection of RPGs and AI is focused on proof-of-concept attempts to replace the GM -- but a GM is responsible for real-time creation and evolution of an enormous, **self-consistent** game world, which AIs are nowhere close to achieving. However, I'm discovering that AIs can simulate an RPG _player_ sufficiently well that this usage paradigm could have a real impact on how people learn to acquire the nuanced, many-faceted skill of GMing.

## Master's Thesis: The Computer-Driven, Human-Controlled TTRPG

For my [MSc research thesis]([url](https://www.maxwelljoslyn.com/static/maxwell-joslyn-ms-thesis-v1.0.3.pdf)), I designed, coded, and user-tested ROLEPLAYINGGAME[^1], the first-ever tabletop RPG companion app to support runtime editing of game rules and content without stopping gameplay. I aimed to combine the flexibility of traditional RPGs with the complex, real-time rule evaluation of videogames.

<img width="524" src="https://github.com/maxwelljoslyn/maxwelljoslyn/assets/11641081/160e989f-b0a2-4752-9391-f3b4e759f304">

<img width="524" alt="The GM's Inspector, with a command and one parameter specified." src="https://github.com/maxwelljoslyn/maxwelljoslyn/assets/11641081/2d412f53-fa5d-420f-9586-f89c9bd6ba50">

## Computational TTRPG Tools

My master's project grew out of a long-standing personal quest: creating a custom tabletop RPG with rules so detailed they could only exist as software. Before starting my MSc, I had already developed several tools in this area, including a pricing simulator for over 1,000 17th-century items, a program that generates characters' life stories based on their stats, and CLI tools for rapidly updating the game world during live gameplay.

I'll discuss the pricing simulator below. Here's one of the 50ish tables it creates:

<img width="1048" alt="One vendor from a market price table from my homemade RPG app." src="https://github.com/maxwelljoslyn/maxwelljoslyn/assets/11641081/5c7ee7a2-5c72-4cc0-8bf2-e6de5f93ba0b">

The pricing simulator begins with encyclopedia data I've collected on the relative abundance of raw materials at numerous real life towns and cities. The more abundant a material is, the cheaper it is per unit. Tens of thousands of calculations specify quantities like the length and radius of a spear haft, the thickness of a clay pot, or the amount of wood needed to build a shed (unit-aware calculations are made easy with [Pint](https://pint.readthedocs.io/).)

Each of the player-purchaseable items is defined by a "recipe," which I write by doing research on 17th-century manufacturing. Each recipe consists of raw materials and other, simpler recipes; summing the prices for these components gives us the final player-facing price[^2]. Altogether, the set of recipes forms a [directed forest](https://en.wikipedia.org/wiki/Tree_(graph_theory)#Polyforest).

## Ryan Quest

I made [the text adventure *Ryan Quest*](https://www.maxwelljoslyn.com/ryanquest) as a surprise birthday present for my best friend from college, Ryan Wright. The player controls Ryan in a parody of his real life. After doing all the writing, coding, and user testing, I flew out to surprise him with the game in person.

*Ryan Quest* was written in Inform 7, an unusual programming language (its syntax looks a lot like English) which is laser-focused on being good for creating interactive fiction (including text adventures.)

[^1]:  An acronym for **R**PG **O**peration, **L**earning, and **E**xecution **P**latform **L**aden with **A**dvantages for **Y**ielding **I**nfinitely **N**itty-**G**ritty **G**ames that **A**llow **M**alleable **E**volution.

[^2]: This glosses over some complexities.

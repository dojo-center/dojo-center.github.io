## Stephen Wolfram, cellular automata and the mind
 
1. It is perhaps a little humbling to discover that we as humans are in effect computationally no more capable than cellular automata with very simple rules.

If you aren't familiar with the cellular automata reference, it would be useful to explain that.

Cellular automata were first described by John Von Neumann in discussion with Stanislaw Ulam and dating first to their interactions at Los Alamos in the 1940's.

Cellular automata are best simply described as a cell on a two dimensional graph with a finite number of neighbor cells.

![Cellular automata](link)

Automata also have a specific rule applied to them, and this determines their path in this two dimensional world.

A common and great visualization of cellular automata in action is Conway's Game of Life.

![Game of Life](link)

Wolfram's quote is then saying that our minds make decisions in a limited number of directions from our current state, then the next state has a same number of possible choices after that decision.

It's significant that Wolfram believes that the rules for the mind are also a simple cellular automata rule. A rule dictates what the cell does in its two dimensional state and the complexity of its action. Rules for cellular automata have a given graph that helps visualize their progress through space and time.

![Cellular Automata Rule Diagrams](link)

Now imagine a hypothetical engineer at a tech company. They have great experience and every indication that they are highly capable at their job. And while they want to take the next step in their career, they have not been allowed this step yet. It turns out that they have had some rough interactions with peers at work, and the word spread that they are, at times, hard to work with.

Have you ever run into someone like this where you work?  I have. I have also been this person!

The truth is that in the wildly complex tech world, where advanced systems interact to give us incredible options at the touch of a finger, humans are still humans. Humans continue to act in ways that humans have always acted and interacted. This won't (and probably shouldn't) go away anytime soon.

There are several different scenarios above that can be independently, or collectively, true.

There may have been one or more bad interactions with other people at the company. There may not have been an interaction, and a story just took shape that took on a life of its own. Or the interaction was not that bad but the subsequent telling of the story made it much worse than it was.

Now imagine that you actually witness an interaction like this. 

In your imaginary scenario, do you know the complete context of the interaction? The history that happened right before the interaction? Or do you know if there were previous interactions that were relevant? Or the conversations that the people involved had with other people in the company that may also be relevant?

In many cases, the history of what led up to a memorable interaction would look a lot like a decision tree, or more accurately, a graph database with many nodes and many connections. In reality it won't be possible for us to understand the complete context of any given interaction, even when we are involved! Since we would need to know the history of conversations that happened with the other person before we interacted with them.

![Decision tree](link)
![Graph database](link)

But how do we usually judge a situation like the above if we witness it? The truth is, the human mind will try to simplify a situation down to as small an answer as possible. In this case, folks will usually want to boil things down to a "bad" person and a "good" person, and we'll want to take the side of the good person.

This gets problematic in a complex corporate environment, because these decisions can have meaninful and lasting results. If we choose who is good and who is bad in an interaction, and this story spreads within an organization, this could have negative impact for the person involved. 

And this result can have an even bigger impact that we assume. If the person who is affected is in a critical role for supporting core product(s), the affect on the person will now probably have an affect on the product. If the person then leaves the company due to this, it could have very large and specific effects on the product.

Now imagine the complexity of how that result spreads into the future. The product may be supported in a sub optimal way for the future, if the person effected had input on the feature list then it may have a strong effect on the success of the product going forward. And if there are other people whose job is to support the product, it will effect their future as well.

So now we can see a simple interaction has a highly complex history that precedes it, and possibly complex results that result from it, including ones that may affect many people and even the company as a whole.

So why do we boil these situations down to a simple answer that has a good chance of being incorrect and may have highly negative outcomes for the future.

It goes back to Wolfram's statement on the mind and cellular automata. We approach highly complex situations but we have to approach it with a mind that is limited to how much complexity it can understand.

2. So while science has often made it seem that we as humans are somehow insignificant compared to the universe, the Principle of Computational Equivalence now shows that in a certain sense we are at the same level as it is. For the principle implies that what goes on inside us can ultimately achieve just the same level of computational sophistication as our whole universe.

Wolfram's statement here is a great counterbalance to the quote above. While our minds are not more complex than cellular automata, the rules of the universe are also not a level of complexity above that. So we hypothetically have a great power and potential in our minds to understand the universe.

We are very often so caught up in the day to day work of our lives that we rarely get a chance to look up and observe the progress.

Have you ever had this chance to pause and look back at your accomplishments, and been somewhat awestruck and amazed at the progress you have made?

There was a point years ago when the company I was working for needed to refactor our production deployment infrastructure (see chapter on David Hume).

We had many tiers in production to refactor. It involved different technologies across different hosting operating systems, so a unified process was most likely not possible.

Our first step was to determine what (open source) technologies to use to do the deployments. This was a quick task at the beginning where we simply queried the industry via search engines and found out what technolgies companies (who generously shared their stories) were using. We chose Capistrano for Linux deployments and PowerShell for Windows.

Now we had to dive into all of the builds (I think it was already in the dozens at this point, if not a hundred) that needed a corresponding production deployment. The work was split up among the team based on expertise. There was the added complexity (probably recognized by many) that we needed to keep the current state of production deployments going at the same time we were refactoring the work.

We ground out this code over a period of months. We made advancements one at a time, then kept moving on to the next challenge. There were some struggles along the way (one deployment was completely unique and segmented into one environment for a specific customer, and the deployment complexity was greater than the more vaulable shared deployments), but we did not hit any blocking issues.

After some months, we had most of the work done, enough so that the licensed product we had been using could be removed and we could rely on our code. 

We were so busy during this migration that we did not have a chance to look back and understand what was accomplished. We were immediately moved onto new work once that was complete (another thing that I think most people can identify with), so we did not get a chance to look at this work once complete either.

But now looking back, we had juggled an immense amount of complexity with a limited amount of time across a team of several experts with no long blocking issues and no conflict. 

How did we do it?

The end result is like a complex graph of cellular automata.

![Cellular automata - complex](link)

What this shows that each step within the work is a series of specific steps based on a specific rule. We knew the target of the work (create a successful production deployment based on open source technology) and we knew the limitations of the rule (a Windows vs a Linux deployment for example).

3. “What will limit us is not the possible evolution of technology, but the evolution of human purposes.”
4. Whatever input it’s given, the neural net is generating an answer. And, it turns out, to do it in a way that’s reasonably consistent with what humans might do. As I’ve said above, that’s not a fact we can “derive from first principles”. It’s just something that’s empirically been found to be true

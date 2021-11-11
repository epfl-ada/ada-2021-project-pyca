# Propositions
## Idea 1
Train a machine learning model to determine who said a given citation, using the citations from the whole dataset which have an author with probability over 60%.
The idea, given a new citation (any citation that is not in the dataset), is to find who said it, generating a list of possible authors with probability.
A related project, maybe more realistic, would be to restrain the training dataset to a single topic (eg. American politics) and train the model to determine the "side" of the speaker (eg. political party, democrat vs republican).
An interesting application would be to determine the "objective" political stance of someone (eg. a politician) or of a group (eg. a political party), comparing it with what other people said.
In France for example there are lots of political parties and even in one party politicians have very varied opinions, it could be interesting to either select one politician and compare him/her with the others, or to select one political party and compare it with the others depending on the citations of its members.

## Idea 2
Check if the idea that young people are more on the left side politically while the older people are more on the right side is true.
Assuming we have a model that tells us if some citation was said by a democrat or a republican like mentioned in idea 1, we can generate a plot of the political stance depending on the age of the speaker, either for a particular speaker or with several speakers at once, and either using the proportion for each people of left-wing vs right-wing citation, or plotting the position of every citation.
More data would be necessary to realize this project: firstly older citations to have a better sight on the political evolution of a given person, and secondly more varied citations, not just from politicians but also from the general public, since the idea is to check the assumption in the general population, but also because politicians might be heavily biased into staying in the same political party.

## Idea 3
Cluster the citations depending on the topic, and generate a heat map of the various topics in the end.
We can determine the proximity of two citations using the keywords, a synonyms dictionary and / or NLP models. This heat map could even evolve depending on the time, and could show new topics appearing and disappearing from the news (eg. coronavirus, the panama papers, etc).
One issue with this project as is, is that a citation could belong to more than one topic, so representing this could be delicate, solution to this issue could be to count each citation one time for each topic, instead of only a single time.

# Feedback
## Feedback
Needs minor improvements

## First idea
Even though this is a nice idea and could even be useful for the dataset itself, as many of the quotes are missing the speaker, there are many speakers in the dataset so this might be a very ambitious and impossible task. Second idea seems more feasible. Keep in mind that Quotebank has only data from English news so finding speakers from some smaller countries might be a bit more difficult,

## Second idea
How do you determine that one particular quote is right/left? First idea categorizes speakers but not the quotes - someone can be right-wing politician but the quote might still be about left-wing topic.

## Third idea
What is the use case for this map?

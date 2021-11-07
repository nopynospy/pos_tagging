# pos_tagging

# Closed-class words and NLTK's POS tagging

English words are always expanding and contain many ambiguities, for example, 'fish' can be a noun or a verb, depending on the context. However, with closed-class words, such as determiner and to-infinitive, 'a fish' is a noun and 'to fish' is a verb. Closed-class words are mainly used for grammatical functions and are very limited in number, so I thought maybe I can improve NLTK's POS tagging and chunking with them.

In the notebook, using some examples from linguistic books, I have examined and improved on the chunking of:
1. Compound nouns (bus stop)
2. All tenses and their passives
3. Yes/no question (questions with do, have)
4. Pronouns (words that can replace noun like he, she, what)
5. Adjective phrases (very cool)
6. Possessive -s (Cat's paw)
7. Determiners (this, that, a, an)
8. Prepositions (above, on top of)
9. Quantifiers (many, a lot of)
10. Modal auxilaries (can, might, will)
11. To as preposition vs. to as infivitive (to school, to eat)
12. Phrasal verb (move on, clean off)
13. Noun phrases (his eyes, the big cat)

I have also proposed the use of more than 2 chunkers on a sentence when rules in the first chunker have internal conflict. For example, "He turned in his homework" can be chunked as "turned in" (phrasal verb = verb + preposition) or "in his homework" (prepositional phrase (prepositional phrase = preposition + noun phrase)). There will be internal conflict if both rules are set in the same chunker, so having 2 chunkers can mitigate such ambiguities.

In addition, I also came up with the method of directly changing the result of POS tagging to 'force' certain desired result in chunking. For example, somehow adding pronoun (PRP$) to chunking grammar rule does not work. I wanted pronouns such as "my" to be considered as a noun phrase, so I just 'forcefully' change its pos to determiner (DT) in the list of dictionary, which then led to pronoun "my friend" being chunked as a noun phrase, as I wanted. I did something similar to multi-word prepositions, such as in front of, by changing 'front' from a noun to a preposition. Thus, in, front and of are all prepositions, leading to the phrase being chunked as a prepositional phrase, as per specified in my grammar rule.
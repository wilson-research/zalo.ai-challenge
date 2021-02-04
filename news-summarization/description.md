# Description

Text summarization is one of the most difficult and interesting tasks in NLP today.
It helps people to acquire important information in long documents without reading their whole contents.  

This challenge focuses only on football match summarization which is a specific domain of online news summarization.   

For each input new article, you must determine whether or not it is a football match report 
then produce the summary of the match follow a template if it is possible.
Otherwise, the result should be empty. A match summary includes several kinds of information 
such as participating teams, match results, goals, cards, substitutions. 

A training set with labels is provided for your training.
A test set contains only articles without any match annotation. 
For each article, a participating system will need to output a match result summary if it is possible, otherwise empty.
Teams are scored and ranked by F1 measure on the test set.

### Input and output

**Input:** Given an football match report between two teams

**Output:** A match summary that summary the result of the match:

* Teams:<br/>
(team1, team2)
* Score board:<br/>
(score1, score2)
* Score List:<br/>
[(player_name, team, time), ...]
* Subsitution List:<br/>
[(player_in, player_out, time), ...]
* Card List:<br/>
[(player_name, team, time), ...]

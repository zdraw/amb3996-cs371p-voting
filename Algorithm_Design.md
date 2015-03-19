# Introduction #

The Australian voting problem is that Australian ballots require voters to rank all candidates in order of preference instead of vote for just one. If one candidate wins more than 50% of the vote, that candidate wins. Otherwise, every candidate in last place is removed from the race, and those ballots are awarded according to their respective second-choice candidates. This process continues until one candidate wins more than 50% of the ballots or every remaining candidate is tied. As a voting process, this method requires that a candidate have at least 50% of the vote otherwise a tie will occur. Without adding more rules, there is no way to break the tie because everyone who is not tied is removed from all the ballots. In our case, if we encounter a tie, all the candidates who tied are printed out.


# Details #

We will write 4 methods in Voting.h to handle each component of the program: read, write, solve, and eval.

Solve:
  * Get the first line of input. This line contains the total number n of testcases.
  * Loop n times, reading one test case at a time, evaluating it, and writing the name of the winning candidate(s) to the outputstream.
  * Before going to the top of the loop, if this iteration is not the last then output a newline to separate the outputs of cases.

Read:
  * Read first line of input. This contains the number n of candidates.
  * Store n candidates into a vector of strings.
  * Until a blank line is encountered or end-of-file occurs, read ballots and store votes into an array.
  * The votes are tokenized by a stringstream.
  * The array will be copied to a ballot object containing the votes and  an index to the current vote.
  * Return vector of candidates and vector of ballots.

Eval:
  * Create a vector for each candidate and sort ballots into their respective vector.
  * Compare the size of each vector against the total number of ballots. If one array has more than 50% of the ballots, its candidate wins.
  * Otherwise, find out who is tied for last and redistribute those candidates' ballots.
  * The redistribution process looks at both the candidates that have been removed and are currently in last place.
  * Repeat bullets 2 and 3 until a winner is found or there is a tie.
  * Returns a string containing the winner(s).

Write:
  * Takes in the string returned by the Eval function.
  * Write the name of the winning candidate plus a blank line.
  * In the event of a tie, the Eval function will have returned a string without a new line at the end so that the write function will perform correctly.
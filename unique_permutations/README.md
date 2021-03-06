## BACKGROUND ##
A fun interview question from 2010. Took me 1/2 the weekend... but I got through it!

## DESCRIPTION ##
Once I changed my implementation to use recursion, I got the correct N! number of permutations. The next challenge was to keep track of which permutations were produced already. I wasn't able to fit all of them in memory so what I winded up doing was splitting the permutations into shards on the filesystem based on the first k chars. (ie, SHARD_aaaabb, SHARD_aaaabk, etc..) So what my code will do is produce k! files temporarily on your filesystem and then merges them at the end of the script and deletes the shard files.

The result is 831,600. I came up with the formula for unique permutations as:

> N! / (K1! x K2! ...)
>
> N=number of chars
> K=the number of occurrences of a particular char in N

## PERFORMANCE ##
The complexity of the solution is O(N!). The enclosed file was produced in just under 25 min on my machine with possible improvement if I were to shard further. (I ran it with 6! shards) The usage of the filesystem to keep state reduced performance significantly.

## MEMORY USAGE ##
Because of the nature of my solution, there wasn't that much memory used in terms of runtime memory. The data was mostly stored on disc and merged up at the end. Total max disc usage was roughly the size of the produced file.

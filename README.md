# Today's interview

### First of all
I'd like to thank to Arkadiusz and Filip for a very nice atmosphere during the interview!
Maybe it will sound a little weird, but I really appreciate, we have stayed formal. This is much more comfortable 
for an examined as it keeps symmetrical distance. I believe we will have an opportunity to become colleges.
Moreover, it is very kind, when interviewer answers the question or explain it shortly once he/she is not 100% happy 
of the answer. 
Great, thank for very well provided interview.


#### ABBA
Filip asked me, how to swap 2 numbers (e.g ```int```) without using additional auxiliary variable.
I was thinking about playing with sum, to not lose an information. And that was pretty close, that you said OK.
After I had come home I have found solution :

Imagine we have two numbers **A** and **B**, and no more memory space for auxiliary variable. 
In describition below A,B stays for values, while order defines variable 1 or 2.

We start then with :
```A , B```
in memory. 

In next step at first position I write sum of two variables, keeping B unchanged.

``` A+B, B```

This is one step operation, and no information is lost. Moreover, I have choosed sum, as it is symetrical : A+B = B+A.

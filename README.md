# interview A

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

This is one step operation, and no information is lost. Moreover, I have choosen sum, as it is symetrical : A+B = B+A.

In a second step I will keep 1<sup>st</sup> variable unchanged while as a second one I put `var_1 - var_2`.

```A+B, A```

Finally, I do the same with a first variable (`var_1 - var_2`) leaving 2<sup>nd</sup> unchanged :

```B, A```

In summary:

```A,B -> A+B, B -> A+B, A -> B, A ```

That's it. I called it ABBA as A,B -> B,A. I haven't searched on the web yet - I swear.

Filip, you have asked that further one could ask what would happen if we reach MAX of int (as in this example).
To answare it, it is worth to know, how integers are coded, kept in Java. In binary representation their are cyclic.
This means `MAX + 1 = MIN`. **Thank to** that it is **cyclic**, it **do not metter** where we start, so described algorith will **work fine** also when numerical **limits are reached**.

I wrote a small code in Java to check it:
```java
	public static void main(String[] args) {
		// auxiliary to check binary cyclicism
		final String FORMAT = "%11d      %32s%n";
		Integer [] tab = {Integer.MIN_VALUE, 0, -1, Integer.MAX_VALUE, Integer.MAX_VALUE + 1};
		Arrays.stream(tab).forEach(i->System.out.format(FORMAT, i, Integer.toBinaryString(i)));
		
		System.out.println(" - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -");
		
		
		Integer a= Integer.MAX_VALUE - 1000;
		Integer b= 2000;
		
		// ABBA test
		
		final String FORMAT2 =  "A=%11d      %32s  ,   B=%11d      %32s%n";
		// step 0
		System.out.format(FORMAT2, a, Integer.toBinaryString(a), b, Integer.toBinaryString(b));
		a=a+b; // b=b; 
		System.out.format(FORMAT2, a, Integer.toBinaryString(a), b, Integer.toBinaryString(b));
		/* a=a; */ b=a-b;
		System.out.format(FORMAT2, a, Integer.toBinaryString(a), b, Integer.toBinaryString(b));
		a=a-b; // b =b;
		System.out.format(FORMAT2, a, Integer.toBinaryString(a), b, Integer.toBinaryString(b));
	}
```

#### Concerning creation of an immutable Class in Java
I have systematized the subject with a very nice blog [page](https://www.journaldev.com/129/how-to-create-immutable-class-in-java). 

#### Concerning Java implementation of Singleton
Again, great description example can be found [here](https://www.javaworld.com/article/2073352/core-java/simply-singleton.html?page=2).
Of cource there is no need of instancies counter, but as **a instancie indicator** one could just **use** ... **an instance of the class itself**, putting it into private static field.
Taking into account thread save we have, lazy Singleton:
```java
public class LazySingleton {
	// Lazy
	private static LazySingleton instance = null;
	
	private LazySingleton() {}
	
	public static LazySingleton getSingleton() {
		if(instance==null) {
			synchronized(LazySingleton.class) {
				if(instance==null) {
					instance = new LazySingleton();
				}
			}
		}
		return instance;
	}
}
```
or eager :
```java
public class EagerSingleton {
	// Eager
	private static EagerSingleton instance = new EagerSingleton();
	
	private EagerSingleton() {}
	
	public static EagerSingleton getSingleton() {
		return instance;
	}
}
```
#### What is in fact a Git branch?
The answer seems simple, but the SVN heritage can seriously distort it.

In fact in Git branch is not a phisical object as in SVN. 
Creating a brach cost nothing in time and memory (what you pay for are Snapshots of new/changed files).

In Git a branch is simply a lightweight movable pointer to one of these snapshot commits, as you can read [here](https://git-scm.com/book/en/v1/Git-Branching-What-a-Branch-Is).

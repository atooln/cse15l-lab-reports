# Lab Report 4: Challenge Task Speedrun 

This is my guide on how to speedrun the CSE15L Week 7 Challenge. 

## Steps of the challenge

1. Log into ieng6
2. Clone your fork of the [repository](https://github.com/ucsd-cse15l-w23/lab7) from your Github account
3. Run the tests, demonstrating that they fail
4. Edit the code file to fix the failing test
5. Run the tests, demonstrating that they now succeed
6. Commit and push the resulting change to your Github account

## Walkthrough

### Step 1: Log into ieng6

```
> ssh cs15lwi23adp@ieng6.ucsd.edu 
```

with my current  [terminal](https://www.warp.dev/), I have the above command saved. All I had to type was ``` ssh<right arrow><enter> ``` to autocomplete the command. 

### Step 2: Clone your fork of the repository
```
 > git clone git@github.com:atooln/lab7.git  
 ```
I already had the ssh URL copied so all I had to do was type ``` git clone<CTRL V><enter> ```

### Step 3: Run the tests and confirm that they fail
```
> cd lab7/

> ls
ListExamples.java  ListExamplesTests.java  lib

> javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java

> java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests
JUnit version 4.13.2
..E
Time: 0.53
There was 1 failure:
1) testMerge2(ListExamplesTests)
org.junit.runners.model.TestTimedOutException: test timed out after 500 milliseconds
	at java.lang.System.arraycopy(Native Method)
	at java.util.Arrays.copyOf(Arrays.java:3213)
	at java.util.Arrays.copyOf(Arrays.java:3181)
	at java.util.ArrayList.grow(ArrayList.java:267)
	at java.util.ArrayList.ensureExplicitCapacity(ArrayList.java:241)
	at java.util.ArrayList.ensureCapacityInternal(ArrayList.java:233)
	at java.util.ArrayList.add(ArrayList.java:464)
	at ListExamples.merge(ListExamples.java:42)
	at ListExamplesTests.testMerge2(ListExamplesTests.java:19)

FAILURES!!!
Tests run: 2,  Failures: 1



 ```

 I used the following command sequence to enter into the ``lab7`` directory and run the junit tests. This is what I typed: ```cd l<tab> -> ls<enter> -> javac -cp<left arrow> -> java -cp<right arrow>```. I had the junit commands saved within my terminal, so all i had to do was right arrow to complete.



### Step 4: Edit the code file
``` 
> cat ListExamples.java
import java.util.ArrayList;
import java.util.List;

interface StringChecker { boolean checkString(String s); }

class ListExamples {

  // Returns a new list that has all the elements of the input list for which
  // the StringChecker returns true, and not the elements that return false, in
  // the same order they appeared in the input list;
  static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(0, s);
      }
    }
    return result;
  }


  // Takes two sorted list of strings (so "a" appears before "b" and so on),
  // and return a new list that has all the strings in both list in sorted order.
  static List<String> merge(List<String> list1, List<String> list2) {
    List<String> result = new ArrayList<>();
    int index1 = 0, index2 = 0;
    while(index1 < list1.size() && index2 < list2.size()) {
      if(list1.get(index1).compareTo(list2.get(index2)) < 0) {
        result.add(list1.get(index1));
        index1 += 1;
      }
      else {
        result.add(list2.get(index2));
        index2 += 1;
      }
    }
    while(index1 < list1.size()) {
      result.add(list1.get(index1));
      index1 += 1;
    }
    while(index2 < list2.size()) {
      result.add(list2.get(index2));
      index1 += 1;
    }
    return result;
  }

}

> vim ListExamples.java
```

To quickly see the contents of the code file, I used ``` cat Li<tab><enter> ```. After doing a quick check I was able to find the error so I used vim to edit the file. I typed ``` vim Li<tab><enter> ``` to edit in vim, i typed ``` <shift>G -> kkkk -> i  ``` to navigate to the bottom of the file and then to the correct line using ``` k ```, and finally entering editing mode using ```i```. I made the necessary changes to the code file and saved it using ``` :wq<enter>```. 

### Step 5: Repeat the tests
```
> java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests
JUnit version 4.13.2
..
Time: 0.016

OK (2 tests)

```

I had the junit commands saved within my terminal so all I had to do was ``` javac -cp<left arrow> -> java -cp<right arrow> ```

### Step 6: Commit and Push changes to GitHub
```
> git status
On branch main
Your branch is up to date with 'origin/main'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	ListExamples.class
	ListExamplesTests.class
	StringChecker.class

nothing added to commit but untracked files present (use "git add" to track)

> git add * 

> git commit -m "fixed error"
[main 5e47cda] fixed error
 Committer: Atul Nair <cs15lwi23adp@ieng6-202.ucsd.edu>
Your name and email address were configured automatically based
on your username and hostname. Please check that they are accurate.
You can suppress this message by setting them explicitly. Run the
following command and follow the instructions in your editor to edit
your configuration file:

    git config --global --edit

After doing this, you may fix the identity used for this commit with:

    git commit --amend --reset-author

 3 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 ListExamples.class
 create mode 100644 ListExamplesTests.class
 create mode 100644 StringChecker.class

 > git push
Enumerating objects: 6, done.
Counting objects: 100% (6/6), done.
Delta compression using up to 8 threads
Compressing objects: 100% (5/5), done.
Writing objects: 100% (5/5), 1.83 KiB | 469.00 KiB/s, done.
Total 5 (delta 0), reused 1 (delta 0), pack-reused 0
To github.com:atooln/lab7.git
   f750e52..5e47cda  main -> main
```

In the terminal, I typed ``` git status<enter> -> git add *<enter> -> git commit -m "fixed error"<enter> -> git push```. 

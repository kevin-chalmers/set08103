# Lecture 14: Test-Driven Development (TDD)

## Behavioural Objectives

- [ ] TODO

## What is Test-Driven Development?

Test-Driven Development is development driven by tests.  We write automated tests first.  Development emerges from this process, in that we:

- Only write new code if an automated test fails.
- We eliminate duplication as we only write code to pass a test.

TDD changes individual and group behaviour as:

- Design emerges organically and running code provides feedback.
- Programmers write their own tests, rather than waiting for a QA department.
- Development environments provide feedback on small batch sizes.
- Designs create highly cohesive and loosely coupled components to make testing easy.

The TDD mantra is: **red-green-refactor**:

1. Red - Write a little test that doesn't work, and perhaps doesn't even compile at first.
2. Green - Make the test work quickly, committing whatever sins necessary in the process.
3. Refactor - Eliminate all of the duplication created in merely getting the test to work.
Red/green/refactor - the TDD mantra.

Red-green-refactor.

How do you test your software? Write an automated test.

When should you write your tests? Before you write the code that is to be tested.

If so, then writing only that code which is demanded by failing
tests also has social implications.
If the defect density can be reduced enough, then quality assurance (QA) can shift from
reactive work to proactive work.
If the number of nasty surprises can be reduced enough, then project managers can estimate
accurately enough to involve real customers in daily development.
If the topics of technical conversations can be made clear enough, then software engineers
can work in minute-by-minute collaboration instead of daily or weekly collaboration.
Again, if the defect density can be reduced enough, then we can have shippable software with
new functionality every day, leading to new business relationships with customers.

### Why Test First?

> No software engineers release even the tiniest change without testing, except the very confident and the very sloppy.
> -Kent Beck, Test-Driven Development by Example.

This is a positive feedback loop. The more stress you feel, the less testing you will do. The less
testing you do, the more errors you will make. The more errors you make, the more stress
you feel. Rinse and repeat.

"Did I just break something else with that change?" Figure 25.1 shows the dynamic at work.
With automated tests, when I start to feel stress, I run the tests. Tests are the Programmer's
Stone, transmuting fear into boredom. "No, I didn't break anything. The tests are all still
green." The more stress I feel, the more I run the tests. Running the tests immediately gives
me a good feeling and reduces the number of errors I make, which further reduces the stress
I feel.

Rework time from Agile Requirements.

### Benefits of Automated Testing

I took two lessons from this experience. First, make the tests so fast to run that I can run
them myself, and run them often. That way I can catch errors before anyone else sees them,
and I don't have to dread coming in in the morning. Second, I noticed after a while that a
huge stack of paper didn't usually mean a huge list of problems. More often it meant that one
test had broken early, leaving the system in an unpredictable state for the next test.

One strategy for keeping track of what we're trying to accomplish is to hold it all in our heads.
I tried this for several years, and found I got into a positive feedback loop. The more
experience I accumulated, the more things I knew that might need to be done. The more
things I knew might need to be done, the less attention I had for what I was doing. The less
attention I had for what I was doing, the less I accomplished. The less I accomplished, the
more things I knew that needed to be done.

## Undertaking Test-Driven Development

Once you are finished reading this book, you should be ready to
Start simply
Write automated tests
Refactor to add design decisions one at a time

Which test should you pick next from the list? Pick a test that will teach you something and
that you are confident you can implement.

Which test should you start with? Start by testing a variant of an operation that doesn't do
anything.
The first question you have to ask with a new operation is, "Where does it belong?" Until
you've answered this question, you won't know what to type for the test. In the spirit of
solving one problem at a time, how can you answer just this question and no other?
If you write a realistic test first, then you will find yourself solving a bunch of problems at
once:
Where does the operation belong?
What are the correct inputs?
What is the correct output given those inputs?
Beginning with a realistic test will leave you too long without feedback. Red/green/refactor,
red/green/refactor. You want that loop to take just minutes

Explanation Test
How do you spread the use of automated testing? Ask for and give explanations in terms of
tests.

Learning Test
When do you write tests for externally produced software? Before the first time you are going
to use a new facility in the package.

Another Test
How do you keep a technical discussion from straying off topic? When a tangential idea arises,
add a test to the list and go back to the topic.

Regression Test
What's the first thing you do when a defect is reported? Write the smallest possible test that
fails and that, once run, will be repaired.
Regression tests are tests that, with perfect foreknowledge, you would have written when
coding originally. Every time you have to write a regression test, think about how you could
have known to write the test in the first place.

## Assertions

When should you write the asserts? Try writing them first. Don't you just love self-similarity?
Where should you start building a system? With stories you want to be able to tell about the
finished system.
Where should you start writing a bit of functionality? With the tests you want to pass with the
finished code.
Where should you start writing a test? With the asserts that will pass when it is done.

## Refactoring

In TDD, the circumstances we care about
are the tests that are already passing.

How do you unify two similar looking pieces of code? Gradually bring them closer. Unify them
only when they are absolutely identical.

This refactoring occurs at all levels of scale.
Two loop structures are similar. By making them identical, you can merge them.
Two branches of a conditional are similar. By making them identical, you can eliminate the
conditional.
Two methods are similar. By making them identical, you can eliminate one.
Two classes are similar. By making them identical, you can eliminate one.

How do you make a long, complicated method easier to read? Turn a small part of it into a
separate method and call the new method.
How
Extract Method is actually one of the more complicated atomic refactorings. I'll describe the
typical case here. Fortunately, it is also the most commonly implemented automatic
refactoring, so you're unlikely to have to do it by hand.
1. Find a region of the method that would make sense as its own method. Bodies of loop, whole
loops, and branches of conditionals are common candidates for extraction.
2. Make sure that there are no assignments to temporary variables declared outside the scope of
the region to be extracted.
3. Copy the code from the old method to the new method. Compile it.
4. For each temporary variable or parameter of the original method used in the new method,
add a parameter to the new method.
5. Call the new method from the original method.

## What to Test?

You could write the tests so they each encouraged the addition of a single line of logic and a
handful of refactorings. You could write the tests so they each encouraged the addition of
hundreds of lines of logic and hours of refactoring. Which should you do?
Part of the answer is that you should be able to do either. The tendency of Test-Driven
Developers over time is clear, though - smaller steps. However, folks are experimenting with
driving development from application-level tests, either alone or in conjunction with the
programmer-level tests we've been writing.

What don't you have to test?
The simple answer, supplied by Phlip is, "Write tests until fear is transformed into boredom."
This is a feedback loop, however, and it requires that you find the answer yourself. Because
you came to this book for answers, not questions (in which case you're already reading the
wrong section, but enough of the self-referential literary recursion stuff), try this list. You
should test:
Conditionals
Loops
Operations
Polymorphism

How do you know if you have good tests?
The tests are a canary in a coal mine revealing by their distress the presence of evil design
vapors. Here are some attributes of tests that suggest a design in trouble.
Long setup code - If you have to spend a hundred lines creating the objects for one simple
assertion, then something is wrong. Your objects are too big and need to be split.
Setup duplication - If you can't easily find a common place for common setup code, then there
are too many objects too tightly intertwined.
Long running tests - TDD tests that run a long time won't be run often, and often haven't
been run for a while, and probably don't work. Worse than this, they suggest that testing the
bits and pieces of the application is hard. Difficulty testing bits and pieces is a design problem,
and needs to be addressed with design. (The equivalent of 9.8 m/s
2 is the ten-minute test
suite. Suites that take longer than ten minutes inevitably get trimmed, or the application
tuned up, so the suite takes ten minutes again.)
Fragile tests - Tests that break unexpectedly suggest that one part of the application is
surprisingly affecting another part. You need to design until the effect at a distance is
eliminated, either by breaking the connection or by bringing the two parts together.

## Test-Driven Development and eXtreme Programming (XP)

How does TDD relate to the practices of Extreme Programming?
Some reviewers of this book were concerned that by my writing a book exclusively about TDD,
folks will take it as an excuse to ignore the rest of the advice in Extreme Programming (XP).
For example, if you test drive, do you still need to pair? Here is a brief summary of how the
rest of XP enhances TDD, and TDD enhances the rest of XP.
Pairing - The tests you write in TDD are excellent conversation pieces when you are pairing.
The problem you avoid is that of the partners not agreeing on what problem they are solving,
even though they are trying to work on the same code. This sounds crazy, but it happens all
the time, especially when you are learning to pair with someone. Pairing enhances TDD by
giving you a fresh mind to take over when you get tired. TDD's rhythm can suck you in, and
lead you to continue to program even when you're tired. Your partner, however, is ready to
take the keyboard when you flag.
Work fresh - On a related note, XP advises you to work when you are fresh and stop when
you are tired. When you can't get that next test to work, or those two tests to work together,
it's time for a break. Uncle Bob Martin and I were working on a line break algorithm once, and
we just couldn't get it to work. We struggled in frustration for a few minutes, but it was
obvious we weren't making progress, so we stopped.
Continuous integration - The tests make an excellent resource, enabling you to integrate
more often. You get another test working and the duplication removed, and you check in. The
cycle can be 15 to 30 minutes instead of the 1 to 2 hours that I usually shoot for. This may be
part of the key to having larger teams of programmers on the same code base. As Bill Wake
says, "An n
2 problem is not a problem if n is always 1."
Simple design - By coding only what you need for the tests and removing all duplication, you
automatically get a design that is perfectly adapted to the current requirements and equally
prepared for all future stories. The mind-set that you are looking for just enough design to
have the perfect architecture for the current system also makes writing the tests easier.
Refactoring - The Remove Duplication rule is another way of saying "refactoring." But the
tests give you confidence that your larger refactorings haven't changed the behavior of the
system. The higher your confidence, the more aggressive you will be in trying large-scale
refactorings that extend the life of your system. By refactoring, you make writing the next
round of tests that much easier.
Continuous delivery - If TDD tests really do improve the MTBF of your system (a contention
you will have to verify for yourself), then you can put code into production much more often
without disrupting customers. Gareth Reeves makes the analogy to day trading. In day
trading, you close out your positions every night, because you don't take risk around that
which you aren't managing. In programming, you like all of your changes in production
because you don't want code around that you aren't receiving concrete feedback on.

## Other Advice from Kent Beck's *Test-Driven Development by Example*

### Clean Code

Clean code that works, in Ron Jeffries' pithy phrase, is the goal of Test-Driven Development
(TDD). Clean code that works is a worthwhile goal for a whole bunch of reasons.
It is a predictable way to develop. You know when you are finished, without having to worry
about a long bug trail.
It gives you a chance to learn all of the lessons that the code has to teach you. If you only
slap together the first thing you think of, then you never have time to think of a second,
better thing.
It improves the lives of the users of your software.
It lets your teammates count on you, and you on them.
It feels good to write it.

### Courage

Test-driven development is a way of managing fear during programming.

 Being careful is good, but fear
has a host of other effects.
Fear makes you tentative.
Fear makes you want to communicate less.
Fear makes you shy away from feedback.
Fear makes you grumpy.
None of these effects are helpful when programming, especially when programming something
hard. So the question becomes how we face a difficult situation and,
Instead of being tentative, begin learning concretely as quickly as possible.
Instead of clamming up, communicate more clearly.
Instead of avoiding feedback, search out helpful, concrete feedback.
(You'll have to work on grumpiness on your own.)

#### Scrum Values

![Scrum Values](img/scrum-values.png)

### Taking Breaks

The way out of this loop is to introduce an additional outside element.
At the scale of hours, keep a water bottle by your keyboard so that biology provides the
motivation for regular breaks.
At the scale of a day, commitments after regular work hours can help you to stop when you
need sleep before progress.
At the scale of a week, weekend commitments help get your conscious, energy-sucking
thoughts off work. (My wife swears I get my best ideas on Friday evening.)
At the scale of a year, mandatory vacation policies help you refresh yourself completely. The
French do this right - two contiguous weeks of vacation aren't enough. You spend the first
week decompressing, and the second week getting ready to go back to work. Therefore, three
weeks, or better four, are necessary for you to be your most effective the rest of the year.

## Summary

## Recommended Reading

## Test-Driven-Development Recommendations
Test-Driven-Development (TDD) involves writing a failing test and then writing the implementation code needed to pass the test. Some people do TDD with unit tests. They write a failing unit test, write the minimum code needed to pass the test, and then refactor their solution. This is known as red-green-refactor. Some people do TDD with acceptance tests (ATDD) where they do red-green-refactor with acceptance tests. The best way to do TDD is to use it for both acceptance tests and unit tests.<sup>a</sup> This is sometimes referred to as double loop TDD.

### Double Loop TDD
Double Loop TDD involves an outer loop where we do red-green-refactor on our acceptance tests. In order to make our acceptance test go from red to green, we do red-green-refactor on unit tests (inner loop). Here is an image from [Waldemar Mękal’s presentation on double loop TDD](https://www.youtube.com/watch?v=c9FdwL1_TBE&feature=youtu.be) that displays this process

![](http://cezary.mcwronka.com.hostingasp.pl/wp-content/uploads/2016/03/DoubleLoopTDD-1024x652.png)
Here are the steps explained at a lower level that I recommend using for implementing double loop TDD:
1. Brainstorm user stories
2. Pick a user story
3. Brainstorm given/when/thens (acceptance criteria)
4. Choose one given/when/then
5. High-level design for acceptance test (if needed)
6. Code up failing acceptance test
7. High level design for implementation code needed to pass the acceptance test
8. Brainstorm unit test cases
9. Choose one unit test
10. Write a failing unit test
11. Write the minimum amount of code to make the test pass
12. Refactor
13. Repeat Step 9 until all unit tests are done
14. Repeat Step 8 until the acceptance test is passing
15. Refactor
16. Repeat Step 4 until all given/when/thens have been tested (if needed)
17. Repeat Step 3 until the user story is completed

## Sources
a. Freeman, Steve. Growing Object-Oriented Software, Guided by Tests. Addison-Wesley, 2012.
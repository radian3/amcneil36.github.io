## When is it appropriate to refactor previously existing code?
Suppose you have a codebase that you feel takes a long time to do code changes in due to portions of the codebase being coded or designed poorly. It would make sense to have some refactoring done on the codebase in order to make the code easier to work with. But when should we do this refactoring? One option is to schedule time in advance for refactoring. We could create refactoring tasks where the only objective is to refactor the codebase. There would be no new functionality for this task. The only purpose of these tasks would be to make future code changes easier and faster. Unfortunately, it turns out we shouldn't create refactoring tasks where the only purpose of the task is to refactor.<sup>1</sup> There are a few reasons for this:
1. Tasks for refactoring do not add any immediate business value as they do not change the external behavior of the system  
2. Refactoring tasks only add value if a future task goes on to benefit from it. This makes refactoring tasks more along the lines of 'coding for the future.'  We could run into a scenario where we refactor something that we think will help us in the future but then never end up needing that refactoring in the future  

Let's jump into the correct time to do refactoring.

### Only refactor previously existing code if it will help you with your current task
You should only refactor code if it will help you with the current task you are doing.<sup>1</sup> Let's talk about some examples of this.

#### Refactor to help you understand code that is needed to be understood for your task
Suppose you need to make a code change in a file. Let's say that you need to look at and understand a few other files before you can make this code change. If these other files are confusing you, it is a good idea to refactor them in order to help you understand the code better.<sup>1</sup> This would generally involve renaming variables and methods or extracting blocks of code out into their own method with a descriptive name. Or, if your own file that you need to make a code change in is confusing you, it is a good idea to refactor there as well.<sup>1</sup> So any time that something is confusing you that you need to understand in order to do your task, it is a good idea to refactor it to help you understand it. I am not talking about doing this as a temporary refactoring that gets undone after you understand the code. You should do this as a permanent refactoring that gets merged to trunk with the rest of your work.

#### Refactor the design to make it more modular or more re-usable so that code for your current task can call into it
Sometimes you will be in a scenario where some code out there almost does what you need but not quite. If this code were instead designed slightly different, you could call into it for your current task and it would save a lot of work. This is a scenario where you would want to look into refactoring the code to make it more modular or more re-usable so that you can call into it for your current task.<sup>1</sup>

### Do not refactor any code that has no unit tests
One of the downsides of refactoring is that we could potentially break something. If there are no unit tests in the code we are refactoring, then it is hard to tell if our refactoring broke anything. Therefore, we should not refactor any code that has no unit tests.<sup>1</sup> If we are interested in refactoring code that has no unit tests, we should add the unit tests first and then do the refactoring after. If we aren't interested in adding unit tests then we will not be refactoring.

### Summary
Instead of scheduling time in advance for refactoring tasks, we should do refactoring as part of our tasks. Furthermore, we should only do a refactoring if it will help the task we are working on. We should not be doing a task and then simultaneously do random refactorings that do nothing to help our task. Only refactoring when it will help our task gets us more in the mindset of coding for now where we are doing something that is immediately benefiting us. Doing refactoring-only tasks results in us programming for the future which is risky because things can change in the future, causing our refactoring to never go on to benefit us. When implementing refactoring properly, we should have frequent small bursts of refactoring as we work on our feature.<sup>1</sup> Each check-in leaves the codebase slightly cleaner than it was before.<sup>2</sup> Lastly, any code that we are considering refactoring should be unit tested before we do the refactoring so that we have more confidence that our refactoring doesn't break the code.

## Sources
1. Fowler, Martin and Beck, Kent. Refactoring: Improving the Design of Existing Code. Addison-Wesley, 1999.  
2. Mancuso, Sandro. The Software Craftsman: Professionalism, Pragmatism, Pride. Pearson Education, 2015.

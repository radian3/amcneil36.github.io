## Local and Ci-Server Build Recommendations
### The build must be able to be started from the command line
We want our build to be able to be started from the command line.<sup>a</sup> This will help make the build able to be ran from any developer's machine as well as on a ci-server.

### Commit build recommendations
#### 10-minute build
We want our build that is ran on commit to be able to be ran in 10 or fewer minutes.<sup>a,b</sup> Having a build that takes longer than this makes it take a while to fix errors in the build since there has to be such a long wait to make sure that the build completes. People will also be less inclined to merge to trunk as frequently if the build has a long wait time. 

#### Static analyzers to run
* code formatters
  * allows people to develop on whichever IDE they want
* code coverage tool
  * pick a threshold to ensure that the unit tests achieve
* check for good/bad programming practices
* security vulnerability checks

#### Unit tests
All unit tests should run on the commit build. Any unit test under 1/10 of a second is a slow test.<sup>c</sup> Therefore we should have no issue with unit tests taking the build a much longer time to finish.

#### Acceptance tests
We would ideally run all acceptance tests on the commit build. However, we did say that we want a 10-minute build and in some cases, running all of the acceptance tests would take longer than 10 minutes. If our acceptance tests are causing our build to take longer than 10 minutes, then we should look into doing the following:
* run the acceptance tests in parallel<sup>a</sup>
* share expensive resources between tests<sup>a</sup>
  * if there are resources that take a long time to make, we could look at having this resource made once and sharing this instance between tests<sup>a</sup>
* adhere to the test automation pyramid when determining how much of each test type to make<sup>d</sup>
  * the most common type of automated test should be a unit test followed by the back-end functional tests followed by GUI tests
* delete any redundant acceptance tests that don't add much value over already existing acceptance tests

If the acceptance tests are still causing the build to take longer than 10 minutes after doing this, then we want to take the least important acceptance tests and have them run post-commit.<sup>a</sup> The most important acceptance test and the ones that are most likely to fail should be the ones ran on commit in this case. All acceptance tests would still need to pass before releasing though.

### Place all tests in the same repository as the code they test
Sometimes people will try to place acceptance tests in a different repository than the code they test. This makes it harder to set up a build that runs all the necessary tests. It also prevents people from having a repository out of date with the repository that tests it. Having tests in the same repository as the code they test will make the build easier to set up and will make it less likely that people merge with tests that are failing elsewhere.

### Ability to choose the environment to deploy to on the command line
We should be able to deploy to any environment we want by just running one command on the command line.<sup>a</sup> This could be as simple as just passing in the environment name as a parameter to the command that is ran on the command line.

### Containerization
Our build should be able to create a new environment, run all of the tests, and then destroy the environment.<sup>e</sup> This is best done with containerization.<sup>e</sup>

### Smoke test deployments
When deploying to any environment, we should have smoke tests that run to make sure that the environment is configured properly.<sup>a</sup> If any external service we depend on is not working or not configured properly, the test should fail.

### Nightly build
Nightly builds are builds that run once per day, usually around 3 am when no one is awake. These are most commonly done with tests that might use expensive resources or take a long time. The downside of nightly builds is that if something goes wrong, you don't find out until the next day. It would be convenient if everything ran on commit so that you know sooner if something went wrong. However, some things are too expensive and just can't be ran on commit.

Tests like load tests, stress tests, and longevity tests are all good candidates to have ran nightly on a ci-server.<sup>a</sup> These tests would also ideally be ran in parallel.

### Use the application's API to put the environment in the correct state for tests
What some people will do to put the environment in the correct state needed for their test is to write their own code to set up the environment. The problem with this is that when the environment changes, we would have to update our test code to set up the environment properly for the new changes. We should use the application's API to set up the state for our tests so that when changes to the environment are made, our tests will automatically set up the environment the new way.<sup>a</sup> This will ensure that we are testing our application against the correct environment.

### Favor push hooks over polling
Some people will set up their ci-server to poll their repository every so often for changes. This is not only expensive but it also causes the ci-server to not necessarily build the project right away after receiving a commit. We should instead use a push hook to where the ci-server is notified by our version control system as soon as we push. This will make our project built as soon as a commit is pushed and will use up much less resources.

### Pre-tested commit vs post-tested commit on ci-server
When developing on a branch, I like having the ci-server build my branch post commit. This means that my commit is made to my remote branch and then the ci-server builds. This does allow for my build to go red but I don't find that as big of a deal on a development branch in comparison to trunk. I sometimes just want to be able to save my work remotely or be able to show a teammate my work remotely and I don't want that attempt at committing to be rejected on my remote development branch due to a red build.

When it comes to merging code into trunk, however, I prefer the ci-server to build pre-commit. What I mean by this is that the ci-server will locally merge your development branch into trunk and build that. If the build succeeds, the ci-server will notify you that it succeeded. The ci-server could either automatically commit this merge to trunk upon a successful build or have you press a button or type a command to indicate that you want to complete the merge. This helps keep the trunk build passing.

### Set up a timebox for fixing broken builds before reverting
If a check-in breaks the build, everyone needs to stop what they are doing and try to fix the build. If no one can fix the build within ten minutes, revert the commit that broke the build.<sup>a</sup> This helps keep the build passing and prevents people from getting blocked on merging.

## Sources
a. Humble, Jez and Farley, David. Continuous Delivery: Reliable Software Releases Through Build, Test And Deployment Automation. Addison-Wesley, 2010.  
b. Beck, Kent and Andres, Cynthia. Extreme Programming Explained. Addison-Wesley, 2004.  
c. Feathers, Michael. Working Effectively with Legacy Code. Pearson Education, 2005.  
d. Wolff, Eberhard. A Practical Guide to Continuous Delivery. Addison-Wesley, 2017.  
e. Cohn, Mike. Succeeding With Agile: Software Development Using Scrum. Addison-Wesley, 2013.
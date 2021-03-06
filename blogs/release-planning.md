## Release Planning

Releasing is the only thing that adds value to the customer so it makes sense to have some planning done on the release level. This is known as release planning. Release planning for a new project generally involves planning 3-6 months of work. When planning a release, there are tradeoffs that need to be considered such as scope, date, and cost. It can almost always be expected that some things won't go according to plan so we need to have some sort of flexibility in our release plan to account for this. If we try to fix scope and date, we generally don't have enough room to make adjustments for when we get behind schedule. Adding humans late in a project makes the project later so having a flexible cost for the project doesn't do as much help as one might think. So in order to have enough flexibility for when something goes wrong, we need scope or date flexible. This leads us to the two most common ways to release plan which is to plan a fixed scope release or a fixed date release.

### Fixed Scope Release
In the fixed scope release, we end up with a release plan that includes the functionality we want to include in the next release. There will likely be a date range where all of this functionality is predicted to be finished by but the actual date of the release will just be whenever everything is done. If the work takes longer than predicted, we end up just releasing at a later date.

### Fixed Date Release
In the fixed date release, we end up with a release plan that has a date for when we want to release. There will be some functionality included on the release plan but it would be negotiable. We can add or reduce scope as needed. Unlike the fixed scope release, the fixed date release will sometimes fix cost. If we have a release date, we can fix cost by simply not allocating more resources than originally planned.

### Should we do a fixed scope release or a fixed date release?
For defect fixes and minor enhancements, I like the idea of a fixed scope release where you just release whenever the code changes are done. For larger changes, especially for a project's initial release, the fixed date release is generally better.<sup>1</sup> Fixing scope means you are indicating that you upfront know what the customer wants. What if the customer changes their mind? What if the market changes? We need to be able to have some flexibility to account for these things when working on a major release. However, for defect fixes and minor enhancements, customers changing their mind or changes in market are not as big of a deal since these code changes are so small and fast. We can release on each defect fix and can release on each minor enhancement completed as long as our release process is automated (which it should be anyway).

Customers also like the idea of receiving dates for major releases because major releases might be something that they need to make plans around. Perhaps your team is interested in starting a new Java project but the next major Java version is going to be released soon so you are thinking of waiting for that to come out before starting the project. Since Java communicates the dates they plan to release their major versions, you can use this information to help determine if you want to start now with the current Java version or wait until the next Java version. However, knowing when the next minor Java version is going to come out probably won't be information you need to know in order to prioritize when to start on this new Java project.

### Planning a Fixed Scope Release
Planning a fixed scope release can be done by:
1. Identify your MVP or MMF depending on business needs
1. Add up the number of story points of work 
1. Use team's past velocity to provide a range of dates that the release is predicted to be done by
    * this is commonly done by taking the team's lowest velocity in the past few sprints for the lower bound estimate and the team's highest velocity in the past few sprints as the upper bound

If the fixed scope release is being used for a minor enhancement or defect fix, you don't need to go through all this work. You can simply just do the task or story and then release it when it is done.

### Planning a Fixed Date Release
Planning a fixed date release can be done by:
1. Identify your MVP or MMF depending on business needs
1. Add up the number of story points of work 
1. Add another 25-40% story points of work depending on risk, uncertainty, and consequences of not meeting the deadline
1. Add this to the amount of story points of work
1. Use team's past velocity to calculate a release date based on the amount of story points of work

The concern that arises the most with fixed date releases is the deadline. What do we do if we are behind schedule when we get to the deadline? We should be able to reduce scope. The 25-40% additional story points of work should be nice to have work that is not mandatory. Our definition of the MVP or MMF may even become reduced throughout the project as well. The scope in the fixed date release is very flexible. When behind schedule, we should be able to reduce scope and still release since we have done the most important work first.

### Whole development team works on the same release
We should have the whole development team work on the release the same release which is the release that we have planned. Having a development team work on two releases at once produces additional waste because it adds more work that is not released at any given time. Since work only adds value when it is released, we want to swarm the same release in order to release earlier. There are some exceptions to this. If there is an incoming defect found in production, then it is OK for a team member to switch to working on that defect, release it, and then come back to the release that everyone else is working on. This is because the incoming defect might be more important. If a development team is too large, then it might appear to make sense to work on multiple releases at the same time. However, a development team that is too large can be split into two development teams that are working on different releases. Or, if the product they are working on is a big one, there could be one or more development teams working on different features for the same release.

### MVP vs MMF
We talked earlier about doing the MVP or MMF depending on business needs. The MVP (Minimum Viable Product) represents the minimum amount of work that must be done to take something to market and learn something. The MMF (Minimum Marketable Features) is the minimum amount of work needed to be done in order to add significant value to the customer. The MVP makes more sense for products with less certainty such as being very uncertain about how popular the product might be or how the product will respond to being used by customers. The MMF makes more sense in all other scenarios.

### Flexibility of the release plan
The release plan is very flexible.<sup>2</sup> Some teams will take a look at the release plan every sprint during the backlog refinement meeting and make changes as needed. We can make adjustments to the release plan for many reasons such as changes in the market, customers changing their mind, work taking longer than predicted, work being completed in a different way than predicted, etc.

### Assumptions about who will do the work
Do not make any assumptions about who will do which work when planning a release.<sup>3</sup> It is very hard to know far in advance who will do what since many tasks could take longer or shorter than predicted which could affect who we would want to work on them. Perhaps there is a very important set of tasks that is taking one person longer than predicted so we have someone else help out there.

### Summary
I like the fixed scope releases for minor enhancements and defect fixes since they are quick and small fixes. There is not much room to reduce scope in such small releases and it is unlikely for there to be many changes in priorities in such a small time period. For major releases, I prefer the fixed date release as they allow for us to change scope when market changes and when there is customer feedback. Knowing release dates for major releases can be helpful to customers because they might be interested in making plans around a particular release date for a major release.

## Sources
1. Rubin, Kenneth. Essential Scrum: A Practical Guide To The Most Popular Agile Process. Addison-Wesley, 2013.  
2. Beck, Kent and Fowler, Martin. Planning Extreme Programming. Addison-Wesley, 2004.  
3. Cohn, Mike. Agile Estimation and Planning. Pearson Education, 2006.

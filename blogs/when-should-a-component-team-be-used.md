## When should a component team be used?
We previously talked about [why we should favor using feature teams over component teams](https://amcneil36.github.io/blogs/feature-teams-vs-component-teams-which-one-is-better). However, we didn't establish that component teams should be completely avoided. We just established that we should use feature teams for most scenarios. So when should component teams be used? Let's look at an example.

Suppose your team needs code changes made in some component that it has never used before. There are two different setups we could have:
1. feature team setup where our team will make code changes in the component
2. component team setup where a component team will make code changes in the component

In the feature team setup, there is an overhead of having to learn about the component before making code changes to it. This is why the changes in the component would most likely take more man hours in the feature team setup. However, the component team setup often results in queues before the request can be serviced which generally leads to more elapsed time from the time of the request to the time of the request being completed. 

For a component that is easy to work with and learn, it might take, for example, 1.3 times more man hours to make a code change in a component with a feature team setup than with a component team setup. We would generally be fine with spending 1.3 times more man hours since it prevents the additional overhead of cross-team dependencies and work sitting in queue. So for components that are easy to work with, it makes more sense to have a feature team setup instead of a component team setup. What about for difficult to work with components?

When components are difficult to work with, the initial overhead of having to learn about a component before making code changes in it starts to become too great for it to be worth it to use the feature team setup. For components that are difficult to work with, it could easily take 20 times more man hours to make a code change in a component with a feature team setup than with a component team setup. When code changes take significantly more man hours in a feature team setup than a component team setup, we would generally be fine having a component team do the work, even if it results in the work having to sit in queue for a little.

So it could be said that **the more difficult it is to work with a component, the more sense it makes to form a component team around that component. The less difficult it is to work with a component, the less sense it makes to form a component team around that component.** Let's get into some examples of components that would be difficult to work with.

### Examples of components that would be difficult to work with
#### Low Level Code in components
Components with a lot of low-level code would generally be scenarios in which it would take a lot of extra time to study the component prior to making the code change. This is because the low-level code requires more code in order to do less work.

#### Security
Components that deal with security would be components that would be hard for any developer in an organization to jump in and work with. This is because a developer would need to spend a lot of time learning about security before being able to make these code changes.

#### Weird/Uncommon technologies
When teams within an organization use similar technologies for their components, it is easier for any team to make a code change in any component. If a component uses a different technology, especially if this technology is not well documented or known, this would add a bit of an overhead to other teams needing to make code changes in the component.

#### Legacy Code
Legacy code generally has a large overhead of learning and is very fragile to changes. We should try to keep our code modernized to where a component team is not needed but if that is not feasible, then a component team is something to look into.

#### Overly complicated data model
We should try to make our data model as simple as possible to where we don't need to make a component team that works with the data model. But if we cannot keep our data model simple, then there will be a bit of an overhead for other teams needing to make code changes to the component. So this is a scenario in which a component team may make sense as a last resort.

### Does the re-usability and number of consumers of a component affect whether or not we should have a component team?
It is commonly believed that the more re-usable and widely used a component is predicted to be, the more it makes sense to form a component team around that component. I would agree that these factors increase the likelihood that a component team makes sense. But I don't think that these factors play as big of a role as most people might think. The difficulty of making code changes in a component would play a much more significant role than these factors in determining whether a component team makes sense. Even if a lot of teams need code changes made in a component, they probably wouldn't want the overhead of cross team dependencies and work sitting in queue if they could make the code changes themselves in just a few additional man hours than what it would take with a component team setup.

### Summary
Component teams tend to make more sense for components that are more difficult to make code changes in. This primarily pertains to components that require a lot of pre-requisite knowledge prior to working in them. When possible, we should try to set up components such that it is very easy for anyone to make code changes in them and thus not need a component team for them. However, sometimes this just isn't feasible or possible so a component team is justified. Component teams should not be the most common way to organize and should be thought of more as a last resort.

## Additional Resources
* [SAFe Features and Components](https://www.scaledagileframework.com/features-and-components/)
* [SAFe Shared Services](https://www.scaledagileframework.com/shared-services/)

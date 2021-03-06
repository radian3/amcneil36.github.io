## Horizontal vs Vertical Slicing

In order to complete a feature for a customer, code changes must be made in one or more components. Most of the time, this will involve more than one component. The term 'component' just refers to a re-usable asset that is used to complete a portion of a feature. The front-end and back-end are both considered components. Within the back-end there could be multiple components such as a data retrieval component, a data insertion component, and more. So the term 'component' could be used at different levels of granularity.

When planning out a project, there are two different approaches that teams might take to plan out the order for the work to be done. One approach is **horizontal slicing** where a team will attempt to complete all work in one component before moving on to another component. This might involve trying to do the whole back-end before starting the front-end. It might involve trying to do the whole front-end before starting the back-end. Or, it might involve completing one component in the back-end and then completing one component in the front-end followed by returning to the back-end. The second approach is **vertical slicing** where a team will code up a portion of multiple components at a time in order to produce a small amount of end to end functionality.

Suppose you are working on a feature that needs front-end and back-end code changes. Perhaps the front-end and back-end both have multiple components for this feature. Maybe they don't. Doesn't matter for this upcoming question. Should we do horizontal slicing or vertical slicing? Let's look at one at a time to see how it would look.

### Horizontal Slicing
As stated previously, horizontal slicing involves completing all code in one component before moving on to another component. We will start off by discussing a simple example.

#### Coding all of the back-end followed by coding all of the front-end
In this scenario, we will start off by coding up all of the back-end for the next release. When it comes to demoing we won't get much feedback because there is no front-end. You will be half way through the project with no working software to show in the demo. Stakeholders will become concerned that the project is not on target. Once the front-end starts coming along, you will finally start getting feedback at the demos since there will be usable functionality that the customer can see in a demo. However, we don't want to wait until half way through the project to start getting feedback at the demo. The later you get feedback, the more code that gets tossed in the event that you adjust the code to the feedback. It is also more difficult to make changes later in plans since the release date is closer.

Another issue with doing all of the back-end before all of the front-end is that the layers may not communicate together when you finally get around to integrating them. As you code up the back-end, you will need to make some assumptions about which information the front-end will be able to pass to the back-end. If these assumptions turn out to be wrong, you won't find out until very late in the project when you are finally integrating the layers. This creates for more code getting tossed when there are integration issues.

#### Coding all of the front-end before all of the back-end
In this scenario, we will start off by coding up all of the front-end for the next release. When we demo our code, we should be able to get a lot of feedback in terms of how everything is coming along. One downside is that more project will appear more complete than it actually is done since the call to the back-end will be stubbed out. This could confuse the customer. However, this downside is manageable. After the front-end is done, we would then go on to do all of the back-end. We might not get much feedback in the last half of the project since that portion is just back-end but it's better to be getting your feedback early than late. So in terms of getting feedback in a demo, this approach is not so bad. One thing to keep in mind is that the front-end calls into the back-end but the back-end doesn't call into the front-end. So unlike the previous scenario, this time we might have to make some minor front-end changes as the back-end is getting coded up so that the front-end is getting updated to call into the back-end.

Unfortunately, this approach suffers the same issue as the previous approach in that the layers are not being frequently integrated together. As we code up the front-end, there are some assumptions that we have to make about how the back-end will look. When we integrate this code later, we may find these assumptions were wrong. Perhaps there are some unforeseen performance issues when we finally integrate everything. Perhaps we have to make significant changes to both the front-end and back-end to account for these performance issues. The later we integrate, the more code that gets tossed.

### Vertical Slicing
In this scenario, your team would make code changes in a little bit of each component each sprint. The team would produce a small amount of fully integrated usable software each sprint. This is because most working software requires code changes in multiple components. The team would be able to get feedback from customers every sprint since working software is delivered frequently. If there are any issues discovered when integrating components, these issues will be discovered early since we are frequently integrating. If the project becomes behind schedule, the we still might be able to release despite not having finished all of the work that we previously intended to include in our release. This is because we made sure to create usable software each sprint with code that was fully integrated and truly considered done.

### Should we do horizontal slicing or vertical slicing?
We should do vertical slicing. Horizontal slicing suffers tremendous risk in that components aren't integrated until very late and this integration could lead to unforeseen issues that may cause code to have to get thrown away. In addition to that, horizontal slicing doesn't result in usable software until far later in the project. It might look like you get usable software early in horizontal slicing if you do all of the front-end before all of the back-end. While it is true that you can click on stuff, the software isn't truly useable because it is stubbing out the back-end.

Vertical slicing fixes all of the issues seen by horizontal slicing without having much of any drawbacks. Vertical slicing results in frequently integrating layers which leads to less integration issues and less time spent doing re-work. It results in more frequent feedback and more frequent usable software that could be shipped out.

### Recommendations for vertical slicing
#### Use user stories expressed in terms of business value
The easiest way to start thinking in terms of vertical slices is to make user stories and to express them in terms of business value. Let's look at the following user story:
>As a homeowner, I want to be able to register my house to the homeowner’s association so that my house can be placed on the market.

This user story is expressed in terms of business value. This is something that would likely require front-end and back-end code changes and would result in producing usable software. Teams that do horizontal slicing tend to have stories expressed along technical boundaries, for example:
>Create SQL query for inserting into the House table

This story expressed along technical boundaries provides no business value when completed because the SQL query has to be fully integrated with the rest of the software in order to provide business value. This would require writing some code that calls into the SQL query.

#### Tracer Bullet Development
With tracer bullet development you start out by getting some working end to end functionality as soon as possible where most of the stuff happening in-between is stubbed out.<sup>1</sup> You then slowly replace stubs with real calls until you no longer have stubs and now have fully usable software. Suppose you are starting a project where you want the following functionality:
1. The user fills in some input  
1. The user presses a submit button
1. A report is generated and is somehow affected by the input that the user selected 

Furthermore, suppose that behind the scenes there is tons of business logic with reads and writes to the database after the user presses the submit button. With tracer bullet development, we might work like this:
1. Make button and have clicking on that button display a report that says “hello world”  
1. Add an input field and have clicking on the button generate a report that uses some information from the input field
1. Repeat step 2 with a different input field. Keep doing this until all input fields are done
1. Add any additional text to the report that is not determined from input

When completing the first step, we have some working end to end functionality where the calls to the database are stubbed out. For the second step, we add a new input field and then add any code that interacts with the database that is needed so that the report we generate can be updated to have whichever information needed that is dependent on the answer to that question. As you can see, each step requires a little bit of code in each layer and produces a little bit more fully integrated functionality. This is what we want.

### Summary
We want to be working on vertical slices so that we increase the amount of feedback we get from demos as well as reduce the number of integration issues. One of the easiest ways to get into this is to start making user stories that are expressed in terms of business value. Code changes in each layer are generally required to add value to the customer. As we carry out these user stories, we want to be using tracer bullet development to quickly get working end to end functionality.

## Sources
1. Freeman, Steve. Growing Object-Oriented Software, Guided by Tests. Addison-Wesley, 2012.

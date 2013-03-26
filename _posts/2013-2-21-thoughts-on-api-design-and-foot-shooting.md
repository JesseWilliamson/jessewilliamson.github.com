---
layout: post
title: Thoughts On API Design and Foot Shooting
synopsis: my thoughts on API design and usability
---      
# Thoughts On API Design and Foot Shooting

This isn't anything new. I'm sure it's be spoken to by people much smarter and well-respected than I, but it's eating away at my brain, so here we are.

I was on a phone call this morning with some other developers on my team, and the topic of a troublesome release came up. Now, I was involved in the development of features for said release. I made mistakes. I own outright. I want to make that very clear; this is not an attempt to skirt any blame I am deserving of. More than anything, this is a way to get this frustration off of my chest, because doing so in any other forum would create far too much conflict, and would ultimately have no effect on the day-to-day activities of the team.

As we discussed the failure of our last release, _Senior_ chimed in with:

>The reason our last release failed was because we didn't have enough time for proper mentoring and code review with new developers.

Read "new developers" as "Jesse." I was the only new dev on the project and at least one of the issues could be directly sourced to code I wrote.

Now, _Senior's_ statement isn't incorrect, there was very little time for mentoring, and zero code review. It's an accurate statement, but it's short-sighted. You see, the only way a code review would have helped discover this error is if _Senior_ performed it himself.

Why?

Simple. _Senior_ wrote the API I was coding against. He wrote the objects I was using to send requests to the service, and _Senior_ has a particular style of coding that makes the object as unintuitive possible. Here is a simple example:

We have feature in our app that use, what are essentially, Query Objects. Correction, Query Object. There are 10-15 different types of queries we provide, they all use the same Type. The class is the poster-child for ISP violation. Some members are used for query A, others for query B, and so on and so on. It's a case of making things as generic (no not &lt;T&gt;) as possible, in order to prevent object explosion, while simultaneously shooting yourself in the foot.

Well, except for _Senior_.

_Senior_ knows how to use it, he knows what to put where for each query, so he wouldn't shoot himself in the foot. You? You shoot yourself in the foot. Then _Senior_ comes around with a Medical Kit to patch you up. And now you won't shoot yourself again; well, not with that bullet at least. What you don't know is that while you were getting stitched up, your gun was being reloaded. And the hammer is cocked.

Dont' get me wrong. Peer review and mentoring are crucial; we _did_ need more time for that. What I am saying is that your code shouldn't make it easy for me to blow a hole in my foot. If I am forced to use your API, your classes, you should have the courtesy to provide abstractions that make sense. Use good names. Write classes that provide some insight into how they should be used. PROVIDE APPROPRIATE CONSTRUCTORS! That's a pet peeve of mine. Don't give me a bag of getters and setters and then throw exceptions because I didn't set things properly. If you do that, I hate you.

In the our example, how hard would it have been to have fine-grained query objects that know exactly as much as they need to know in order to get the job done? How hard to give them names that make sense?

Not hard.

You might say it's more time upfront, more lines of code, more classes. You'd be right, and you'd go on being right, until somebody, *cough* me *cough*, uses your API and thinks they got it right, but didn't. So yeah, you saved a few precious lines of code. You prevented creating a interface or inheritance chain. You saved some time upfront. And I came along and I caused you a megaton of rework, and all the joy that comes along with it.

So many things went wrong with this ill-fated release. No unit-tests , poor user testing, insufficient time for mentoring, devs being pulled in all directions, API signature changes (WTF?!). Hard to use code is such a small part, but it's importance is dispropotionate to it's size. Yes, a unit test could have caught it (have fun introducing a test suite into a legacy winforms app that never had one before). Yes, a diligent UAT tester should have caught it. Yes, a code review would have caught it (well, assuming _Senior_ led it). Does that mean you should write your code without consideration for those who come after you, and those consume it?
	
Obviously, there is no API in the world that will magically allow the consumer to know exactly how to use it. Nobody is going to create a library so well written that you don't have to write tests, or review with a peer. That's not what I'm saying. What I am saying it is your responsibility, as the author, to write your API in an intuitive way. Yes it will take more time. Yes you will have more classes. And? The extra upfront cost is a one time investment. Your code will live on long after you're done writing it. Presumably, for quite some time to come. New developers will come and go. People will have to learn to use your code, and that will continue. The time you spend upfront has a direct impact on the time it takes to complete future projects.

Design your API with an audience in mind. Someone will have to read it. Someone will have to use it. Why wouldn't you want them to use it correctly, with as few barriers as possible?
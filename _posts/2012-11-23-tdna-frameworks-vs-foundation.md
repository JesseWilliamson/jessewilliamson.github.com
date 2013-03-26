---
layout: post
title: Things New Devs Ask: What Should We Learn? Frameworks vs Foundations
synopsis: whether frameworks or fundamentals are more important for new devs to learn.
---      
# Things New Devs Ask: What Should We Learn: Frameworks vs Foundations
  
> Wherein I swallow my pride and ask total n00b questions and expect you to answer them.
## A Little Background

I'm a self-taught developer. I didn't got to college, save a couple of intro to HTML/CSS classes. As I imagine a lot of self-taught devs did, I began by picking a language and discovering the wonders of programming from there. As a result, I had very little basic foundational knowledge in Object Oriented Design, or Computer Science in general. The thing that makes self-teaching easy is that books, and tutorials tend to deal with a fixed point of view: here's how you do X with Framework Y. Of course, if you're curious enough, and I think I am, you eventually begin to look outside of the box you've chosen and go a little deeper. Hanselman, actually has a [great post](http://www.hanselman.com/blog/PleaseLearnToThinkAboutAbstractions.aspx) about just this...more or less.

But I've come to notice some things in my recent dealings with other, much more senior, developers. One thing I've noticed is that, while very skilled and knowledgeable in a given framework, the basic fundamentals of design are lacking. Or, if not truly lacking, they have, at the very least, taken a back seat to the framework knowledge.

## The Question
### _What should new devs learn: Frameworks or Foundations_

That sounds like a question that answers itself. We all know the story of the fool who built is house on sand, so we all "know" that having a solid foundation is important. But can't strong knowledge of a framework be a foundation? Particularly when you organization is "in bed" with a given technology provider; so much so that the organization makes strategic decisions based on said provider's offerings? I mean, if a framework puts requirements on you to write bad code, but you have no choice but to use Framework Y, what good is it to know any other way to do it?

## My Answer

When I started writing these question I didn't want to offer my answers. That whole idea seemed flawed because I wouldn't be asking them if I had my own opinion formulated, but I'm will to make exceptions; particularly when my experiences bring my opinions into question. Which is the case here.

### _My answer is to learn the foundations._

When I first started, I just wanted to learn C# and MVC, but as I started digging more I started learning more about design, patterns, SOLID, and all that. That all seemed very important to me. It dawned on me that it didn't matter what language or framework I used as long as I understood how to write good software. Frameworks have short shelf-lives, but foundations tend to outlive the frameworks built atop them. But the interesting thing about that is many of them become zombies. I'm working on a WinForms app for God's sake. WinForms!

[Jason Gorman](http://codemanship.co.uk/parlezuml/blog/?postid=1153) had a post recently that made a very good point, most devs are working in legacy systems. Companies, especially large ones (the type that tend to hire .Net devs), are slow to change; it's scary and expensive. So, while Framework Y is [old and busted](http://www.youtube.com/watch?feature=player_detailpage&amp;v=ha-uagjJQ9k#t=13s), a dev that concentrates on just knowing how to work in that framework can get and keep a job for quite some time. So, there is an argument for learning how to code for Framework Y and never learn the foundations. Framework Y may go out of style, but I can guarantee you there are a bunch of [dark matter devs](http://www.hanselman.com/blog/DarkMatterDevelopersTheUnseen99.aspx) still working on it and getting things done.

So you can see why I would question my own opinion. I still think foundations are more important, but when you see people getting things done doing it the wrong way, because that's how you do it in Framework Y, does it really matter? For now I say yes, and I hope I continue to, because I think that going the other way means I've been bested.

## Oh, Just One Last Thing

And finally, I leave you with a conversation based on a true story.

Allow me to set the stage. Senior and N00b are discussing a bit of code. The code introduces a new class into the system, let's say it's called DiscountPartner. In this system a DiscountPartner can't exist without a Name, a PartnerCode and a DiscountRate (I believe fancy people call these "invariants"). N00b wrote the class with a single constructor that takes three arguments, guess what they are.

Senior: "You probably want to go ahead and just use the default constructor, and make all of those properties public."

N00b: "But, can a DiscountPartner exist without those things?"

Senior: "Sure, that's what the default constructor does."

N00b: "Well, yeah, but does it make sense for a DiscountParnter to exist without a Name, Code or Rate?"

Senior: "That doesn't really matter because you can just use the curly brace syntax to set those" (He meant object intializers in C#)

N00b: "Um...ok, but..."

Senior: "Plus you have to do it that way for it to work with Framework Y".

And scene.

Now, I see a problem(s) here, but not everybody does. In my opinion, Senior is making design decisions based on 1) Language features, 2) Framework constraints. Object intializers are great, but they're not going to stop you from shooting yourself in the foot. Granted, proper constructors don't either, but they certainly put the safety on. Framework constraints are what they are. If you've made the decision to use Framework Y, then you've got decisions you're going to have to live with. Personally, I like the Uncle Bob approach: Frameworks are plug-ins. Your system shouldn't know about them and it most certainly should not be constrained by them Take ASP.NET MVC for example. Default model binding requires default constructors with publically accessible properties. Fine, that's why we use view models (one reason at least, [there are others](http://odetocode.com/blogs/scott/archive/2012/03/11/complete-guide-to-mass-assignment-in-asp-net-mvc.aspx)); I'm not going to compromise my domain model because the framework has limitations.

So what are your thoughts? Is all of this foundational stuff high-falootin', ivory tower non-sense? At the end of the day is it just about getting it done, or is there something deeper that we should strive to understand?
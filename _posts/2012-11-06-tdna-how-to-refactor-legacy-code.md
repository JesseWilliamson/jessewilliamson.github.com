---
layout: post
post-title: Things New Devs Ask - How To Refactor Legacy Code
synopsis: how to approach refactoring legacy code
---      
        
# Things New Devs Ask: How To Refactor Legacy Code         
>Wherein I swallow my pride and ask total n00b questions and expect you to answer them.

## A Little Background

 I work remotely. Kind of. My company has offices all around the country, but IT is based out of our main office on the east coast. As such, any IT associate not located there is considered remote (actually, that's only part true but I won't get into it). For the most part, our organization has a policy against remote developers, for whatever reason. In order to move into a dev position, I had to take what I could get, which meant working on legacy code. Now, when I say "legacy code" I want you to envision all the horrible things you've ever heard of, or seen: static everything, "unit" tests that have 40+ assertions, tests that only run if the DB is running and only if you're pointed to the right server, code that is "object-oriented" only because the language is, hacks on hacks on hacks, all that. It literally gives me a headache to read. It's totally foreign to me. I'm not saying I write amazing code, but what I'm used to seeing, what I'm used to writing, is nothing like this. Devs with more experience have seen this situation before, I'm sure of it.

## The Question

### _How do you begin to refactor legacy code?_

I'd like to think that I know a little about well written code. Code that is easy to read, expressive, code that can be tested easily, that makes it's dependencies known, code that is (dare I say) "SOLID"...at least I think I do. The problem is that what I know I learned from starting with a blank page, or even code that was striving toward the same goals as I was. What do you do when all you've got is a tightly coupled, tangled mess? How do you begin to refactor if the only thing you know for sure is that you're going to break everything. What's more, how to do you get buy-in from your team and management when it seems clear that they have very little interest in developing that way? To make matters worse, how do you do that when you're the new guy in his first development role?
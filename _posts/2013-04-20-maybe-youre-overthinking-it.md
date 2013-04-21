---
layout: post
post-title: Maybe You're Overthinking It
synopsis: a quick KnockoutJS refactor I did, and wanted to share.
---

# Maybe You're Overthinking It

My current project is a fairly large single page application written in [KnockoutJS]("http://knockoutjs.com"). I won't get into all of that too much, and my opinions on a straight, vanilla Knockout solution for a large project will be saved for another post. What I need to explain is this: our current task is, essentially, to retrofit the UI to a new backend. So we're going page by page, and updating bindings, etc. The directive was one of zero refactoring. Just get it working, and we'll clean it up later. My thoughts on that approach are also best saved for another time. Regardless, I simply couldn't resist myself when I came across this.

Here is pared down example. The idea is that we have a list of objects that the user can choose from. For whatever reason, we need to store the currently selected item, and it's ID...separatly, as you do, I suppose.
<pre>
	<code class="javascript">
	var Model = function(){
	    var self = this;
	    self.options = ko.observableArray([
	    {id: 1, name: "Item1", description: "The first item"},
	    {id: 2, name: "Item2", description: "The second item"},
	    {id: 3, name: "Item3", description: "The third item"},
	    {id: 4, name: "Item4", description: "The fourth item"}
	    ]);
	    self.selectedOption = ko.observable();
	    self.selectedOptionId = ko.observable();
	    self.postTheThing =  function(){
	        //for real we do some ajax stuffs
	        alert(JSON.stringify(self.selectedOption()));
	    },
	    self.setSelectedOptionId = function(id){
	        self.selectedOptionId(id);
	    };
	    self.selectedOptionId.subscribe(function(){
	        var option = ko.utils.arrayFirst(self.options(), function(item){
	                return item.id === self.selectedOptionId();
	            });
	        if(option){
	            self.selectedOption(option);
	        }
	    });
	}

	ko.applyBindings(new Model());
</code>
</pre>
And the view code:
<pre>
	<code class="html">

	<h2>LOLWUT?</h2>
	<ul data-bind="foreach: options">
	    <li data-bind="click: function(){$parent.setSelectedOptionId($data.id)}, css: {active: $data.id === $parent.selectedOptionId()}, text: name"></li>
	</ul>
	<button data-bind="click:postTheThing">Save</button>
</code>
</pre>

To me, this was a weird combination of things. We've got inline function calls in the HTML, which seems like a rookie move. Then we've two things a rookie probably wouldn't do: we're subscribing to the observable, and we're using ko.utils.arrayFirst. 

So what does this code do? It's pretty basic actually. When you click an item, we'll call the setSelectedOptionId function with the Id of the item and update the selectedOptionId observable. Since we've subscribed to that observable, we then run a function that finds the first item in our array that has the current Id.

Seems like a combination of overthinking and ignorance of some foundational concepts in Knockout. A case of, "Well, I know the Id, and I need that object. How can I get it?" It's not all that terrible of a solution, except that Knockout provides a much simpler way to access items within a loop.

Within a loop, if you bind to a function, Knockout will provide you access to that object. That means we can write this:
<pre>
	<code class="javascript">
	var Model = function(){
	    var self = this;
	    self.options = ko.observableArray([
	    {id: 1, name: "Item1", description: "The first item"},
	    {id: 2, name: "Item2", description: "The second item"},
	    {id: 3, name: "Item3", description: "The third item"},
	    {id: 4, name: "Item4", description: "The fourth item"}
	    ]);
	    self.selectedOption = ko.observable();    
	    self.postTheThing =  function(){
	        //for real we do some ajax stuffs
	        alert(JSON.stringify(self.selectedOption()));
	    };
	    self.selectOption = function(item){
	        self.selectedOption(item);
	    };
	}

	ko.applyBindings(new Model());
	</code>
</pre>
And the view:

<pre>
<code class="html">
	<h2>DATS BETTER</h2>
	<ul data-bind="foreach: options">
	    <li data-bind="click: $parent.selectedOption, css: {active: $data === $parent.selectedOption()}, text: name"></li>
	</ul>
	<button data-bind="click:postTheThing">Save</button>
</code>
</pre>
In the new code, we get replace the setSelectedOptionId function and that explicit subscription, and replace them with a single function that takes one parameter.
<pre>
	<code class="javascript">
	self.selectOption = function(item){
	        self.selectedOption(item);
	    };
</code>
</pre>

When our function is called, item will refer to the item clicked. Simple.

You might have noticed I removed the Id observable. I did that originally because I couldn't find any place in the real code, other than the CSS binding, were it was used. So I just replaced the updated the CSS binding.

Oh, and I got rid of that inline function.

Now, I don't claim to be a Knockout master. I've only been working in it for about 2 months, so I'm sure there are ways to improve upon this more (that CSS binding bugs me). All the same, I thought I would put this out there, I mean, at least one dev out there didn't know it. Who knows, maybe it'll help somebody someday somewhere.

The point is one that you've heard made over and over again, I'm sure. Dont' overthink things. It's easy to get caught up on the problem, and conjure up cleverer and cleverer solutions. Often times, however, the solution is much simpler than we might think, but our fixation has blinded us to that fact. How many times have you left a problem, frustrated and spent, only to have a simple solution occur to you that night in bed? If find yourself saying, "there has got to be an easier way," you're probably right. This was an easy example of that, but it holds true for more complicated situations.

Don't overthink it. The simplest solution is probably the best. 
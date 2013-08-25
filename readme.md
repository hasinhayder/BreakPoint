#BreakPoint
Breakpoint helps you to define multiple breakpoint ranges and load external javascript files when someone resize their browser window to those breakpoints. Beside loading external scripts, Breakpoint also triggers an event whenevr browser width falls in any of those predefined breakpoint ranges.

##Using Breakpoint

Using BreakPoint is pretty simple. Include jQuery in your web application and then include jquery.breakpoint.js. Now you can define multiple breakpoint ranges and initialize like this

```
$(document).ready(function(){
	$.BreakPoint({
		breakpoints:{
			mobile:{max:480,load:true},
			default:{min:480,max:1024, load:true},
			wide:{min:1024,max:1200,load:true},
			superwide:{min:1200,load:true},
		}
	});
});
```

In the example above, we have defined four different breakpoints. The first one **mobile** will be used whenever browser is resized from 0px to 480 pixel (all inclusive). The next breakpoint, **default** will be used whenever browser is resized between 480px to 1024px (all inclusive), and so on. 

Now, whenever a breakpoint is reached, BreakPoint jQuery Plugin will load an external javascript file with the same name of the breakpoint. For example, when browser is resized to 400px it will fall under **mobile** and now an external file named **mobile.js** will be loaded and executed. 

By default BreakPoint will look for external javascript files in the **js/** folder in the current path. But you can change this by passing a parameter named **prefix**, like this

```
$(document).ready(function(){
	$.BreakPoint({
		prefix: "scripts/", 
		breakpoints:{
			mobile:{max:480,load:true},
			default:{min:480,max:1024, load:true},
			wide:{min:1024,max:1200,load:true},
			superwide:{min:1200,load:true},
		}
	});
});
```

Now BreakPoint will load external js files from the **scripts/** folder. 

## Breakpoint Parameters
1. prefix: By default, prefix is set to **js/** but you can change it to anything you want. 
2. breakpoints: for each breakpoints, there are three paramaters you can pass which are **min**, **max** and **load**. By default ```min``` is set to 0, ```max``` is set to 9999 and ```load``` is set to false. The **load** parameter is an important one if you want to load external javascript files whenever a breakpoint is reached. If ```load``` is set to ```true```, external files will be loaded, otherwise not. 


##BreakPoint Events
Whenever a breakpoint is reached, BreakPoint plugin will trigger a **window** event named **breakpoint**. The event object will have an attribute named **breakpoint** which will contain the name of the breakpoint that has been reached. Here is an example how you can add an event listener to this breakpoint event

```
$(document).ready(function(){
	$(window).bind("breakpoint",function(e){
		if(console)
		console.log(e.breakpoint);
	});
});

```
 
That's mainly it. Enjoy!



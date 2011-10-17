Dynamic
=======

Is a simple script for keeping track of asynchronous calls in an object's 
methods. Put simply, it ensures two asynchronous method calls will happen one
after the other. The example below illustrates:

``` javascript
$(function () {
	var dmc = ik.dynamic.make();
	dmc.map({
		sampleCall: function () {
			console.log("Call starting");
			var url = "http://code.jquery.com/jquery-latest.min.js";
			dmc.ajax({
				url: url,
				dataType: "script", 
				complete: function () {
					console.log("Call ending");
				}
			});
			
			return dmc;
		}
	});
	
	dmc.sampleCall().sampleCall();
});
```

Besides the obvious use for method chaining asyncrhonous calls, a dynamic 
object works like a queue of calls, so it can be used to ensure that particular 
method calls are executed sequentially.

Usage
-----

In order to use a dynamic object, all you have to do is:

1. Create a new dynamic template object, via `ik.dynamic.make()`.
2. Use the provided `map()` method to extend the object with any number
   of methods.
3. You 're done.
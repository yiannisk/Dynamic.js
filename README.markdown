Dynamic
=======

Is a simple script for keeping track of asynchronous calls in an object's 
methods. Put simply, it ensures two asynchronous method calls will happen one
after the other. The example below illustrates:

``` javascriot
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
ES6StylePromisesWithTheQLib
============================

Example of how to use the $q library using more ES6 style syntax.

#Intro
Within the popular AngularJs framework is a promise library called $q.  Although not commonly used, as services such as $http and $timeout will automatically return a promise for you, I do sometimes find the need when calling multiple promises. 

#Traditional Way
Create the deferred object. Call its resolve or reject methods in the body. Then return the deferred promise.

	function promiseOld(field) {

		var deferred = $q.defer();

		dataService1(field).then(function() {
			deferred.resolve();
		});

		return deferred.promise;
	}

#ES6 Style Way
Return $q() which takes a functions with resolve and reject parameters through its construction. Then simply call resolve() / reject() methods within the function.

	function promiseNew(field) {

		return $q(function(resovle){
		
			dataService1(field).then(function() {
				resolve();
			});
		});
	}

#Conclusion
To conclude, this is a much cleaner code which ties closer to the promise interface found within the ES6 specification.

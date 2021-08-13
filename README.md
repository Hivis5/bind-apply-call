1) The bind() Method

For such cases we can use the ECMAScript 5 bind() method of the Function.prototype property. This means bind() can be used by every single function.

var myCarDetails = car.displayDetails.bind(car); 
myCarDetails(); // GA12345 Toyota

The bind() method creates a new function where “this” refers to the parameter in the parenthesis in the above case “car”. This way the bind() method enables calling a function with a specified “this” value.

What if we would like to pass a parameter to the displayDetails function? We can use the bind method again. The following argument of the bind() method will provide an argument to the function bind() is called on.

Let me rewrite the car object:

var car = { 
    registrationNumber: "GA12345",
    brand: "Toyota",

    displayDetails: function(ownerName){
        console.log(ownerName + ", this is your car: " + this.registrationNumber + " " + this.brand);
    }
}

Example of passing arguments with bind():

var myCarDetails = car.displayDetails.bind(car, "Vivian"); // Vivian, this is your car: GA12345 Toyota


Unlike the call() and apply() methods, the bind() method doesn’t immediately execute the function. 
It just returns a new version of the function whose this sets to thisArg argument.

2) call() and apply() methods

    a) The call() method calls a function functionName with a given this value and arguments.

       The first argument of the call() method thisArg is the this value. It allows you to set the this value to any given object.


    b) The apply() method accepts two arguments:

        The thisArg is the value of this provided for the call to the function fn.
        The args argument is an array that specifies the arguments of the function fn. Since the ES5, the args argument can be an array-like object or array object.
        

THe apply() method is similar to the call() method except that it takes the arguments of the function as an array instead of the individual arguments.

Similar but slightly different usage provide the call() and apply() methods which also belong to the Function.prototype property.

This time there is a car object without the displayDetails function, which is located in the global context.

var car = { 
    registrationNumber: "GA12345",
    brand: "Toyota"
}

function displayDetails(ownerName) {
    console.log(ownerName + ", this is your car: " + this.registrationNumber + " " + this.brand);
}

We can use the apply() function:

displayDetails.apply(car, ["Vivian"]); // Vivian, this is your car: GA12345 Toyota

Or

displayDetails.call(car, "Vivian"); // Vivian, this is your car: GA12345 Toyota

Note that when using the apply() function the parameter must be placed in an array. Call() accepts both an array of parameters and a parameter itself. Both are great tools for borrowing functions in JavaScript.

bind(), call() and apply() functions can make your life easier when you need to set the value of ‘this’.

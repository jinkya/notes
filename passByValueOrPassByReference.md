# Call by value and Call by reference

### Intro
A great theory is developed to determine _when_ to evaluate the argument(s) of a function call for function and _what kind_ of value to pass to the function.
For more details, The Evaluation strategies reference in [wiki](https://en.wikipedia.org/wiki/Evaluation_strategy)

### Primary Terms
	name = 'ajinkya'
	Value =  'ajinkya'
	address (memory location) = 0x7fd5d258dd00 (just a random hex)

### Authentic definition 
-   When a parameter is  **passed by reference**, the caller and the callee  **use the same variable**  for the parameter. If the callee modifies the parameter variable, the effect is visible to the caller's variable.
    
-   When a parameter is  **passed by value**, the caller and callee have  **two independent variables**with the same value. If the callee modifies the parameter variable, the effect is not visible to the caller.  
*caller is calling the callee

![Pass by Value vs Reference Animated Gif](https://www.mathwarehouse.com/programming/images/pass-by-reference-vs-pass-by-value-animation.gif)

### Language Agnostic Approach

#### Javascript
Javascript is always pass by value but when a var refers to an object(including arrays), the "value" is a reference to the object.

	function f1(a,b,c){
		a = 3;
		b.push("flagA")
		c.val = false
	}

	var x = 1;
	var y = [ 'flag1', 'flag2' ]
	var z = { val: true }
	
	let p = 2;
	let q = [ 'flag3', 'flag4' ]
	let r = { val: true }
	
	f1(x,y,z)
	console.log(x, y, z) 
	// 1  ["flag1", "flag2", "flagA"] {val: false}
	
	f1(p, q, r)
	console.log(p, q, r)
	// 2  ["flag3", "flag4", "flagA"] {val: false}

Doesn't it seem much easier? Wait its not that simple  

	function f2(x, y, z){
		x = x * 10;
		y.val = "hero";
		z = { val: "heroine" };	
	}

	var a = 1;
	var b = { val: 'ajinkya' };
	var c = { val: 'aarunya' };

	let p = 1;
	let q = { val: 'rajesh' };
	let r = { val: 'ujwala' };
	
	f2(a, b, c);
	console.log(a, b, c);
	// 1 {val: "hero"} {val: "aarunya"}
	
	f2(p, q, r);
	console.log(p, q, r)
	// 1 {val: "hero"} {val: "ujwala"}
	
If you change the parameter itself that will not affect the item that is fed into parameter, but changing internals of a parameter that will propagate up.    
Technically it is [call by sharing](https://en.wikipedia.org/wiki/Evaluation_strategy#Call_by_sharing).

#### Python 


... to be continued
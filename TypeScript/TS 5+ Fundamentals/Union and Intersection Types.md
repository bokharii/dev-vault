* union types, represented by pipe symbol ( | )
	* can be thought of as OR for types
	* OneThroughFive | Evens => {1, 2, 3, 4, 5, 6, 8}
* When thinking about types as sets, we should consider 
	* values a type can accept AND
	* guarantees about set members
* intersection types, represented by the ampersand (&) symbol
	* opposite of the union type in some ways
	* OneThroughFive & Evens => {2, 4}
* ![[Screenshot 2026-07-09 at 10.14.27 AM.png]]


<h4>Union Types</h4>
* ![[Screenshot 2026-07-09 at 1.20.30 PM.png]]
* `let evenOrLowNumber = 5 as Evens | OneThroughFive;`
* you create sets by creating typings, and you can define types in terms of other types
* A **union type** in TypeScript is a type that combines multiple specific types using the | operator.
* The **cardinality** of a type is the number of members in a set or dimension
* Numbers are represented in JS as doubles (floating-point numbers)
* A **type alias** is a way of defining a type using a name and its definition
* Its a LOT more common to see union types when compared to intersection types
	* because for instance, functions can have different control flows where they return different things
		* `flipCoin()` can return `heads | tails`
* ![[Screenshot 2026-07-09 at 1.41.19 PM.png]]
	* looks through every number in the set, and as soon as it finds one that is not compatible, it bails
		* for example, printLowNumber(x) could potentially take in 6 from `Evens | OneThroughFive`, which obviously results in a type error
* Narrowing with type guards
	* use `instanceof`
* Discriminated union
	* using the first element of the tuple as a discriminator to help TypeScript understand and narrow down the possible types in a union
* Type guards are techniques like **instanceof** or **typeof** that allow TypeScript to narrow down the type of a variable within a specific code branch
* When accessing elements in a union type tuple, you can only access properties **common to all types**

#### Intersection Types
* 
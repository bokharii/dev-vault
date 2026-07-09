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
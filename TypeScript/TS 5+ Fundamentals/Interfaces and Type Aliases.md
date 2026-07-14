* allows us to give names to our types and pass them across module boundaries using imports/exports
* Type Alias
	* allows us to **define a meaningful name** for types
	* declare the shape of the type **in a single place**
	* **import and export** the type from modules
	* ![[Screenshot 2026-07-14 at 4.16.35 PM.png]]
		* so instead of printAmount taking in a (currency: string, value: number) it can just take in (amt: Amount)
	* a type alias can hold ANY type that you can define in TS, unlike interfaces
	* type aliases are like variables for types
	* type aliases are completely erased during the compilation process, only existing at compile-time for type checking
	* you can create a more specific type by using intersection types (&)
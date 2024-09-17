# Typescript Notes
- typescript provide type safety 
```typescript
let a = 9022
a = "siddharth"  // ⚠ Error Type 'string' is not assignable to type 'number'.
```
### How to install typescript compiler
- npm i typescript -g
### Typescript Setup 
- setting up a typescript project ( app.ts )
- configure tsconfig.js           ( tsc --init )
- compiling typescript            ( tsc app.ts ) &nbsp ( tsc ) &nbsp ( tsc --watch )

 ## Basics Types  
1. Primitive  (call by value ( When called, a copy is returned.))
     - Number       --> range (2<sup>53</sup>)
     - String      --> ""
     - Boolean     --> true/false
2. Non Primitive (Reference)  (call by reference ( When called, an address is returned.))
     - Array       &nbsp; &nbsp; &nbsp; 
     - Tuples      &nbsp; &nbsp; &nbsp; let arr: [number,string] = [44,"sidd"]
     - Function    &nbsp; &nbsp; &nbsp; enum user{ admin = "super admin" } &nbsp;   // access user.admin &nbsp; // *key = value
3 Type
- any
  ```typescript
  let a;          // type any  * bad practice 
  let a: number;  // type number
  ```
- unknown
  ```typescript
 let a: unknown;
 a = 7;
 a = "sidd";
 if(typeof a === "string")
     a.toUpperCase();
  ```
 - void
  ```typescript
  function abcd(): void {   // function kuch return nahi kar raha
    console.log("sidd")
  }
  ```
 - null
  ```typescript
   let a: null;
  ```
 - undefined 
  ```typescript
   let a: undefined;
  ```
 - never 
  ```typescript
   function abcd(): never {
      while(true) {}
   }
   abcd()
   console.log("sidd")   // kabhi bhi ye code run nahi hoga
  ``` 
  

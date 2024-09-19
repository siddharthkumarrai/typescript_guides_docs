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
3. Type
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
### Type Inference
```typescript
   let a = "sidd";
```
### Type annotations
```typescript
   let a: number | string | boolean;
   a = 12;
   a = "sidd";
   a = true

   function some( a: number, b: string ) : void { }
```
## Interfaces &nbsp; &nbsp; object parameter ki sakal hain
```typescript
   interface User{
      name: string;
      email: string;
      gender?: string;           // optional ho jayega de deya to thik nahi deya to bhi theek
   }

   function getDataOfUser(obj: User) { }
   getDataOfUser({name: "sidd", email: "sidd@fb.com"})
```
- Extending interfaces
```typescript
   interface User{
       name: string;
       email: string;
       password: string;
   }
   interface Admin extends User {   // admin ke pass user kibhi property hogi
       admin: boolean;
   }

   **Imp
   interface User{
       name: string;
   }
   interface User{                   // override nahi karega dono ko mila ke single interface aa jayega      
       aemail: string;
   }
```
## Type aliases &nbsp; &nbsp; 
```typescript
   type value = string | number | null;

   let a: value;
```
## Union and Intersection &nbsp; &nbsp; 
> Union
```typescript
   type sidd = string | number | null;
```
> Intersection
```typescript
   type User = {
      name: string,
      email: string,
   }
   type Admin = User & {
       getDetails(user: string): void
   }
```
#### Difference between type and interface
1.) type abcd = number;
    type abcd = string;
 error ayegi type mein , interface mein merge kar raha tha
 
2.) 
- type ka kam hain detatype batana
- interface ka kam hain object ka shape batana
## Classes and OOP
```typescript
class user{
    age = 0;
    constructor(public name: string , public email: string, public subject = "Maths"){
        this.name = name
        this.email = email
    }
}
let userOne = new user("sidd","sidd@fb.com") 
console.log(userOne)   // user { name: 'sidd', email: 'sidd@fb.com', subject: 'science', age: 0 }
```
> Access modifiers (public, private, protected)
- public
      
    


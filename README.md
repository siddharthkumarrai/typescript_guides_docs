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
- public &nbsp;  app khai pr bhi change kro or use karo variable ko change ho jayegi
```typescript
   class bottleMaker{
      constructor(public name: string){
          this.name = name;
      }
      changeName(){
          this.name = "sidd"
      }
   }
   let b1 = bottleMaker("milton")
   b1.name = "hululu"
```
- private &nbsp; aap bottleMaker ke ander public or private ko change kar sakte ho khai bhi
```typescript
   class bottleMaker{
      constructor(public name: string){
          this.name = name;
      }
      changeName(){
          this.name = "sidd"
      }
   }
   let b1 = bottleMaker("milton")
   b1.changeName()
   b1.name = "hululu" //
```
- Inheritance  (private mein jo bhi variable hain wo bas usi class mein access ho payenge
```typescript
class BottleMaker{
                 
    constructor (public name: string){}
                // (private name: string)
}

class MetalBottleMaker extends BottleMaker{
     constructor(name: string){
         super(name);
     }

     getValue(){
         console.log(this.name)
     }
}
let b1 = new MatalBottleMaker("millton")
```
- protected (jis class mein variable use ho skta hain or jisne extend kari usmein bhi access hoga but bhar nahi hoga or change nahi karne dega
```typescript
class BottleMaker{   
    protected name: "milton";
}

class MetalBottleMaker extends BottleMaker{
     public material = "metail";

     changename(){
         this.name = "something"
     }
}
let b1 = new MatalBottleMaker("millton")
b1.name = "other name"  // error ayega
```
> Readonly property
```typescript
   class User{
      constructor(public readonly name: string){}

      changeName(){
           this.name = "japan"
      }
   }
   let u1 = new user("sidd");
   u1.changeName()    // vhange nahi karne dega
```
> Optional Property
```typescript
   class User{
      constructor(public name: string, public gender?: string){}
   }
   let u1 = new user("sidd");
```
> Parameter property
```typescript
   class User{
      constructor(public name: string, public age: string){}  // parameter property bolte
   }
```
> Getters and Setters
```typescript
   class User{
      constructor(public _name: string, public _age: string){}

      get name() {
          return this._name
      }

      set name(value: string) {
           this._name = value;
      }
   }
```
> Static &nbsp; aap bin uska new instance banye us property or method ko access kar skte ho static memeber include nahi honge new instances mein
```typescript
   class siddLiberary{
       static version = 1.0;

       static getrandomNumber(){
              return Math.random();
       }
   }
   let sl = new siddLiberary(); abhi koi bhi member nahi hoga ismein
```
> Abstract classes and methods
- wo class jisk instance hum create na kre khali extends kare bas
- us class ko new keyword se naya instance na bane
## Functions
```typescript
   function abc(name: string, cb: (argument: string) => void){
      cb("sidd")
   }
   abc("sidd",(arg: string) =>{
      console.log(arg)
   }
```
> Optional and Default Parameter
- Optional 
```typescript
   function abc(name: string, gender?: string){}
```
- Default Parameter
```typescript
   function abc(name: string, gender: string = "tujhe nahi pata"){}
```
> Rest parameter
```typescript
   function friends(...args: string[]){
        console.log(args)
   }
   friends("sidd","abhi","raj","sag")
```
> Overloads
```typescript
   // ts function signature
   function abcd(a: string): void;
   function abcd(a: string, b: number): number;

   function abcd(a: any, b?: any){
      if(typeof a === "string" && typeof b === undefined){
          console.log("first")
      }
      if(typeof a === "string" && typeof b === "number"){
          return 123;
      }
      else throw new Error("something went wrong")
   }
   abcd("sidd")
   abcd("sidd",12)
```
### Generics

      

      
    


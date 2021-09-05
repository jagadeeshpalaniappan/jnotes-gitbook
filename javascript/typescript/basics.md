# Basics



{% tabs %}
{% tab title="Basics" %}
```typescript
const myAny: any = 'abc';

const myString: string = 'Jagadeesh Palaniappan';
const myNo: number = 101;

const myBoolean: boolean = true;

const myStrArr: string[] = ['a', 'b', 'c'];
const myNoArr: number[] = [1, 2, 3];

// ################### Object ###################

const myObj1: { name: string; age: number } = {
  name: 'Jagadeesh Palaniappan',
  age: 10
  // something: 'xxx'  // it errors out
};

// better way of declaring Object type

interface User {
  name: string;
  age: number;
  city?: string; // optional
}
const myObj2: User = {
  name: 'Jagadeesh2',
  age: 10
  // something: 'xxx'  // it errors out
};

const myObj3: User = {
  name: 'Jagadeesh3',
  age: 10,
  city: 'San Francisco'
};

// ################### Function ###################

const myFn1 = (a: number, b: number): number => {
  return a + b;
};

const result1 = myFn1(10, 5);
// const result1: number

type AddFn = (a: number, b: number) => number;

const myFn2: AddFn = (a, b) => {
  return a + b;
};

const result2 = myFn2(10, 5);
// const result2: number

const myFn3 = (options: { a: number; b: number }): number => {
  return options.a + options.b;
};

const result3 = myFn3({ a: 10, b: 5 });
// const result3: number

// ################### UNIONS ###################
type MaybeStringOrNoOrBool = string | number | boolean;

// ################### ENUM ###################
enum ActionEnum {
  Add,
  Concat,
  Bool
}

const myFn4 = (
  a: number,
  b: number,
  action: ActionEnum
): MaybeStringOrNoOrBool => {
  if (action === ActionEnum.Add) return a + b;
  if (action === ActionEnum.Concat) return a + '::' + b;
  if (action === ActionEnum.Bool) return !!(a && b);
};

const result4 = myFn4(10, 5, ActionEnum.Add);
console.log(result4); // 15
const result5 = myFn4(10, 5, ActionEnum.Concat);
console.log(result5); // 10::5
const result6 = myFn4(10, 5, ActionEnum.Bool);
console.log(result6); // true

// ################### TYPE-CASTING

class MyElement {
  prop1: string;
}
class MyChildElement extends MyElement {
  prop2: string;
}

function testFn(): MyElement {
  const o = new MyChildElement();
  o.prop1 = 'Prop1';
  o.prop2 = 'Prop2';
  return o;
}

const o1 = testFn();
console.log(o1.prop1); // Prop1
// console.log(o1.prop2);
// ERROR: Property 'prop2' does not exist on type 'MyElement'.

const o2 = testFn() as MyChildElement;
console.log(o2.prop1); // Prop1
console.log(o2.prop2); // Prop2

```
{% endtab %}

{% tab title="type vs interface" %}
```typescript
/*
##### type vs interface ##### 

type: (Type Alias)
- types are static - it alias to a fixed shape
- cannot extend another type (Type Alias)
- but we can make new types using unions and intersections
- but we cannot change the type itself

interface: 
- can extend another interface
- use 'interface' as much as possible 
- if you're building library exporting 'interface' is much better 
- (so that the user can extend the interface according to their needs

*/

// ------------------------------- Object: -------------------------------
enum Sex {
  Male = 'male',
  Female = 'female'
}
type Age = number;
type Name = { firsName: string; lastName: string };

// ################### using: type ###################

type UserTypeAlias = {
  name: Name;
  age: Age;
  sex: Sex;
};

const u1: UserTypeAlias = {
  name: { firsName: 'Jag', lastName: 'Pal' },
  age: 10,
  sex: Sex.Male
};

// MERGE: using union
type SpeciaTypeAlias = {
  special: boolean;
};
type SpecialUserTypeAlias = UserTypeAlias & SpeciaTypeAlias;

const su1: SpecialUserTypeAlias = {
  name: { firsName: 'Jag', lastName: 'Pal' },
  age: 10,
  sex: Sex.Male,
  special: true
};

// ################### using: interface ###################

interface UserInterface {
  name: Name;
  age: Age;
  sex: Sex;
}

const u2: UserInterface = {
  name: { firsName: 'Jag', lastName: 'Pal' },
  age: 10,
  sex: Sex.Male
};

// MERGE: using extends // RECOMMENDED
interface SpecialUserInterface extends UserInterface {
  special: boolean;
}
const su2: SpecialUserInterface = {
  name: { firsName: 'Jag', lastName: 'Pal' },
  age: 10,
  sex: Sex.Male,
  special: true
};

// ------------------------------- Function: -------------------------------
type GreetingTypeAlias = (text: string) => string;
const myFn10: GreetingTypeAlias = text => {
  return `Hello ${text}`;
};
myFn10('Jag');

interface GreetingInterface {
  (text: string): string;
}
const myFn11: GreetingInterface = text => {
  return `Hello ${text}`;
};
myFn11('Jag');

```
{% endtab %}
{% endtabs %}


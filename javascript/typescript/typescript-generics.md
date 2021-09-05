# Typescript Generics



{% tabs %}
{% tab title="1. Fn" %}
```typescript
// ------------------------ Fn without:TypeScript --------------------------------

// No Type:
const getLastItem1 = arr => {
  return arr[arr.length - 1];
};
const last1 = getLastItem1([1, 2, 3]);
// const last1: any // returns: any

// ----------------------- TypeScript Fn (without:Generics) --------------------------

// Number Type:
const getLastItem2 = (arr: Array<number>) => {
  return arr[arr.length - 1];
};
const last2 = getLastItem2([1, 2, 3]);
// const last2: number // returns: number

// const last22 = getLastItem2(['a', 'b', 'c']);
// ERROR: Type 'string' is not assignable to type 'number'.

// Number or String Type:
const getLastItem3 = (arr: Array<number | string>) => {
  return arr[arr.length - 1];
};
const last3 = getLastItem3([1, 2, 3]);
// const last1: string | number  // But what i expect here is only 'number'
const last31 = getLastItem3(['a', 'b', 'c']);
// const last31: string | number // But what i expect here is only 'string'

// #### How do i make this fn more generic?
// and what if i wanted to pass something 'custom object', does this function accept?
// const last32 = getLastItem3([{ name: 'a' }, { name: 'b' }]);
// Type '{ name: string; }' is not assignable to type 'string | number'.
// Answer is 'No' // Use: Generics

// ------------------------- TypeScript fn (with:Generics) --------------------------

// Generics: gives option to pass the custom type to the user
const getLastItem4 = <T>(arr: Array<T>): T => {
  return arr[arr.length - 1];
};

const last4 = getLastItem4([1, 2, 3]);
// const last4: number (typescript automatically 'infer' the dataType as 'number')
const last41 = getLastItem4(['a', 'b', 'c']);
// const last41: string (typescript automatically 'infer' the dataType as 'string')
const last42 = getLastItem4([{ name: 'a' }, { name: 'b' }]);
// const last42: { name: string; } (typescript automatically 'infer' the dataType as '{ name: string; }')

// Insted of typescript automatically 'infer', we can also explicitly specify the type
const last43 = getLastItem4<number>([1, 2, 3]);
// const last44 = getLastItem4<string>([1, 2, 3]);
// ERROR: Type 'number' is not assignable to type 'string'.

const last45 = getLastItem4<{ name: string }>([{ name: 'a' }, { name: 'b' }]);

// ######## 1. we can also write like this...
const getLastItem41 = <T>(arr: T[]): T => {
  return arr[arr.length - 1];
};
// getLastItem4 and getLastItem41 are same

// ######## 2. we can also have multiple generics // we can use any name (not only 'T')
const makeTuple = <X, Y>(a: X, b: Y): [X, Y] => {
  return [a, b];
};
const tuple1 = makeTuple('Jag', 101);
// const tuple1: [string, number] // (typescript automatically 'infer' the dataType)

// Insted of typescript automatically 'infer', we can also explicitly specify the type
const tuple2 = makeTuple<string, number>('Jag', 101);
// const tuple2: [string, number] // simmilar to 'tuple1'

// ######## 3.
const makeFullName1 = (obj: { firstName: string; lastName: string }) => {
  return { ...obj, fullName: obj.firstName + ' ' + obj.lastName };
};

const obj1 = makeFullName1({ firstName: 'Jag', lastName: 'Pal' });
// const obj1: { fullName: string; firstName: string; lastName: string; }

// what if i wanted pass some extra param - E.g. 'age'?
// const obj11 = makeFullName1({ firstName: 'Jag', lastName: 'Pal', age: 10 });
// ERROR:
// Argument of type '{ firstName: string; lastName: string; age: number; }' is not assignable to parameter of type '{ firstName: string; lastName: string; }'.
// Object literal may only specify known properties, and 'age' does not exist in type '{ firstName: string; lastName: string; }'.

const makeFullName2 = <T extends { firstName: string; lastName: string }>(
  obj: T
) => {
  return { ...obj, fullName: obj.firstName + ' ' + obj.lastName };
};

const obj2 = makeFullName2({ firstName: 'Jag', lastName: 'Pal', age: 10 });
// const obj2: { firstName: string; lastName: string; age: number; } & { fullName: string; }


```
{% endtab %}

{% tab title="2. Interfaces" %}
```typescript
// -------------------- TypeScript Interface (with:Generics) -----------------------
interface Tab1 {
  id: string;
  position: number;
  data: any;
}
interface NumberTab1 {
  id: string;
  position: number;
  data: number;
}
interface StringTab1 {
  id: string;
  position: number;
  data: string;
}

// ------------------- TypeScript Interface (without:Generics) -----------------------
interface Tab2<T> {
  id: string;
  position: number;
  data: T;
}
type NumberTab2 = Tab2<number>;
type StringTab2 = Tab2<number>;

```
{% endtab %}

{% tab title="3. JSX" %}
```jsx
import React, { useState } from 'react';

interface Props {
  firstName: string;
  lastName: string;
}

interface FullNameState {
  fullName: string;
}

export const Hello: React.FC<Props> = ({ firstName, lastName }) => {
  const [state, setState] = useState<FullNameState>({ fullName: '' });

  return (
    <div>
      <h1>Hello {firstName},</h1>
      <button
        onClick={() => setState({ fullName: firstName + ' ' + lastName })}
      >
        Get FullName{' '}
      </button>
      <p>Your full name is {state.fullName}</p>
    </div>
  );
};

```
{% endtab %}
{% endtabs %}


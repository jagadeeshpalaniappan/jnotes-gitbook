# TypeScript Decorators



{% tabs %}
{% tab title="1. Class" %}
```typescript
function getRandomNoUtil(min: number, max: number) {
  min = Math.ceil(min);
  max = Math.floor(max);
  return Math.floor(Math.random() * (max - min + 1)) + min;
}
console.log('------------------ without:Decorator ------------------------');

class BaseEntityClass {
  readonly id: number;
  readonly created: string;
  constructor() {
    this.id = getRandomNoUtil(1, 1000);
    this.created = new Date().toLocaleDateString();
  }
}

class User1 extends BaseEntityClass {
  constructor(public name: string) {
    super(); // it calls 'BaseEntity' constructor
  }
}

let user1 = new User1('Jagadeesh');
// 'id' and 'created' property populated automatically
console.log('name:', user1.name);
console.log('id:', user1['id']); // TODO: check why 'ny.id' is throwing error ?
console.log('created:', user1['created']);

console.log('------------------- with:Decorator -------------------------');

function BaseEntityDecorator() {
  return function(target: Function) {
    target.prototype.id = getRandomNoUtil(1, 1000);
    target.prototype.created = new Date().toLocaleString('es-ES');
  };
}

@BaseEntityDecorator()
class User2 {
  constructor(public name: string) {}
}

let user2 = new User2('Jagadeesh');
// 'id' and 'created' property populated automatically
console.log('name:', user2.name);
console.log('id:', user2['id']); // TODO: check why 'ny.id' is throwing error ?
console.log('created:', user2['created']);

```
{% endtab %}

{% tab title="2. Property" %}
```typescript
// Property Decorator
function AddEmojiPropertyDecorator(emoji) {
  return function(target: Object, key: string | symbol) {
    let val = target[key];

    const getter = () => {
      return val;
    };
    const setter = next => {
      console.log(`... setting:${key.toString()} , value:${next} ...`);
      val = `${emoji} ${next} ${emoji}`;
      console.log(`... setting:${key.toString()} , newVal:${val} ...`);
    };

    Object.defineProperty(target, key, {
      get: getter,
      set: setter,
      enumerable: true,
      configurable: true
    });
  };
}

class IceCreamClass {
  @AddEmojiPropertyDecorator('🍦')
  flavor: string;
  constructor() {}
  setFlavor(flavor: string) {
    console.log('--- IceCreamClass:setFlavor --- ', flavor); // vanila
    this.flavor = flavor; // decorator: setter gets invoked and adds emoji
    console.log('--- IceCreamClass:setFlavor --- ', this.flavor); // 🍦 vanila 🍦
  }
}

const ice1 = new IceCreamClass();
ice1.setFlavor('vanila');
console.log(ice1.flavor); // 🍦 vanila 🍦

```
{% endtab %}

{% tab title="3. Method" %}
```typescript
// Method Decorator
function AddEmojiMethodDecorator(toping: string) {
  return function(
    target: Object,
    key: string | symbol,
    descriptor: PropertyDescriptor
  ) {
    const original = descriptor.value;

    descriptor.value = function(...args: any[]) {
      console.log(`... setting:${key.toString()} , args:${args} ...`);
      const updatedArgs = args.map(arg => `${arg} :: ${toping}`);
      const resultVal = original.apply(this, updatedArgs);
      return resultVal;
    };

    return descriptor;
  };
}

export class IceCreamClass {
  @AddEmojiMethodDecorator('🍦')
  @AddEmojiMethodDecorator('🍫')
  @AddEmojiMethodDecorator('🍌')
  getIceCream(updatedFlavor: string) {
    console.log('--- IceCreamClass:getIceCream --- ', updatedFlavor); // vanila
    return updatedFlavor;
  }
}

const ice1 = new IceCreamClass();
ice1.getIceCream('vanila');
ice1.getIceCream('butterscotch');

```
{% endtab %}

{% tab title="4. Parameter" %}
```typescript
function logParameter(target: any, key: string, index: number) {
  var metadataKey = `__log_${key}_parameters`;
  if (Array.isArray(target[metadataKey])) {
    target[metadataKey].push(index);
  } else {
    target[metadataKey] = [index];
  }
}

function logMethod(target, key, descriptor) {
  if (descriptor === undefined) {
    descriptor = Object.getOwnPropertyDescriptor(target, key);
  }
  var originalMethod = descriptor.value;

  //editing the descriptor/value parameter
  descriptor.value = function(...args: any[]) {
    var metadataKey = `__log_${key}_parameters`;
    var indices = target[metadataKey];

    if (Array.isArray(indices)) {
      for (var i = 0; i < args.length; i++) {
        if (indices.indexOf(i) !== -1) {
          var arg = args[i];
          var argStr = JSON.stringify(arg) || arg.toString();
          console.log(`${key} arg[${i}]: ${argStr}`);
        }
      }
      var result = originalMethod.apply(this, args);
      return result;
    } else {
      var a = args.map(a => JSON.stringify(a) || a.toString()).join();
      var result = originalMethod.apply(this, args);
      var r = JSON.stringify(result);
      console.log(`Call: ${key}(${a}) => ${r}`);
      return result;
    }
  };

  // return edited descriptor as opposed to overwriting the descriptor
  return descriptor;
}

class Person {
  public name: string;
  public surname: string;

  constructor(name: string, surname: string) {
    this.name = name;
    this.surname = surname;
  }

  @logMethod
  public saySomething(
    @logParameter something: string,
    somethingElse: string
  ): string {
    return (
      this.name +
      ' ' +
      this.surname +
      ' says: ' +
      something +
      ' ' +
      somethingElse
    );
  }
}

var p = new Person('remo', 'jansen');
p.saySomething('I love playing', 'halo');

```
{% endtab %}
{% endtabs %}


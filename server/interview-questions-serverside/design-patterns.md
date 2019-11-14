# Design Patterns

```javascript
1. Creational       // talks abt 'creation' of an obj
    - Singleton     // only one obj instance per JVM (one President per Country)
    
    - Factory       // create object without exposing the creation logic to the client
                    // (Circle, Square, Rectangle) --> Shape 
                    //  Shape shape1 = shapeFactory.getShape("CIRCLE"); shape1.draw();
                    
    - Prototype     // (JS objects) (create a 'clone' of the current object)
    - Builder       // (builds a complex object using simple objects, using step-by-step)
                    // new ConfeeBuilder("Mocha").milk(true).sugar(false).size("L").build();
    
    
2. Structural      // talks abt 'structure' of an objs
    - MVC          // Model View Ctrl // Seperation of Concerns
    - Filter       // to filter a set of objects using different criteria and chaining them in a decoupled way through logical operations
    - Proxy        // a class represents functionality of another class


3. Behavioral     // talks abt one obj ~behavior~ with another obj
    - Observer    // if one obj is modified, its depenedent objects are to be notified)
    - Iterator    // helps iterating each items in a collection without need to know its underlying representation)
    - 
    
```


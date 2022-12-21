#### Class Parameter Properties
```typescript
class Person {
    constructor(public name: string, public age: string) {}
}

const adam = new Person('Adam', 120000)
console.log(adam.name, adam.age) // 'Adam', 1200000
```

#### Intersection Types
```typescript
type Point2D = {
    x: number
    y: number
}

type Point3D = Point2D & {
    z: number
}
```

#### Optional Modifier & Non-null Assertion
```typescript
type Point = { x: number, y: number, z?: number }
const point: Point = { x: 1, y: 2, z: undefined }

let nonNullPoint: Point
function initialize() {
    nonNullPoint= { x: 0, y: 0 }
}
initialize()
console.log('After initialized', nonNullPoint!.x, nonNullPoint!.y)
```

#### Never Type
```typescript
// const fail: (message: string) => never
const fail = (message: string) => {
    throw new Error(message)
}

// const sing: () => never
const sing = function() {
    while(true) {
        console.log('Never gonna give you up')
    }
}

// never can only assign to never
let example: never = 123 // Error: Type 'number' is not assignable to type 'never'.

// any type can assign to never and as same as that type
type Example = string | never // Same: type Example = string

// Usage: Ensure all cases are handled
type Square = {
    kind: 'square'
    size: number
}

type Rectangle = {
    kind: 'rectangle'
    width: number
    height: number
}
type Shape = 
    | Square
    | Rectangle

// function area(s: Shape): number
function area(s: Shape) {
    if(s.kind === 'square') {
        return s.size * s.size
    }
    const _ensureAllCasesAreHandled: never = s // Type'Rectangle' is not assignable to type 'never'
    return _ensureAllCasesAreHandled
}
```

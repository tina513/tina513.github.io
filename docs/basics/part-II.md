#### Type Aliases
```typescript
type Point = { x: number, y: number}

const center: Point = {
    x: 0,
    y: 0
}
```

#### Type Assertions & Casting
```typescript
let leet = '1337'

// Use as number
const asNum = leet as number
const castNum = +leet

console.log(asNum) // '1337'
console.log(castNum) // 1337
```

#### Structural Typing
In TypeScript’s structural-type system a type is considered to be a subtype if its component features are **equal-to** or a **superset** of those specified by the base type. No explicit inheritance or extension is required.
```typescript
type Point2D = { x: number, y: number }
type Point3D = { x: number, y: number, z: number }

let point2D: Point2D = { x: 0, y: 10 }
let point3D: Point3D = { x: 0, y: 10, z: 20 }

function takesPoint2D(point: Point2D) {}
takesPoint2D(point3D) /** Extra info ok **/
```

#### Interfaces
```typescript
// Type
type Point2D = {
    x: number
    y: number
}

type Point3D = Point2D & {
    z: number
}

export const point: Point3D = {
    x: 0,
    y: 0,
    z: 0
}

// Interface
interface Point2D {
    x: number
    y: number
}

interface Point3D extends Point2D {
    z: number
}

export const point: Point3D = {
    x: 0,
    y: 0,
    z: 0
}
```

#### Interface Declaration Merging
```typescript
// Express Base
export interface Request {
    body: any
}

// Express JSON
export interface Request {
    json: any
}

// App
function handleRequest(req: Request) {
    req.body
    req.json
}
```
#### Type VS Interface
| type | interface |
| ----------- | ----------- |
| Unions | Declaration Merging |
| Intersections | Familiarity (extends) |
| Primitives | |
| Shorthand Functions | |
| Advanced Type Functions | |
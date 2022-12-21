#### ReturnType<T>
```typescript
export function createPerson(firstName: string, lastName: string) {
    return {
        firstName,
        lastName,
        fullName: `${firstName} ${lastName}`
    }
}

function logPerson(person: ReturnType<typeof createPerson>) {
    console.log(
        'Person:',
        person.firstName,
        person.lastName,
        person.fullName
    )
}
```

#### Readonly<T>
```typescript
export type Point = {
    x: number,
    y: number,
    z: number
}

const center: Readonly<Point> = {
    x: 0,
    y: 0,
    z: 0
}

center.x = 100 // Error: readonly field
```

#### Mapped<T>
```typescript
export type Point = {
    readonly x: number,
    y?: number
}

export type Mapped<T> = {
    readonly [P in keyof T]-?: T[P]
}

export type Result = Mapped<Point> // type Result = { readonly x: number, readonly y: number }
```

#### Partial<T>
```typescript
export class State<T> {
    constructor(public current: T) {}
    update(next: Partial<T>) {
        this.current = { ...this.current, ...next }
    }
}

const state = new State({ x: 0, y: 0 })
state.update({ y: 123 })
console.log(state.current) // { x: 0, y: 123 }
```

#### Required<T>
```typescript
type CircleConfig = {
    color?: string,
    radius?: number
}

class Circle {
    private config: Required<CircleConfig>

    constructor(config: CircleConfig) {
        this.config = {
            color: config.color ?? 'green',
            radius: config.radius ?? 0
        }
    }

    draw() {
        // No null checking needed
        console.log(`Color: ${this.config.color}, Radius: ${this.config.radius}.`)
    }
}
```

#### Record<K,V>
```typescript
type Pages = Record<'home' | 'services' | 'contact', { id: string, title: string }>
```

#### Template Literal Type
```typescript
type Size = 'small' | 'medium' | 'large'
type Color = 'primary' | 'secondary'

type Style = `${Size}-${Color}` // "small-primary" | "medium-secondary" | ...
```


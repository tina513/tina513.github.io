#### Primitive
```typescript
let isPresent: boolean = false
let magic: number = 66.6
let hello: string = 'world'

let notDefined: undefined = undefined
let notPresent: null = null
```

#### Array & Tuples & Object
```typescript
let arr: Array<number> = [1, 2, 3]
let array: number[] = [3, 4, 5]

let tuple: [number, number] = [0, 0]

let center: { x: number, y: number } = {
    x: 0,
    y: 0
}
```

#### Function 
```typescript
function add(a: number, b: number): number {
    return a + b
}

function log(message: string): void {
    console.log('LOG:', message)
}

function sum(...values: number[]) {
    return values.reduce((prev, curr) => prev + curr)
}

sum(1, 2, 3)
```

#### Classes & Inheritance
```typescript
class Animal{
    protected name: string

    constructor(name: string) {
        this.name = name
    }

    public move(distanceInMeter: number): void {
        console.log(`${this.name} moved ${distanceInMeter}m.`)
    }
}

let cat = new Animal('Cat')
cat.move(10)
cat.name = 'Dog' /** Error: Can't access the private/protected field outside of class */

class Bird extends Animal {
    fly(distanceInMeter: number): void {
        /** protected field can be accessed in child class */
        console.log(`${this.name} flew ${distanceInMeter}m.`)
    }
}
```
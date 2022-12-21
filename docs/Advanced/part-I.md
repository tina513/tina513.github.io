#### Implements Keyword
To ensure class provide all the features required by the type
```typescript
type Animal = {
    name: string
    voice(): string
}

class Cat implements Animal {
    constructor(public name: string) {}
    voice() { return 'meow' }
}
```

#### Definite Assignment Assertion
```typescript
let dice!: number
function rollDice() {
    dice = (Math.floor(Math.random() * 6) + 1)
}
rollDice()
console.log('Current Dice Value', dice)
```

#### Type Guards - Implementation
```typescript
type Square = {
    size: number
}

type Rectangle = {
    width: number
    height: number
}

type Shape = Square | Rectangle

function isSquare(shape: Shape): shape is Square {
    return 'size' in shape
}

function isRectangle(shape: Shape): shape is Rectangle {
    return 'width' in shape
}

function area(shape: Shape) {
    if(isSquare(shape)) {
        return shape.size * shape.size
    }
    if(isRectangle(shape)) {
        return shape.width * shape.height
    }
    const _ensure: never = shape
    return _ensure
}
```

#### Assertion Function - Test
```typescript
type Person = {
    name: string
    dateOfBirth?: Date
}

function assert(condition: unknown, message: string): asserts condition {
    if(!condition) throw new Error(message)
}

function assertDate(value: unknown): asserts value is Date {
    if(value instanceof Date) return
    else throw new TypeError('value is not a Date')
}

const maybePerson = loadPerson()

assert(maybePerson !== null, 'Could not load person')
console.log('Name:', maybePerson.name)

assertDate(maybePerson.dateOfBirth)
console.log('Date of Birth:', maybePerson.dateOfBirth.ISOString())
```
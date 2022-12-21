#### Modifier: readonly
readonly fields
```typescript
type Point = {
    readonly x: number
    readonly y: number
}
const point: Point = {
    x: 0,
    y: 0
}
// Property assignment
point.x = 1 /** Error: readonly field can't be modified */
point.y = 2 /** Error: readonly field can't be modified */
// Property read
console.log(`${point.x}, ${point.y}`)
```
readonly arrays & tuples
```typescript
function reverseSorted(input: readonly number[]): number[] {
    return input.sort().reverse() // Error: Cannot mutate input -> use slice()
}

type Point = readonly [number, number]
```

#### Union Type & Literal Type
```typescript
type Padding = number | string

type CardinalDirection = 'North' | 'East' | 'South' | 'West'
type DiceValue = 1 | 2 | 3 | 4 | 5 | 6
```

#### Type Narrowing 
```typescript
// Primitive Type Narrowing: typeof
function padLeft(value: string, padding: number | string) {
    if(typeof padding === 'number') {
        return Array(padding + 1).join(' ') + value
    }
    if(typeof padding === 'string') {
        return padding + value
    }
    throw new Error(`Expectd number or string, got ${padding}.`)
}
padLeft('Hello world', 4) // '    Hello world'

// Classes Narrowing: instanceof
class Cat {
    meow() {
        console.log('meow')
    }
}

class Dog {
    bark() {
        console.log('bark')
    }
}

type Animal = Cat | Dog

function speak(animal: Animal) {
    if(animal instanceof Cat) {
        animal.meow()
    }
    if(animal instanceof Dog) {
        animal.bark()
    }
}

// Object Narrowing: in
type Square = {
    size: number
}

type Rectangle = {
    width: number
    height: number
}

type Shape = Square | Rectangle

function area(shape: Shape) {
    if('size' in shape) {
        return shape.size * shape.size
    }
    if('width' in shape) {
        return shape.width * shape.height
    }
}
```

#### Discriminated Unions
```typescript
type ValidationSuccess = {
    isValid: true
    validatedValue: string
}

type ValidationFailure = {
    isValid: false
    errorReason: string
}

type ValidationResult = ValidationSuccess | ValidationFailure

function logResult(result: ValidationResult) {
    if(result.isValid) {
        console.log('Success, validated value:', result.validatedValue)
    }
    if(result.isValid === false) {
        console.error('Failure, error reason:', result.errorReason)
    }
}
```
#### Operator: typeof
Generate type from variable
```typescript
const center = {
    x: 0,
    y: 0
}

type Point = typeof center

const unit: Point = {
    x: center.x + 1,
    y: center.y + 1
}
```

#### Lookup Types
```typescript
type SubmitRequest = {
    consent: {
        informationTrue: boolean,
        personInfoCheckConsend: boolean,
        ...
    },
    payment: {
        creditCardToken: string
    }
}

export function getPayment(): SubmitRequest['payment'] {
    return {
        creditCardToken: '324234sdfsd87sdf'
    }
}
```

#### Operator: keyof
```typescript
type Person = {
    name: string,
    age: number,
    location: string
}

const john: Person = {
    name: 'John',
    age: 35,
    location: 'Melbourne'
}

function logSet<Obj, Key extends keyof Obj>(obj: Obj, key: Key, value: Obj[Key]) {
    console.log('Setting:', key, value)
    obj[key] = value
}

logSet(john, 'age', 40)
```

#### Conditional Types
```typescript
export type TypeName<T> = 
    T extends string ? 'string' :
    T extends number ? 'number' :
    T extends boolean ? 'boolean' :
    'object'

function typeName<T>(t: T): TypeName<T> {
    return typeof t as TypeName<T>
}

const str = typeName('hello world')
const num = typeName(123)
const bool = typeName(true)
const obj = typeName(null) // 'object'
```
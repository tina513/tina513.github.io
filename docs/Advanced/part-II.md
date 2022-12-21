#### Function Overloading
Add in function overloading shadow the internal function signature
```typescript
function reverse(string: string): string
function reverse(string: string[]): string[]
function reverse(string: string | string[]) {
    if(typeof stringOrStringArray == 'string) {
        return stringOrStringArray.split('').reverse().join('')
    } else {
        return stringOrStringArray.slice().reverse()
    }
}

const hello = reverse('hello') // 'olleh'
const h_e_l_l_o = reverse(['h', 'e', 'l', 'l', 'o']) // ['o', 'l', 'l', 'e', 'h']
```

#### Abstract Classes
```typescript
abstract class Command {
    abstract commandLine(): string

    execute() {
        console.log('Executing:', this.commandLine())
    }
}

class GitResetCommand extends Command {
    commandLine() {
        return 'git reset --hard'
    }
}

new GitResetCommand().execute()
new Command() // Error: Cannot create an instance of an abstract class
```

#### Index Signature
```typescript
type Person = {
    displayName: string
    email: string
}

type PersonDictionary = {
    [username: string]: Person | undefined
}

const persons: PersonDictionary = {
    jane: { displayName: 'Jane Doe', email: 'jane@example.com' }
}
persons['john'] = { displayName: 'Jane Doe', eamil: 'jane@example.com' } // Error: 'eamil' does not exist in type 'Person'
```

#### Double Assertion & const Assertion
```typescript
// Double Assertion
type Point = { x: number, y: number }
type Person = { name: string, age: number }

let point: Point = { x: 0, y: 0 }
let person: Person = { name: 'john', age: 2 }

point = person as unknown as Point

// const Assertion 
// -> change all field including array to readonly
// -> change string to literal type (enum)
const dave = {
    name: 'Dave',
    role: 'drummer'
} as const
dave.name = 'John' // Error 
```

#### Generic Constraints
```typescript
type NameFields = { firstName: string, lastName: string }

function addFullName<T extends NameFields>(obj: T): T & { fullName: string } {
    return {
        ...obj,
        fullName: `${obj.firstName} ${obj.lastName}`
    }
}

const john = addFullName({
    email: 'john@example.com',
    firstName: 'john',
    lastName: 'Doe'
})

console.log(john.fullName)
```
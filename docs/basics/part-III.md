#### Generics
```typescript
class Queue<T> {
    data = []

    push(item: T) { 
        this.data.push(item) 
    }

    pop(): T {
        return this.data.shift() 
    }
}

const queue = new Queue<number>()
queue.push(123)
queue.push('random string') /** Error: only support number type */
queue.pop() /** 123 */
```

#### Async Await
print out 3 sec by sequence with 1000ms wait in between
```typescript
// Async Await
const delay = (ms: number) => new Promise(res => setTimeout(res, ms))

const mainAsync = async () => {
    await delay(1000)
    console.log('1s')
    await delay(1000)
    console.log('2s')
    await delay(1000)
    console.log('3s')
}

// Callback Hell
const main = () => {
    setTimeout(() => {
        console.log('1s')
        setTimeout(() => {
            console.log('2s')
            setTimeout(() => {
                console.log('3s')
            })
        })
    })
}
```

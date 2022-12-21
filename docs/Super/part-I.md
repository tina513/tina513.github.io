#### Autocomplete Literal Unions with Primitives
```typescript
type Padding = 'small' | 'normal' | 'large' | (string & {})

function getPadding(padding: Padding): string {
    if(padding === 'small') return '12px'
    if(padding === 'normal') return '16px'
    if(padding === 'large') return '24px'
    return padding
}

let padding: Padding
padding = 'small' // Provide nice autocomplete from IDE
padding = '8px' // Also support other string values
```

#### Operator: satisfies
```typescript
type ColorString = 'red' | 'blue' | 'yellow' | 'purple'
type ColorRGB = [red: number, green: number, blue: number]
type Color = ColorString | ColorRGB

type Theme = Record<string, Color>

const theme = {
    primary: 'red',
    secondary: [0, 255, 0]
} satisfies Theme

const [r, g, b] = theme.secondary
```

#### Special Type: PropertyKey
```typescript
let example: PropertyKey // type PropertyKey = string | number | symbol
```

#### Awaited<T> Utility
```typescript
async function example<T>(input: T) {
    const output: Awaited<T> = await input
}
```
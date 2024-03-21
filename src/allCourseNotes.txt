//types //

let a = 'sfg'

const b = 4

a = 4

//null vs undefined

let c: null = null
c = undefined

// array // 

const a: number[] = [1, 2, 3]

a.push(4)

const b: Date[] = [new Date()]

//any //

let a: any = 4

a = 3
a = 'saf'
a. //no auto complete do not use any cause it is counterproductive

const b = fetch('serrsa').then(res => res.json()).then(data => {
  data
})

//object basics //

const person: {name: string; age: number; isProgrammer?: boolean} = { name: 'evan', age: 22}

person.isProgrammer = true

//types vs interfaces//

interface Person {
  name: string; 
  age: number; 
  isProgrammer?: boolean;
}

const person: Person = { name: 'evan', age: 22}

person.isProgrammer = true

//interface only used with objects

//defining functions //

function sum(a: number, b: number): number{
  return a + b
}

const c = sum(1, 2) //knows c will be number

type Person = {
  name: string;
}

function printPerson (person: Person){
  console.log(person.name)
}

const person = { name: 'evan', age: 28} //as long as it includes name, its good

printPerson(person)

//void type

//destructuring rest parameters 

type Option = {
  debugMode?: boolean
  indentLevel?: number
}

function printNameAndAge(
  name: string, {
    debugMode = false, indentLevel }: Option = {}
) {
  console.log("sgs")
}

function sum(...nums: number[]){
  return
}

sum(1, 2, 4)
sum(1,2)

//typing variables as functions

function sumWithCallback(a: number, b: number, cb: (sum: number)){
  cb(a + b)
}

sumWithCallback(1, 2, (sum)=> {
  console.log(sum)
})

type PrintNameFunc = (name: string) => void

function f(name: string){
  return 2
}

//unions

type Todo = {
  name: string
  status: 'Complete' | 'Incomplete' | 'Draft'
}

type Person = {
  name: string
  age: number
}

type TodoPerson = Todo | Person

const todo: Todo = {name: 'Laundry', status: 'Complete'}

//unions need to be written as a type, not interface

//intersections
//be both at the same time rather than prior

type Person = {
  name: string
  age: number
}

type Todo = {
  complete: boolean
}

type PersonWithId  = Person & Todo & { id: string}

const person: PersonWithId = {id: 'daffa', name: 'Evan', age: 28}

//readonly

type Person = {
  readonly id: number
  name: string
  age: number
}

const person: Person = {id: 1, name: 'Evan', age: 28}

//keyof

type Person = {
  age: number
  name: string
  isProgrammer?: boolean
}

function groupBy

const age = getValue('age', { name: 'evan', age: 22})

function groupBy(key: keyof Person, people: Person[]){
  return person[key]
}

//typeof

function sayHi(name: string){
  console.log(name)
}

type FuncType = typeof sayHi

//index

const a = {
  name: 'evan',
  age: '22',
  isProgrammer: true
}

type A = (typeof a)[keyof typeof a] // get any value
type A = (typeof a)['name'] // name string value 

type Person = {
  name: string
  skillLevel: 'Beginner' | 'Intermediate' | 'Expert'
}

type PeopleGroupedBySkillLevel = {
  [index in Person['skillLevel']]: Person[] //index = skilllevel
}

type PeopleGroupedBySkillLevel = {
  [index: Person['name']]: Person[] //find name
}

const a: PeopleGroupedBySkillLevel = {
  'Beginner': [{name: 'evan', skillLevel: 'Beginner'}],
  'Intermediate':
}

//const and enums

const SKILL_LEVELS = ['Beginner', 'Intermediate', 'Expert'] as const

type Person = {
  skillLevel: (typeof SKILL_LEVELS)[number]
}

SKILL_LEVELS.forEach(skillLevel => {
  console.log(skillLevel)
})

const person = {
  age: 28,
  name: 'evan',
  address: {
    street: 'coral dr.',
  },
} as const

//tuples

const person = {
  name: 'evab',
  age: 26
}

Object.entries(person).forEach(([key, value]) => {
  console.log(key, value)
})

type Tuple = [string, boolean]
const a: Tuple = ['sfa', true]

//generics 

function getSecond<ArrayType>(array: ArrayType[]) {
  return array[1]
}

const a = [1, 2, 3]
const b = ['fafasf', 'afsda', 'adsd']

const retA = getSecond(a)
const retB = getSecond(b)

const c = new Map<string, number>([['asdas', 3]])
c.set('sadas', 3)

type APIResponse<TData extends object = { status: number }> = {
  data: TData
  isError?: boolean
}

type UserResponse = APIResponse<{name: string, age: number}>

const d: UserResponse = {
  data: {
    name: 'sasd',
    age: 534
  },
  isError: false
}

const e: Array<number> = [1, 2, 3] //these are the same
const f: number[] = [1, 2, 3]

function aToO<T>(array: [string, T][]){
  const obj: {
    [index: string]: T
  } = {}

  array.forEach(([key, value]) => {
    obj[key] = value
  })
  return obj
}

const arr: [string, number | boolean][] = [
  ['keyOne', 1],
  ['keyTwo', 2],
  ['keyThree', 3],
]

const obj = aToO(arr)

//pick / omit

Pick<Person, 'name | status' | 'completed')>

//partial and required

//return type and parameters

//record

//awaited

//basic type guards

type Todo = {
    dueDate: Date | string
}

function extendTodo(todo: Todo) {
    if (todo.dueDate instanceof Date){
        
    } else {
        console.log(todo.dueDate)
    }
    switch (todo.priority){
        case 'High':
            console.log(todo.priority)
    break
        case 'Normal':
            console.log(todo.priority)
    break
        case 'Low':
            console.log(todo.priority)
    break
    }
}

//! = cannot be null

//never type

//unknown type

//as casting

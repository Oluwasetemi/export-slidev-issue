---
theme: seriph
background: https://res.cloudinary.com/drnqdd87d/image/upload/f_auto/nmgakkzd3lmlibnfosps
title: TypeScript Class Notes by @Oluwasetemi
info: |
  ## TypeScript Class Notes

  making of world class developers with AltSchool Africa.

  Join at [AltSchool Africa](https://altschoolafrica.com)
class: text-center center
highlighter: shiki
drawings:
  persist: false
transition: slide-left
mdc: true
hideInToc: true
---

# TypeScript Class Notes

AltSchool Africa

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Are you ready to learn TypeScript? Press <kbd>space</kbd> on your keyboard <carbon:arrow-right class="inline"/>
  </span>
</div>

<div class="abs-br m-6 flex gap-2">
  <button @click="$slidev.nav.openInEditor()" title="Open in Editor" class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon:edit />
  </button>
  <a href="https://github.com/Oluwasetemi/typescript-class-note" target="_blank" alt="GitHub" title="Open in GitHub"
    class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
  <a href="https://github.com/Oluwasetemi/typescript-class-note" target="_blank" alt="GitHub" title="Open in GitHub"
    class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-download />
  </a>
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
class: grid place-content-center
hideInToc: true

---

# What is TypeScript?

<br>
TypeScript is a strongly typed programming language that builds on JavaScript, giving you better tooling at any scale.

<v-click>

## JavaScript and More

TypeScript adds additional syntax to JavaScript to support a tighter integration with your editor. Catch errors early in your editor.
A Result You Can Trust

</v-click>

<v-click>

TypeScript code converts to JavaScript, which runs anywhere JavaScript runs: In a browser, on Node.js or Deno and in your apps.
Safety at Scale

</v-click>

<v-click>
TypeScript understands JavaScript and uses type inference to give you great tooling without additional code

</v-click>
<br>
<br>

Read more about [TypeScript?](https://www.typescriptlang.org/)

<style>
h1,h2 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---
layout: two-cols
layoutClass: gap-16
transition: slide-up
class: grid place-content-center
hideInToc: true

---

# Table of Content

What are the things we will be covering?

::right::

<Toc v-click minDepth="1" maxDepth="2"></Toc>

---

# The Basics

- Static type-checking
- Non-exception Failures
- Types for Tooling
- tsc, the TypeScript compiler
- Emitting with Errors
- Explicit Types
- Erased Types
- Downleveling
- Strictness
- noImplicitAny
- strictNullChecks

---
hideInToc: true
---

# TypeScript Compiler `tsc`

- The TypeScript compiler is a tool that takes TypeScript code and turns it into JavaScript code.

- The TypeScript compiler can be installed as a Node.js package.

- The TypeScript compiler can be run from the command line.

- The TypeScript compiler can be configured using a configuration file.

- The TypeScript compiler can be used to compile multiple files.

- The TypeScript compiler can be used to compile a project.

```shell
npm install -g typescript

tsc hello.ts

tsc --noEmitOnError hello.ts

tsc --init


```

---
hideInToc: true
---

# tsconfig.json

<v-clicks>

- The tsconfig.json file is a configuration file that tells the TypeScript compiler how to compile your TypeScript code.

- Strictness: You can use the strict flag to enable all strict type-checking options or in the config file. You can opt out of strictness by setting strict to false or `noImplicitAny` to false and `strictNullChecks` to false.

- Downleveling: You can use the target flag to specify the version of JavaScript that the TypeScript compiler should output. The default is ES3.

- Emitting with Errors: You can use the noEmitOnError flag to prevent the TypeScript compiler from emitting JavaScript code if there are any errors.

- Explicit Types: You can use the noImplicitAny flag to prevent TypeScript from inferring the any type.

</v-clicks>

---
hideInToc: true
---

# tsconfig.json

- Erased Types: You can use the noUnusedLocals and noUnusedParameters flags to prevent TypeScript from emitting JavaScript code if there are any unused variables or parameters.

```json
{
  "compilerOptions": {
    "strict": true,
    "noImplicitAny": true,
    "strictNullChecks": true,
    "target": "ES5",
    "noEmitOnError": true
  }
}
```

---

# Everyday Types

The primitives, any, Type annotations on variables, Functions, Object types, Union Types, Type Aliases, Interfaces, Type Assertions, Literal Types, null and undefined, Enums

````md magic-move
```ts
let person: string | number = "OjoT99";

if (typeof person === "string") {
  person.split("T");
} else {
  // only number
  // person.toFixed(2);
}

let age: number = 99;

let isAltSchoolStudent = false;
let nothing = null;
let something = undefined;
```

```ts
let arrayOfScores = [99, 45, 56, 67, 99];
let arrayOfScores2: number[] = [99, 45, 56, 67, 99];

let arrayOfNames: string[] = ["bisi", "sola", "augustina", "typescritina"];

let arrayOfTruths = [true, false];

let names: Array<string> = ["dancing", "eating", "sleeping"];
// <> -> generics  Array<number> Array<boolean> Array<null>

let arrayInsideArrays = [["a"], ["b"]];

let newArr = [undefined];
```

```ts
let obj: { name: string; age: number; job?: string } = {
  name: "ade",
  age: 99,
};

function greet(msg: string): string {
  return msg + "Hi :dance:";
}

if (typeof obj.job === "string") {
  // typeguard
  greet(obj.job);
} else {
  // strictly undefined
  obj.job;
}
```

```ts
let profile: Record<string, number> = {
  age: 99,
  height: 6,
  weight: 100,
};

let objFlex: Record<string | symbol, string | boolean | number> = {};

objFlex.name = "lagbaja";
objFlex.animal = "cat";
objFlex[Symbol("id")] = true;
// any or never
//
let objFlexNumber: Record<string, number> = {
  age: 99,
};
```

```ts
// mixing types
const specialArr: Array<number | string | [] | {}> = [
  "name",
  99,
  {},
  [],
  "ginia",
  100,
];

let result: number[] = person.split("T");

result;

console.log(result);
console.log("Hello", "AltSchool");
```

```ts
let user: "student" | "admin";

user = "temi";

user = "admin";
```

```ts
function add(): number {
  console.log("hello");
  return 99;
}

// typing arguments
function add2(a: number, b: number): number {
  return a + b;
}

add2(99, 78);
```

```ts
// function overloading

function add3(a: number, b: number): number;
function add3(a: string, b: string): string;
function add3(a: any, b: any): any {
  return a + b;
}

add3("na", "me");
add3(99, 78);
let name2: any = "wale";
let age2: any = 99;
add3(name2, age2);
```

// type assertion as
//

```ts
// type alias
type Person = {
  name: string;
  age: number;
};

let person2: Person = {
  name: "ade",
  age: 99,
};
```

//
//

```ts
// interface
interface Person2 {
  name: string;
  age: number;
}

function greet2(person: Person2): string {
  return `Hello ${person.name}`;
}

greet2({ name: "ade", age: 99 });
```

```ts
// type assertion
let res = JSON.parse('{"name": "ade"}') as { name: string };
```

```ts
// 'satifies', 'as const', '!'
```

```ts
const addTwoNumbers = (a: number, b: number): number => {
  return a + b;
};

interface Params {
  a: number;
  b: number;
}

const addTwoNumberObject = (params: { a: number; b: number }): number => {
  return params.a + params.b;
};

```

```ts
// extending the inteface(obj only!)
interface ThreeParams extends Params {
  c: number;
}
// conditional type
type NewParams = ThreeParams extends Params ? string : number;

const addThreeNumberObject = (params: ThreeParams): number => {
  return params.a + params.b + params.c;
};

addThreeNumberObject({ a: 99, b: 78, c: 100 });
```

```ts
// make b optional
const addTwoNumberObject2 = (params: { a: number; b?: number }): number => {
  if (params.b) {
    return params.a + params.b;
  }
  return params.a;
};

console.log(addTwoNumberObject2({ a: 99 }));
```

```ts
const addTwoNumberObject3 = (params: { a?: number; b?: number }): number => {
  if (params.a) {
    return params.a;
  }

  if (params.b) {
    return params.b;
  }

  return 5;
};

addTwoNumberObject3({});
```

```ts
const addTwoNumber3 = (a: number = 2, b: number = 5) => {
  return a + b;
};

addTwoNumber3();

type Admin = {
  name: boolean;
};
```
````

---
hideInToc: true
---

# Everyday Types

````md magic-move
```ts {*|1-3|*|6-9|10-13|15|*}
function getPersonName(admin: Admin) {
  return admin.name;
}
getPersonName({ name: false });

type AdminModified = {
  name: string;
  role: "client" | "admin" | "superadmin";
};

function getPersonString(admin: AdminModified) {
  return `${admin.name} is a ${admin.role}`;
}

getPersonString({ name: "ken", role: "superadmin" });
```

```ts
type Post = {
  title: string;
  author: string;
  id: number;
  body: string;
};

type AdminWithPosts = {
  posts: Array<Post>;
  name: string;
  role: "client" | "admin" | "superadmin";
};

function getPersonPost(person: AdminWithPosts): Array<Post> {
  return person.posts;
}
```

```ts
let res = getPersonPost({
  posts: [
    {
      title: "hello",
      author: "ken",
      id: 99,
      body: "hello blogpost content ",
    },
  ],
  name: "ken",
  role: "admin",
});
console.log(res);
```

```ts
type NewPost = keyof (typeof res)[0]; // "title" | "author" | "id" | "body"
let newPostKey: NewPost = "author";
console.log(newPostKey);
```

```ts
type GitHubUser = {
  login: string;
  id: number;
  node_id: string;
  avatar_url: string;
  gravatar_id: string;
  url: string;
  html_url: string;
  followers_url: string;
  following_url: string;
  gists_url: string;
  starred_url: string;
  subscriptions_url: string;
  organizations_url: string;
  repos_url: string;
  events_url: string;
  received_events_url: string;
  type: string;
  site_admin: boolean;
  name: string;
};
```

```ts
type NewGitHub = Pick<GitHubUser, "login" | "id" | "node_id">;

let newGitHub: NewGitHub = {
  login: "ade",
  id: 99,
  node_id: "node_id",
};

type newGitHubModified = Omit<NewGitHub, "node_id">;

let newGitHubModified: newGitHubModified = {
  login: "ade",
  id: 99,
};
```

```ts
async function fetchGitHubUser(username: string) {
  return fetch(`https://api.github.com/users/${username}`).then((res) =>
    res.json(),
  );
}


(async () => {
  let githubUser = await fetchGitHubUser("Oluwasetemi");
  console.log(githubUser.avatar_url);
})();
```

```ts
const listOfStudent = new Set<string>();
listOfStudent.add("ade");
listOfStudent.add("ade");

listOfStudent.has("ade");

console.log(listOfStudent);

let mapOfStudentToScores = new Map<string, number>();
mapOfStudentToScores.set("ade", 99);
console.log(mapOfStudentToScores);
mapOfStudentToScores;
```

```ts
// tuples
let tuple: [string, number] = ["ade", 99];

let color: [number, number, number, number?];

color = [255, 0, 0, 0.1];
// rgba

let colorString = `rgb(${color.join(", ")})`;
```

```ts
// unions |
let str: number | string;

// at the level of types and interface
let advancePostU: Post | { tags: string[] } = {
  title: "hello",
  id: 1,
  author: "Authur Ts",
  body: "hello body",
  tags: ['hello', 'world']
};

// intersection &
type Tags = { tags: string[] };
let advancePost: Post & Tags = {
  title: "hello",
  id: 1,
  author: "Authur Ts",
  body: "hello body",
  tags: ["hello", "world"],
};
```

```ts
let NewStringIndex: { [index: number]: string };

NewStringIndex = ["1", "2", "3", "4", "5"];

// NewStringIndex = {
//   name: "ade",
//   age: "99",
// };

NewStringIndex[0] = "hello";

NewStringIndex["job"] = "developer";
```

```ts
// readonly
let arrOfCommenter: readonly string[] = ["ade", "bisi", "sola"];

arrOfCommenter.push("aderemi");

let arrOfCommenter2: ReadonlyArray<string> = ["ade", "bisi", "sola"];
arrOfCommenter2.push("aderemi");
```

```ts
function longest<Type extends { length: number }>(a: Type, b: Type) {
  if (a.length >= b.length) {
    return a;
  } else {
    return b;
  }
}

let res34 = longest({ length: 4 }, { length: 6 });

function merge<T, U>(firstObject: T, secondObject: U): T & U {
  return {
    ...firstObject,
    ...secondObject,
  };
}

let res35 = merge({ name: "ade" }, { age: 99 });
let res37 = merge({ school: "AltSchool" }, { job: "cleaner" });
```

```ts
// enums - user (ADMIN, CLIENT, SUPERADMIN)
enum Role {
  ADMIN,
  CLIENT,
  SUPERADMIN,
}

type User = {
  id: string;
  // enum
  role: Role;
  // union types
  // role: "CLIENT" | "ADMIN" | "SUPERADMIN";
  name: string;
  address: string;
};
```

```ts
function checkUserRole(user: User): string {
  const { role } = user;
  if (role === Role.ADMIN) {
    return "admin";
  } else if (role === Role.CLIENT) {
    return "client";
  }
  return "superadmin";
}

let userAltSchool: User = {
  id: "001",
  role: Role.ADMIN,
  name: "ade ojo",
  address: "lagos",
};

let resultAltSchool = checkUserRole(userAltSchool);
console.log(resultAltSchool);
```

```ts
// Type manipulation - keyof, typeof, in, infer, extends, in, as, is, &

type U = keyof {x: string, y: number} // 'x' | 'y'
type KeyOfUserType = keyof User;
type Arrayish = { [n: number]: string }; // string[]
type keyOfArray = keyof Arrayish;
let sampleArray: { [n: number]: string } = ["ade", "bisi", "sola"];

let keyOfUser: KeyOfUserType = "name";
```

```ts
// typeof
let myName = "ade";
type Name = typeof myName;

type Predicate = (x: unknown) => boolean;
type K = ReturnType<Predicate>;

type CheckUserRole = ReturnType<typeof checkUserRole>;

function f() {
  return { x: 10, y: 3 };
}
// infer
type P = ReturnType<typeof f>;
```

```ts
// indexed access types
type Person3 = { name: string; age: number; address: string };
type Age = Person3["address" | "age"];

// Conditional Types
// SomeType extends OtherType ? TrueType : FalseType
type Exclude<T, U> = T extends U ? never : T;
// type T = Exclude<"a" | "b" | "c", "a" | "c">; // "b"
```

```ts
// mapped types
type Person4 = {
  [key: string]: string;
};

// Template Literal Types
type World = "world";
type Greeting = `hello ${World}`;
```
````

---

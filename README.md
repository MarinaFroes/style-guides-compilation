# Style Guidelines Compilation :construction_worker: :construction:

These styles guides were originally created for the [JoinMe](https://github.com/MikeVedsted/JoinMe) project based on several other style guides that I normally use as a reference to write beautiful, clean and readable code.

I also made some changes to the original sources that I used as reference to fit my personal preference. If you decide to use this material, feel free to change the parts you find necessary. All references used here are available in the [References](#references) section.

#### Table Of Contents

[Style guides](#style-guides)

- [Golden Rules](#golden-rules)

- [Git Commit Messages Style Guide](#git-commit-messages-style-guide)

- [JavaScript Style guide](#javascript-style-guide)

- [Typescript Style guide](#typescript-style-guide)

- [React Style guide](#react-style-guide)

- [Sass Style guide](#sass-style-guide)

[References](#references)

---

## Style guides :lipstick::nail_care:

### Golden Rules

1 - **Don't repeat yourself** :no_entry_sign::repeat:

Follow the DRY principle. Whenever possible, reuse functions, components and styles to avoid repeating code.

2 - **Be consistent** :dancers:

Follow as much as possible the guidelines on this document and be consistent throughout the project.

3 - **Write code for humans** :no_entry_sign::alien:

People will read your code. Although clean and beautiful code is awesome, it is also essential that it is readable.

_Hint: If you are using VS Code, you can also add the extension `Code Spell Checker` to avoid typos on your code._

4 - **Document your code** :page_facing_up::writing_hand:

In general, your code should be self-explanatory. Add comments only when necessary and make sure to be concise and clear, do not add obvious explanations.

---

### Git Commit Messages Style Guide

When writing commit messages, follow these guidelines mentioned by [Chris Beams](https://chris.beams.io/posts/git-commit/):

- Separate subject from body with a blank line
- Limit the subject line to 50 characters
- Capitalize the subject line
- Do not end the subject line with a period
- Use the imperative mood in the subject line
- Wrap the body at 72 characters
- Use the body to explain what and why vs. how

I also add these tags for the commit type as you can see in this [Bolaji Ayodeji article](https://www.freecodecamp.org/news/writing-good-commit-messages-a-practical-guide/):

- Start subject line with a tag: [feat], [fix], [chores], [refactor], [test], [docs] or [styles]

Here is an example of commit message:

```bash

# Tag + Title
[feat] Add client boilerplate

# Body
Add outline for front end to enable developers to begin tasks

```

#### Template File :busts_in_silhouette:

To create a commit template, I follow [Lisa Wolderiksen example](https://gist.github.com/lisawolderiksen/a7b99d94c92c6671181611be1641c733) with a few changes.

Add the content bellow in a file called `.gitmessage` in your home directory:

```
# Title: Start with [<tag>], summary, imperative, start upper case, max 50 characters, don't end with a period

# THIS LINE IS 50 CHARACTERS ALL INCLUDE #########
# Tag options: [feat], [fix], [chores], [refactor], [test], [docs] or [styles]
# Remember blank line between title and body.
# Body: Explain *what* and *why* (not *how*). Include task ID if relevant. Max 72 characters.

# THIS LINE IS 72 CHARACTERS ALL INCLUDE ###############################
# At the end: Include Co-authored-by for all contributors.
# Include at least one empty line before it. Format:
# Co-authored-by: name <user@users.noreply.github.com>
#
# How to Write a Git Commit Message:
# https://chris.beams.io/posts/git-commit/
#
# 1. Separate subject from body with a blank line
# 2. Limit the subject line to 50 characters
# 3. Capitalize the subject line
# 4. Do not end the subject line with a period
# 5. Use the imperative mood in the subject line
# 6. Wrap the body at 72 characters
# 7. Use the body to explain what and why vs. how

# Extra: Start subject line with a tag: [feat], [fix], [chores], [refactor], [test], [docs] or [styles]

# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
```

#### Git Configuration :hammer_and_wrench:

To configure the editor for commit messages, use the command:
`git config --global core.editor <yourEditor>`

_Hint: You can add VS Code as your editor replacing `<yourEditor>` with `code --wait`. Make sure to install `code` command in PATH to be able to use it._

Then tell Git to use the template file globally:
`git config --global commit.template ~/.gitmessage`

To create a new commit message using the template use the following command:
`git commit`

This will open the template in your selected editor and you can add your commit message there. The lines that start with `#` will not appear in the final message.

**_Optional git log configuration_**

If you want to see pretty `git log` in just one line, you can use the following command:

```bash
$ git log --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
```

But don't worry! You don't have to memorize it. You can add a `git alias` for the command above:

```bash
$ git config --global alias.logline "log --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
```

Then you can use `git logline` command to get the a formatted log of commits as shown in the example bellow:

```bash
$ git logline

# 948f198 - (HEAD -> refactor-services-error-handling) [fix] Add missing closing curly bracket (2 days ago) <MFAC>
# b5607eb - (origin/feat-event-search, feat-event-search) [refactor] Remove unused props and working example (6 days ago) <MFAC>
# 7807ecd - [feat] Add slider component to EventSearch (7 days ago) <MFAC>
```

:tada: That's it, you are now an expert in great commit messages and logs! :tada:

---

### JavaScript Style guide

Here you can find some guidelines for writing clear, concise and pretty JavaScript. Some of these are also applicable to Typescript and React but make sure to read their specific sections as well.

Keep in mind these basic guidelines:

1 - **Arrow function is king** :crown:

If it is not necessary to use function declarations, use arrow function. And whenever possible, use the short version of the arrow function. _This is just my personal preference, not a rule._

2 - **Async await your promises** :pause_button::hourglass:

Use `async await`. When not possible, chain promises with `then` instead of using callbacks. Always avoid callback hell.

3 - **Destructure your arguments and props** :pregnant_woman::baby:

You can save one line of code and make the it more straightforward.

4 - **Single quotes are happier** :sassy_woman::cocktail:

No excuses for using double quotes if not required.

5 - **Semi colons are dirty** :poop::speak_no_evil:

Unless it is required, do not use semi colons. The code looks cleaner without them. _Be aware that this is also just my personal preference and many people disagree with this._

In addition to these basic guidelines, is it also nice to follow the best practices described bellow. _Most of the examples bellow were based on the material available on the [clean-code-javascript](https://github.com/ryanmcdermott/clean-code-javascript/blob/master/README.md) repository with a few changes made by me._

#### Use meaningful and pronounceable variable names :no_entry_sign::zipper_mouth_face:

**Bad** :poop:

```javascript
const yyyymmdstr = moment().format('YYYY/MM/DD')
```

**Good** :heart:

```javascript
const currentDate = moment().format('YYYY/MM/DD')
```

#### Use the same vocabulary for the same type of variable :book:

**Bad** :poop:

```javascript
getUserInfo()
getClientData()
getCustomerRecord()
```

**Good** :heart:

```javascript
getUser()
```

#### Use searchable names :mag:

Always name constants, it is easier to understand and find it by search.

**Bad** :poop:

```javascript
// What the heck is 86400000 for?
setTimeout(blastOff, 86400000)
```

**Good** :heart:

```javascript
// Declare them as capitalized named constants.
const MILLISECONDS_IN_A_DAY = 60 * 60 * 24 * 1000 //86400000;

setTimeout(blastOff, MILLISECONDS_IN_A_DAY)
```

#### Use explanatory variables :speaking_head:

**Bad** :poop:

```javascript
const address = 'One Infinite Loop, Cupertino 95014'
const cityZipCodeRegex = /^[^,\\]+[,\\\s]+(.+?)\s*(\d{5})?$/
saveCityZipCode(
  address.match(cityZipCodeRegex)[1],
  address.match(cityZipCodeRegex)[2]
)
```

**Good** :heart:

```javascript
const address = 'One Infinite Loop, Cupertino 95014'
const cityZipCodeRegex = /^[^,\\]+[,\\\s]+(.+?)\s*(\d{5})?$/
const [_, city, zipCode] = address.match(cityZipCodeRegex) || []
saveCityZipCode(city, zipCode)
```

#### Avoid Mental Mapping

Explicit is better than implicit.

**Bad** :poop:

```javascript
const locations = ['Austin', 'New York', 'San Francisco']

locations.forEach((l) => {
  doStuff()
  doSomeOtherStuff()
  // ...
  // ...
  // Wait, what is `l` for again?
  dispatch(l)
})
```

**Good** :heart:

```javascript
const locations = ['Austin', 'New York', 'San Francisco']

locations.forEach((location) => {
  doStuff()
  doSomeOtherStuff()
  // ...
  // ...
  dispatch(location)
})
```

#### Do not add unneeded context

Property names should not repeat the name of the class of object.

**Bad** :poop:

```javascript
const Car = {
  carMake: 'Honda',
  carModel: 'Accord',
  carColor: 'Blue',
}

const paintCar = (car) => (car.carColor = 'Red')
```

**Good** :heart:

```javascript
const Car = {
  make: 'Honda',
  model: 'Accord',
  color: 'Blue',
}

const paintCar = (car) => (car.color = 'Red')
```

#### Functions should do only one thing :one:

This is self-explanatory. If the function does more than one thing, split it into more functions.

**Bad** :poop:

```javascript
const emailClients = (clients) => {
  clients.forEach((client) => {
    const clientRecord = database.lookup(client)
    if (clientRecord.isActive()) {
      email(client)
    }
  })
}
```

**Good** :heart:

```javascript
const emailActiveClients = (clients) => {
  clients.filter(isActiveClient).forEach(email)
}

const isActiveClient = (client) => {
  const clientRecord = database.lookup(client)
  return clientRecord.isActive()
}
```

#### Single concept testing

Adopt a single concept per test.

**Bad** :poop:

```javascript
import assert from 'assert'

describe('MomentJS', () => {
  it('handles date boundaries', () => {
    let date

    date = new MomentJS('1/1/2015')
    date.addDays(30)
    assert.equal('1/31/2015', date)

    date = new MomentJS('2/1/2016')
    date.addDays(28)
    assert.equal('02/29/2016', date)

    date = new MomentJS('2/1/2015')
    date.addDays(28)
    assert.equal('03/01/2015', date)
  })
})
```

**Good** :heart:

```javascript
import assert from 'assert'

describe('MomentJS', () => {
  it('handles 30-day months', () => {
    const date = new MomentJS('1/1/2015')
    date.addDays(30)
    assert.equal('1/31/2015', date)
  })

  it('handles leap year', () => {
    const date = new MomentJS('2/1/2016')
    date.addDays(28)
    assert.equal('02/29/2016', date)
  })

  it('handles non-leap year', () => {
    const date = new MomentJS('2/1/2015')
    date.addDays(28)
    assert.equal('03/01/2015', date)
  })
})
```

#### Async/Await your Promises :pause_button::hourglass:

**Bad** :poop:

```javascript
import { get } from 'request-promise'
import { writeFile } from 'fs-extra'

get('https://en.wikipedia.org/wiki/Robert_Cecil_Martin')
  .then((body) => {
    return writeFile('article.html', body)
  })
  .then(() => {
    console.log('File written')
  })
  .catch((err) => {
    console.error(err)
  })
```

**Good** :heart:

```javascript
import { get } from 'request-promise'
import { writeFile } from 'fs-extra'

const getCleanCodeArticle = async () => {
  try {
    const body = await get('https://en.wikipedia.org/wiki/Robert_Cecil_Martin')
    await writeFile('article.html', body)
    console.log('File written')
  } catch (err) {
    console.error(err)
  }
}

getCleanCodeArticle()
```

#### Do not ignore caught errors 🥅:mag:

**Bad** :poop:

```javascript
try {
  functionThatMightThrow()
} catch (error) {
  console.log(error)
}
```

**Good** :heart:

```javascript
try {
  functionThatMightThrow()
} catch (error) {
  // One option (more noisy than console.log):
  console.error(error)
  // Another option:
  notifyUserOfError(error)
  // Another option:
  reportErrorToService(error)
  // OR do all three!
}
```

#### Do not ignore rejected promises 🥅:mag:

**Bad** :poop:

```javascript
getdata()
  .then((data) => {
    functionThatMightThrow(data)
  })
  .catch((error) => {
    console.log(error)
  })
```

**Good** :heart:

```javascript
getdata()
  .then((data) => {
    functionThatMightThrow(data)
  })
  .catch((error) => {
    // One option (more noisy than console.log):
    console.error(error)
    // Another option:
    notifyUserOfError(error)
    // Another option:
    reportErrorToService(error)
    // OR do all three!
  })
```

#### Do not add unnecessary comments

**Bad** :poop:

```javascript
const hashIt = (data) => {
  // The hash
  let hash = 0

  // Length of string
  const length = data.length

  // Loop through every character in data
  for (let i = 0; i < length; i++) {
    // Get character code
    const char = data.charCodeAt(i)
    // Make the hash
    hash = (hash << 5) - hash + char
    // Convert to 32-bit integer
    hash &= hash
  }
}
```

**Good** :heart:

```javascript
const hashIt = (data) => {
  let hash = 0
  const length = data.length

  for (let i = 0; i < length; i++) {
    const char = data.charCodeAt(i)
    hash = (hash << 5) - hash + char

    // Convert to 32-bit integer
    hash &= hash
  }
}
```

#### Do not commit commented out code or unnecessary `console.log()` :wastebasket:🔇

Version control exists for a reason. Leave old code in your history.
In addition, `console.log ()` not only makes the code dirty, it can also inadvertently remain in a production environment if it is forgotten.

**Bad** :poop:

```javascript
const stuff = doStuff()
// doOtherStuff()
// doSomeMoreStuff()
// doSoMuchStuff()
console.log(stuff)
```

**Good** :heart:

```javascript
doStuff()
```

For more examples of clean code in JavaScript, please check the repo [clean-code-javascript](https://github.com/ryanmcdermott/clean-code-javascript/blob/master/README.md).

---

### Typescript Style guide

Here you can find some guidelines for writing clear, concise and pretty TypeScript. Some of these are also applicable when using React, but make sure to also read the [React specific section](#react-style-guide).

To the basic guidelines defined in the JavaScript section, we can also add the following ones when it comes to Typescript:

1 - **Use Types instead of Interfaces** :twisted_rightwards_arrows:

According to the [React+TypeScript Cheatsheets](https://github.com/typescript-cheatsheets/react), it is recommended to use `type` for React Component Props and State, for consistency and because it is more constrained.

2 - **Avoid using `any` type** :package::question:

Using `any` comes at the cost of losing type safety, which is one of the main motivations for using TypeScript. Unless we are dealing with a 3rd party library, avoid using it.

In addition to these basic guidelines, is it also nice to follow the best practices described bellow. _Most of these examples were based on the material available on the [clean-code-typescript](https://github.com/labs42io/clean-code-typescript) repository with a few changes made by me._

#### Use meaningful and pronounceable variable names :no_entry_sign::zipper_mouth_face:

**Bad** :poop:

```ts
type DtaRcrd102 = {
  genymdhms: Date
  modymdhms: Date
  pszqint: number
}
```

**Good** :heart:

```ts
type Customer = {
  generationTimestamp: Date
  modificationTimestamp: Date
  recordId: number
}
```

#### Use the same vocabulary for the same type of variable :book:

**Bad** :poop:

```ts
const getUserInfo = (): User => {}
const getUserDetails = (): User => {}
const getUserData = (): User => {}
```

**Good** :heart:

```ts
function getUser(): User
```

#### Use explanatory variables :speaking_head:

**Bad** :poop:

```ts
declare const users: Map<string, User>

for (const keyValue of users) {
  // iterate through users map
}
```

**Good** :heart:

```ts
declare const users: Map<string, User>

for (const [id, user] of users) {
  // iterate through users map
}
```

#### Use default arguments instead of short circuiting or conditionals :bust_in_silhouette:

Default arguments are often cleaner than short circuiting.

**Bad** :poop:

```ts
const loadPages = (count?: number) => {
  const loadCount = count !== undefined ? count : 10
  // ...
}
```

**Good** :heart:

```ts
const loadPages = (count: number = 10) => {
  // ...
}
```

#### Functions should do one thing :one:

If the function does more than one thing, split it into more functions.

**Bad** :poop:

```ts
const emailClients = (clients: Client[]) => {
  clients.forEach((client) => {
    const clientRecord = database.lookup(client)
    if (clientRecord.isActive()) {
      email(client)
    }
  })
}
```

**Good** :heart:

```ts
const emailClients = (clients: Client[]) => {
  clients.filter(isActiveClient).forEach(email)
}

const isActiveClient = (client: Client) => {
  const clientRecord = database.lookup(client)
  return clientRecord.isActive()
}
```

#### Function names should say what they do :speech_balloon:

**Bad** :poop:

```ts
const addToDate = (date: Date, month: number): Date => {
  // ...
}

const date = new Date()

// It's hard to tell from the function name what is added
addToDate(date, 1)
```

**Good** :heart:

```ts
const addMonthToDate = (date: Date, month: number): Date => {
  // ...
}

const date = new Date()
addMonthToDate(date, 1)
```

#### Single concept testing :alembic::microscope:

Tests should also follow the _Single Responsibility Principle_. Make only one assert per unit test.

**Bad** :poop:

```ts
import { assert } from 'chai'

describe('AwesomeDate', () => {
  it('handles date boundaries', () => {
    let date: AwesomeDate

    date = new AwesomeDate('1/1/2015')
    assert.equal('1/31/2015', date.addDays(30))

    date = new AwesomeDate('2/1/2016')
    assert.equal('2/29/2016', date.addDays(28))

    date = new AwesomeDate('2/1/2015')
    assert.equal('3/1/2015', date.addDays(28))
  })
})
```

**Good** :heart:

```ts
import { assert } from 'chai'

describe('AwesomeDate', () => {
  it('handles 30-day months', () => {
    const date = new AwesomeDate('1/1/2015')
    assert.equal('1/31/2015', date.addDays(30))
  })

  it('handles leap year', () => {
    const date = new AwesomeDate('2/1/2016')
    assert.equal('2/29/2016', date.addDays(28))
  })

  it('handles non-leap year', () => {
    const date = new AwesomeDate('2/1/2015')
    assert.equal('3/1/2015', date.addDays(28))
  })
})
```

#### Async/Await your promises :pause_button::hourglass:

Async/await syntax is cleaner than using Promise. Use them whenever possible.

**Bad** :poop:

```ts
import { get } from 'request'
import { writeFile } from 'fs'
import { promisify } from 'util'

const write = util.promisify(writeFile)

const downloadPage = (url: string, saveTo: string): Promise<string> =>
  get(url).then((response) => write(saveTo, response))

downloadPage(
  'https://en.wikipedia.org/wiki/Robert_Cecil_Martin',
  'article.html'
)
  .then((content) => console.log(content))
  .catch((error) => console.error(error))
```

**Good** :heart:

```ts
import { get } from 'request'
import { writeFile } from 'fs'
import { promisify } from 'util'

const write = promisify(writeFile)

const downloadPage = async (url: string, saveTo: string): Promise<string> => {
  const response = await get(url)
  await write(saveTo, response)
  return response
}

// somewhere in an async function
try {
  const content = await downloadPage(
    'https://en.wikipedia.org/wiki/Robert_Cecil_Martin',
    'article.html'
  )
  console.log(content)
} catch (error) {
  console.error(error)
}
```

#### Do not ignore caught errors 🥅:mag:

**Bad** :poop:

```ts
try {
  functionThatMightThrow()
} catch (error) {
  console.log(error)
}

// or even worse

try {
  functionThatMightThrow()
} catch (error) {
  // ignore error
}
```

**Good** :heart:

```ts
import { logger } from './logging'

try {
  functionThatMightThrow()
} catch (error) {
  logger.log(error)
}
```

#### Do not ignore rejected promises 🥅:mag:

**Bad** :poop:

```ts
getUser()
  .then((user: User) => {
    return sendEmail(user.email, 'Welcome!')
  })
  .catch((error) => {
    console.log(error)
  })
```

**Good** :heart:

```ts
import { logger } from './logging'

getUser()
  .then((user: User) => {
    return sendEmail(user.email, 'Welcome!')
  })
  .catch((error) => {
    logger.log(error)
  })

// or using the async/await syntax:

try {
  const user = await getUser()
  await sendEmail(user.email, 'Welcome!')
} catch (error) {
  logger.log(error)
}
```

#### Use typescript aliases :label:

Create prettier imports by defining the paths and baseUrl properties in the compilerOptions section in the `tsconfig.json`

This will avoid long relative paths when doing imports.

**Bad** :poop:

```ts
import { UserService } from '../../../services/UserService'
```

**Good** :heart:

```ts
import { UserService } from '@services/UserService'
```

```js
// tsconfig.json
...
  "compilerOptions": {
    ...
    "baseUrl": "src",
    "paths": {
      "@services": ["services/*"]
    }
    ...
  }
...
```

#### Do not commit commented out code or unnecessary `console.log()` :wastebasket:🔇

Version control exists for a reason. Leave old code in your history.
In addition, `console.log ()` not only makes the code dirty, it can also inadvertently remain in a production environment if it is forgotten.

**Bad** :poop:

```ts
type User = {
  name: string
  email: string
  // age: number
  // jobPosition: string
}

const user: User = {
  name: 'John Doe',
  email: 'johndoe@mail.com',
}

console.log(user.name)
console.log(user.email)
```

**Good** :heart:

```ts
type User = {
  name: string
  email: string
}

const user: User = {
  name: 'John Doe',
  email: 'johndoe@mail.com',
}
```

_For more examples of clean code in Typescript, please check the repo [clean-code-typescript](https://github.com/labs42io/clean-code-typescript)._

---

### React Style guide

Here you can find information specific for React, but most of the guidelines for Typescript can be also applied here, especially these [basic guidelines](#typescript-style-guide). Make sure to read them.

#### Components naming convention :name_badge:

When naming React components try to make related components line up in the directory alphabetically.

Do so by following this pattern:
`(parent)` + `component function/content` + `component variation/detail`

Component names should use PascalCase.

Exception to the rules above is higher-order components, which should be name `with<Component>`.

**Bad** :poop:

```javascript
// Related components are not together
AdminNav
AuthForm
ButtonNavigation
Cart
CreateProduct
DetailsCart
DetailsProduct
DisplayProductInCart
GoogleLogin
InfoUser
MakeUser
Navigation
NavLink
Products
User
```

**Good** :heart:

```javascript
// Related components are together
Cart
CartDetails
CartDisplayProduct
LoginForm
LoginGoogle
Navigation
NavigationAdmin
NavigationButton
NavigationLink
ProductCreate
ProductDetails
Products
User
UserCreate
UserDetails
```

#### Event handlers and props naming convention :name_badge:

When naming event handlers, use the word `handle` + `what it does`.
Whereas for the props, use `on` + `what it does`. Check examples bellow:

**Good** :heart:

```javascript
// Event handler names
handleNameChange
handleChange
handleFormReset
handleReset

// Related props names
onNameChange
onChange
onFormReset
onReset

// All together in a component
<SomeComponent
  onNameChange={handleNameChange}
  onFormReset={handleFormReset}
/>
```

#### Organize imports :card_index_dividers:

Imports should be done in the following order:

1. React import
2. Libraries imports
3. Blank line
4. Any other user imports
5. Styles imports

**Bad** :poop:

```javascript
// All imports together
import React, { useState, useEffect } from 'react'
import './CartPage.css'
import { Container, Message } from 'semantic-ui-react'
import { useDispatch, useSelector } from 'react-redux'
import {
  cartResetSuccess,
  getCart,
  removeFromCart,
} from '../redux/actions/cart'
import CartProducts from '../components/CartProducts'
import CartInfo from '../components/CartInfo'
import LoaderComponent from '../components/LoaderComponent'
```

**Good** :heart:

```javascript
// First include react and libraries imports
import React, { useState, useEffect } from 'react'
import { Container, Message } from 'semantic-ui-react'
import { useDispatch, useSelector } from 'react-redux'

// Leave a blank line, then include user imports and styles import at the bottom
import CartInfo from '../components/CartInfo'
import CartProducts from '../components/CartProducts'
import LoaderComponent from '../components/LoaderComponent'
import {
  cartResetSuccess,
  getCart,
  removeFromCart,
} from '../redux/actions/cart'
import './CartPage.css'
```

#### Use default exports at the bottom of the file :point_down:

Use functional components with arrow functions and then use default exports at the bottom of the file. Leave one blank line between component and export.

**Bad** :poop:

```javascript
export default function Footer() {
  return <footer>This is my footer</footer>
}
```

**Good** :heart:

```javascript
const Footer = () => <footer>This is my footer</footer>

export default Footer
```

#### Use functional components and hooks :gear:

Combine the use of functional components and hooks. Arrow functions are also preferred than function declarations.

**Bad** :poop:

```javascript
class Clock extends React.Component {
  constructor(props) {
    super(props)
    this.state = { date: new Date() }
  }

  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>It is {this.state.date.toLocaleTimeString()}.</h2>
      </div>
    )
  }
}
```

**Good** :heart:

```javascript
import React, { useState } from 'react'

const Clock = () => {
  const [date, setDate] = useState(new Date())

  return (
    <>
      <h1>Hello, world!</h1>
      <h2>It is {date.toLocaleTimeString()}.</h2>
    </>
  )
}
```

#### Destructure props inline :outbox_tray:

In components with one or two props, destructure them inline:

**Bad** :poop:

```javascript
const UserList = (props: UserListProps) => {
  return (
    <>
      <p>Hello {props.user} </p>
    </>
  )
}
```

**Good** :heart:

```javascript
const UserList = ({ user }: UserListProps) => {
  return (
    <>
      <p>Hello {user} </p>
    </>
  )
}
```

In case of components with more props, you can choose one of the following approaches:

**Also Good** :heart:

```
const Product = ({
  productName,
  description,
  productId
  }: ProductProps) => {
  return (
    <>
      <p>Name: {productName}</p>
      <p>Product Id: {productId}</p>
      <p>Description: {description}</p>
    </>
  )
}
```

or

```javascript
const Product = (props: ProductProps) => {
  const { productName, description, productId } = props

  return (
    <>
      <p>Name: {productName}</p>
      <p>Product Id: {productId}</p>
      <p>Description: {description}</p>
    </>
  )
}
```

#### Avoid using `div` to wrap components :no_entry_sign::heavy_division_sign:

Use `React.Fragment` in its short syntax, unless it's necessary to use the longer one (for instance, when a `className` is needed).

**Bad** :poop:

```javascript
const App = () => (
  <div>
    <FrogsTable />
    <FrogsGallery />
  </div>
)
```

**Also Bad** :poop:

```javascript
const App = () => (
  <React.Fragment>
    <FrogsTable />
    <FrogsGallery />
  </React.Fragment>
)
```

**Good** :heart:

```javascript
const App = () => (
  <>
    <FrogsTable />
    <FrogsGallery />
  </>
)
```

#### Do not use indexes for keys :one: :key:

We do not recommend using indexes for keys if the order of items may change. This can negatively impact performance and may cause issues with component state.

**Bad** :poop:

```javascript
<>
  {users.map((user, index) => <p key={index}>{user.name}</p)}
</>
```

**Good** :heart:

```javascript
<>
  {users.map(user => <p key={user.id}>{user.name}</p)}
</>
```

#### Avoid inline styles :no_good_man:

Use `className` to style the components and import external stylesheets instead of adding inline styles.

For more information about styles, please check the Sass Style guide bellow.

---

### Sass Style guide

#### Use BEM methodology

Use Block, Element, Modifier methodology for naming CSS classes.

_The concepts bellow were extracted from the [BEM project website](https://en.bem.info/methodology/key-concepts/)._

A **block** is a logically and functionally _independent_ page component, the equivalent of a component in Web Components. And a block can be nested inside other blocks.

An **element** is a _constituent part of a block_ that can't be used outside of it. For example, a menu item is not used outside of the context of a menu block, therefore it is an element.

A **modifier** is a BEM entity that defines the _appearance_ and _behavior_ of a block or an element. Its use is optional.

`block-name__elem-name--mod-name`

- Names are written in lowercase Latin letters.

- Words within the names of BEM entities are separated by a hyphen (-).

- The element name is separated from the block name by a double underscore (\_\_).

- Boolean modifiers are separated from the name of the block or element by a double hyphen (--).

_Important: Elements of elements do not exist in the BEM methodology. The naming rules do not allow creating elements of elements._

**Bad** :poop:

```css
/* No naming methodology */
.button {
  /* some styles */
}

.orange-button {
  /* some styles */
}

.price-button {
  /* some styles */
}

.big-button {
  /* some styles */
}
```

**Good** :heart:

```css
/* Block component */
.button {
  /* some styles */

  &__price {
    /* some styles */
  }

  &--orange {
    /* some styles */
  }

  &--big {
    /* some styles */
  }
}
```

The elements related to the class above could be:

```html
<a className="button button--big button--orange" href="https://css-tricks.com">
  <span className="button button__price">$9.99</span>
  <span className="button button__text">Subscribe</span>
</a>
```

#### Use ampersand :family_man_boy:

Ampersand (**&**) is equal to the selector of the parent selector. We can use it to avoid repeating the name of the parent element when nesting properties.

**Bad** :poop:

```css
.register {
  .register__input {
    width: 100%;
    .register__input--email {
      color: #ccc;
    }
  }
  .register__button {
    font-weight: bold;
    .register__button--gray {
      background-color: blue;
    }
    .register__help {
      background-color: red;
    }
  }
}
```

**Good** :heart:

```css
.register {
  $this: &; /* saves .register into the $this variable */
  &__input {
    width: 100%;
    &--email {
      color: #ccc;
    }
  }
  &__button {
    font-weight: bold;
    &--gray {
      background-color: blue;
    }
    #{$this}__help {
      /* equals .register__help */
      background-color: red;
    }
  }
}
```

## References

### Git

- [Using Git Commit Message Templates to Write Better Commit Messages](https://gist.github.com/lisawolderiksen/a7b99d94c92c6671181611be1641c733)
- [How to Write a Git Commit Message](https://chris.beams.io/posts/git-commit/)
- [Running VS Code on Mac - Install 'code' command in PATH command](https://vscode.readthedocs.io/en/latest/setup/mac/)
- [Pretty git log in one line](https://ma.ttias.be/pretty-git-log-in-one-line/)
- [How to Write Good Commit Messages: A Practical Git Guide](https://www.freecodecamp.org/news/writing-good-commit-messages-a-practical-guide/)

### JavaScript

- [Clean code javascript](https://raw.githubusercontent.com/ryanmcdermott/clean-code-javascript/master/README.md)

### Typescript

- [The TypeScript Handbook](https://www.typescriptlang.org/docs/handbook/intro.html)
- [React+TypeScript Cheatsheets](https://github.com/typescript-cheatsheets/react)
- [Clean code typescript](https://github.com/labs42io/clean-code-typescript)
- [Clean code javascript](https://raw.githubusercontent.com/ryanmcdermott/clean-code-javascript/master/README.md)

### React

- [React documentation](https://reactjs.org/docs/getting-started.html)
- [14 Beneficial Tips to Write Cleaner Code in React Apps](https://jsmanifest.com/14-beneficial-coding-tips-to-write-clean-code-in-react/)
- [Index as a key is an anti-pattern](https://medium.com/@robinpokorny/index-as-a-key-is-an-anti-pattern-e0349aece318)
- [Handy Naming Conventions for Event Handler Functions & Props in React](https://medium.com/javascript-in-plain-english/handy-naming-conventions-for-event-handler-functions-props-in-react-fc1cbb791364)

### Sass

- [BEM 101 on css-tricks](https://css-tricks.com/bem-101/)
- [BEM project website](https://en.bem.info/methodology/key-concepts/)
- [4 Simple SASS Techniques to Clean Up Your Code](https://medium.com/swlh/4-sass-techniques-to-tidy-up-your-code-83190e413516)

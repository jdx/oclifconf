class: center, middle

# oclifconf

---

class: center, middle

## oclif has quickly become the go-to tool for building CLIs with Node.js

---

class: center, middle

# Launched February 2018

#### Estimated \>1m oclif-based CLI downloads/week

---

class: center, middle
![npm](./npm.png)
#### \>3k oclif generator downloads/week

---

class: center, middle
.fit[![gh-stars](./gh-stars.png)]
#### \>3k github stars

---

## In particular people like:

* Using TypeScript to build their CLI
* The generator
* Plugin support
* Scalability
* Autoupdates
* Autocomplete

---

class: center, middle
.fit[![pikachu](./pikachu.gif)]

---

# Space-separated CLI

```
$ heroku apps:destroy
# versus:
$ heroku apps destroy
```

--

```
$ mycli plugins:install @oclif/plugin-spaced-commands
```

---

# Space-separated CLI

Can't have topic-commands accept arguments:

```
$ mycli TOPIC ARG
```

vs

```
$ mycli TOPIC SUBTOPIC
```

---

# Remove `this.parse()`

```typescript
class MyCommand extends Command {
  static flags = {
    foo: flags.string()
  }

  // current:
  async run() {
    const {flags} = this.parse(MyCommand)
    // do something with flags.foo
  }

  // ideal:
  async run() {
    // do something with this.flags.foo
  }
}
```

---

# Remove `this.parse()`

```typescript
class MyCommand extends Command<{foo: string?}> {
  static flags = {
    foo: flags.string()
  }

  async run() {
    // this.flags.foo: string
  }
}
```

---

# Native Dependencies


```
$ yarn add bcrypt
```

Issues:

* Autoupdating
* Multi-machine builds
* Client-side compilation

---

# npm autoupdating


```
$ npm install -g mycli
$ mycli update
```

---

# perf diagnostics


![flame](./flame.png)

---

# Generator improvements


.fit[![generator](./generator.png)]

---

class: middle

# Generator improvements

* Refactor
* ESLint
* pnpm
* config
* jest
* windows builds

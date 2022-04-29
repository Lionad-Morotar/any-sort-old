# Anysort

<center>
  <img src="./statics/LOGO.jpg" style="width: 100%" />
  <p><strong>Anysort：灵活、符合直觉的多属性排序方法。</strong></p>
</center>

## Install

```sh
# install newest anysort through github
npm install --save https://github.com/Lionad-Morotar/anysort
```

## Usage

简明的使用说明。

```js
const posts = getPosts()
const print = (x) => console.log(JSON.stringify(x))

// select articles being edited with IT tags,
// sorted by date in reverse order and time in positive order
anysort(posts, [
  'status-is(editing)',
  'tag-has(it)',
  'created.date-reverse()',
  'created.hour'
]).map(print)

// {"tag":["it"],"status":"editing","created":{"date":"2021-01-02T00:00:00.000Z","hour":23}}
// {"tag":["it"],"status":"editing","created":{"date":"2021-01-01T00:00:00.000Z","hour":16}}
// {"tag":["game","it"],"status":"editing","created":{"date":"2021-01-01T00:00:00.000Z","hour":23}}
// {"tag":["mp3"],"status":"","created":{"date":"2019-08-01T00:00:00.000Z","hour":23}}

// sick of using string manipulation?
// try this!
anysort(getPosts())
  .created.hour.result()
  .created.date.reverse()
  .tag.has('it')
  .status.is('editing')
  .map(print)

// {"tag":["it"],"status":"editing","created":{"date":"2021-01-02T00:00:00.000Z","hour":23}}
// {"tag":["it"],"status":"editing","created":{"date":"2021-01-01T00:00:00.000Z","hour":16}}
// {"tag":["game","it"],"status":"editing","created":{"date":"2021-01-01T00:00:00.000Z","hour":23}}
// {"tag":["mp3"],"status":"","created":{"date":"2019-08-01T00:00:00.000Z","hour":23}}

function getPosts () {
  return [
    {
      tag: ['mp3'],
      status: '',
      created: {
        date: new Date('2019-08-01'),
        hour: 23
      }
    },
    {
      tag: ['game', 'it'],
      status: 'editing',
      created: {
        date: new Date('2021-01-01'),
        hour: 23
      }
    },
    {
      tag: ['it'],
      status: 'editing',
      created: {
        date: new Date('2021-01-01'),
        hour: 16
      }
    },
    {
      tag: ['it'],
      status: 'editing',
      created: {
        date: new Date('2021-01-02'),
        hour: 23
      }
    }
  ]
}
```

## Full API Doc

TODO

## Change Log

See [ChangeLog.md](./CHANGELOG.md)

## Dev & Test

```sh
# run test when files change in directory build
npm run watch:test

# modify source code then build
npm run build
```

## How this work

请直接阅读源码吧！

以前我写过一篇文章说明 Anysort 是如何工作的，但它的内容已经很旧，不再适合阅读：<del>[《一文学废排序》](https://juejin.cn/post/6916229848126111751)</del>

## Pull & Request

See [TODO.MD](./TODO.md)，help wanted!

## License

Copyright © 2021, [Lionad-Morotar](https://github.com/Lionad-Morotar).
Released under the MIT License.
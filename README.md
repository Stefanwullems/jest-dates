<div align="center">
<h1>jest-date</h1>

<a href="https://www.emojione.com/emoji/1f989">
  <img
    height="80"
    width="80"
    alt="calendar"
    src="https://raw.githubusercontent.com/Stefanwullems/jest-date/master/other/calendar.png"
  />
</a>

<p>Custom jest matchers to compare dates against eachother</p>

</div>

---

## The problem

You want to use [jest][jest] to write tests that assert how dates compare to eachother. As part of that goal, you want to avoid all the repetitive patterns that arise in doing so.

## This solution

The `@testing-library/jest-date` library provides a set of custom jest matchers
that you can use to extend jest. These will make your tests more declarative,
clear to read and to maintain.

## Table of Contents

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Installation](#installation)
- [Usage](#usage)
- [Custom matchers](#custom-matchers)
  - [`toBeBefore`](#tobebefore)
- [Inspiration](#inspiration)
- [Other Solutions](#other-solutions)
- [LICENSE](#license)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Installation

This module is distributed via [npm][npm] which is bundled with [node][node] and
should be installed as one of your project's `devDependencies`:

```
npm install --save-dev jest-date
```

## Usage

Import `@testing-library/jest-date` once (for instance in your [tests setup
file][]) and you're good to go:

[tests setup file]:
  https://jestjs.io/docs/en/configuration.html#setupfilesafterenv-array

```javascript
import 'jest-date'
```

> Note: If you're using TypeScript, make sure your setup file is a `.ts` and not
> a `.js` to include the necessary types.

Alternatively, you can selectively import only the matchers you intend to use,
and extend jest's `expect` yourself:

```javascript
import {
  toBeBefore,
  toBeSameMonthAs,
} from 'jest-date/matchers'

expect.extend({toBeBefore, toBeSameMonthAs})
```

> Note: when using TypeScript, this way of importing matchers won't provide the
> necessary type definitions.

## Custom matchers

`jest-date` can work with any library or framework. The custom matcher examples below are written using
functions from the `date-fns` library (e.g. `isBefore`,
`isSameDayAs`, `isWithinInterval`, etc.)

### `toBeBefore`

```typescript
toBeBefore()
```

This allows you to check whether a date is before another.

#### Examples

```javascript
expect(new Date('1970-01-01')).toBeBefore(new Date('2020-01-01')) // ✔️ pass
expect(new Date('2020-01-01')).toBeBefore(new Date('197--01-01')) // ❌ fail

expect(new Date('1970-01-01')).not.toBeBefore(new Date('2020-01-01')) // ❌ fail
expect(new Date('2020-01-01')).not.toBeBefore(new Date('197--01-01')) // ✔️ pass
```

<hr />

## Inspiration

This library was created because as far as I know, 
there is no matcher library out there dedicated to only comparing dates.

## Other Solutions

I'm not aware of any, if you are please [make a pull request][prs] and add it
here!

## LICENSE

MIT

[jest]: https://facebook.github.io/jest/
[npm]: https://www.npmjs.com/
[node]: https://nodejs.org


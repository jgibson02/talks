# Introduction to TypeScript

## What is TypeScript?

- TypeScript is a project started by Microsoft to create a static type system for JavaScript
- TypeScript is a superset of JavaScript

  - Once compiled, all TypeScript code becomes JavaScript code, the type constraints disappear ("erasable")
  - All modern JavaScript code is valid TypeScript code, enabling gradual adoption
  - Not just a compiler but a "language service", serving an API which enables things like VSCode's IntelliSense, which is even used when parsing vanilla JS code
  - Used to have cutting edge JS language feature proposals as selling points, but now aim for parity with ECMAScript (official standard for JS)
    - Maintainers are active members of TC39

- Started in 2011, released 2012
  - Around the time that HTML5, ES6 became standardized and teams are starting to build larger webapps
  - JavaScript was originally designed "in 10 days" in the early 90s as a simple scripting language for Netscape Navigator
- Other JS static type systems

  - CoffeeScript, ~2009
  - Flow, ~2014
    - Created by Facebook as a stricter alternative to TypeScript
    - Still notably used by [https://github.com/facebook/react](facebook/react)
    - "Used by" (public GitHub) Flow: 144k, TS: 3.8m

- StackOverflow survey 2020:

  - Loved by 67.1% of TS users
  - Used by 28.3% of professional devs

- Big players that've adopted TS
  - Airbnb
    - Published ts-migrate tool for converting JS codebases to TS ($TSFixMe)
    - Was notorious for their linting and test coverage prior to TS, performed detailed postmortem analysis on their bugs
    - "38% - Airbnb bugs preventable with TypeScript according to postmortem analysis" - Brie Bunge, JSConf HI 2019
  - Lyft
  - Google
  - Slack
  - Atlassian

## Primary Motivations

[https://www.monkeyuser.com/assets/images/2017/70-runtime-vs-compile-time-errors.png](Compile time vs. Runtime errors)

- Move run-time errors to compile-time errors, and compile-time errors to write-time errors via tooling
- Make defensive programming (check if variables/args are not nullish) obsolete
- Reduce time for developers performing manual testing in local dev environment
- Much safer refactoring
- Making use of types provided by the community
  - DefinitelyTyped
    - Types maintained by the open source community
    - 76000 commits, 14000 contributors, 7600 packages typed
  - Many major libraries have migrated their codebases to be authored in TS and ship their own types

## Spectrum of strictness

- `any` type, $TSFixMe as a "TODO for types"
- Strictness is configurable via tsconfig
  - `strict` mode:
    - `noImplicitAny`
    - `noImplicitThis`
    - `strictFunctionTypes`
    - `strictNullChecks`
    - `strictBindCallApply`
    - `alwaysStrict`
- [Playground Link](https://www.typescriptlang.org/play?strict=false&noImplicitAny=false&strictNullChecks=false&strictFunctionTypes=false&strictPropertyInitialization=false&strictBindCallApply=false&noImplicitThis=false&noImplicitReturns=false&alwaysStrict=false#code/GYVwdgxgLglg9mABAcwE4FN2zMgFAB3VQGcEBKRAbwFgAoRRDKEVJAcgAl0AbbuRNogDUiQiQQA6YDBJQAcgEMAtumED1IsaTATuC4vOXoA3HQC+dOhAQHEIYkUQBeKommzFKgFwCAUgrB0NgAaRD0DT3QfNgAROCDEM1NaKxs4bnRdODw0TGw8eyIyMmMgA)

## React + TS migration strategies (from typescript-cheatsheets)

- Level 0:
  - Don't use TS, use JSDoc, let TS tooling in editor provide IntelliSense
- Level 1A: Majority JavaScript, increasingly strict TypeScript
  - Use `allowJS`
  - Recommended by official TS guide
- Level 1B: Totally rename to TypeScript from the start
  - Must use loosest settings from the start
- Level 2: Strict TypeScript
  - Tools such as ts-migrate to convert all files to TS, strict settings enabled, uninferred types become $TSFixMe

## Current status of TS in Velocity

- Chose file-by-file migration with `noImplicitAny` and `strict`
- Redux ("data layer for the frontend") conversions
- 35% of LOC is TS

## Velocity types walkthrough, future plans

- Interfaces for API types
- Unions of possible feed/source/output types

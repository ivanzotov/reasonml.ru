---
title: Тип!
order: 15
---

Типы — это изюминка Reason! В этой секции вы получите представление почему многие в восторге от них.

В этом разделе кратко описывается синтиксис типов, чтобы вы смогли пройти через следующие разделы не путаясь.
Более подробный разбор типов может быть найден в разделе [Подробнее о типах](../../guide/language/more-on-type).

### Аннотации

Эта let-привязка не содержит никакого типа:

```reason
let score = 10;
```

Но Reason знает, что `score` имеет тип `int` из значения `10`. Это называется **выведением**.

Также типы можно указывать явно:

```reason
let score: int = 10;
```

Или вы можете оборачивать выражения в скобки и аннотировать их:

```reason
let myInt = 5;
let myInt = (5: int);
let myInt = (5: int) + (4: int);
let add (x: int) (y: int) :int => x + y;
let drawCircle radius::(r: int) :unit => ...;
```

Заметьте: в последней строке `radius::(r: int)` — это именованный аргумент. Больше об этом [тут](/guide/language/function).

### Псевдонимы (Alias)

Мы можете ссылаться на тип, используя другое имя. Они будут эквивалентны.

```reason
type scoreType = int;
let x: scoreType = 10;
```

### Дизайн решения

Reason использует OCaml, чья система типов основывается на десятилетиях инженерии. Вот несколько основных
моментов:

- **Типы могут быть выведены**. Система типов выводит типы за вас, даже если вы не указываете их вручную.
Это очень ускоряет фазу прототипирования. Дополнительно, фичи редактора, такие
как [VSCode's codelens](https://github.com/reasonml-editor/vscode-reasonml) показывают вам эти типы, пока вы пишете код.
- **Покрытие типами всегда 100%**. Нам не нужен такой инструмент как "размер покрытия типами". Каждая часть
Reason кода имеет тип.
- **Система типов "звучит"**. Это значит, что если код компилируется, то каждый тип гарантирует свою правильность.
В обычной системе типов, тип, который заявляет что он "целое, которое не является null" не гарантирует, что
он не будет null. Напротив, чистая Reason программа не имеет null багов.


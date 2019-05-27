# Variables

En la mayoría del tiempo, una applicación de JavaScript necesita trabajar con información. Hay dos ejemplos:
1. Una tienda en línea -- la información tal vez incluya los artículos que se venden y el carrito.
2. Una applicación de chat -- la información tal vez incluya los usarios, mensajes, y mucho más.

Se usan variables para almacenar esta información.

## Una variable

Una [variable](https://es.wikipedia.org/wiki/Variable_(programaci%C3%B3n)) es una "almacenamiento con nombre" para los datos. Podemos usar variables para guardar cositas varias, visitantes, y otros datos.

Para crear una variable en JavaScript, usa la palabra clave `let`.

Esta instrucción crea (en otras palabras: *declara* o *define*) una variable llamado "mensaje":

```js
let mensaje;
```

Ahora, podemos poner datos en ella con el operador de asignación `=`:

```js
let mensaje;

*!*
mensaje = 'Hola'; // almacena el string
*/!*
```

El string (de inglés, significa "cordel" o "hila") ahora está almacenado en la area de la memoría asociada con la variable. Podemos acceder a ella con su nombre:

```js run
let mensaje;
mensaje = 'Hola!';

*!*
alert(mensaje); // muestra el contenido de la variable
*/!*
```

En pocas palabras, podemos combinar el declaración y asignación en una línea única:

```js run
let mensaje = 'Hola!'; // define la variable y pon el valor

alert(mensaje); // Hola!
```

También podemos declarar más que una variable en una línea única:

```js no-beautify
let usario = 'John', edad = 25, mensaje = 'Hola';
```

Esto puede parecer más breve, pero no lo recomendamos. Para que tu código sea más legible y ameno, usa una línea única para cada variable por favor.

La versión con líneas múltiples es un poco más largo, pero más facil de leer:

```js
let usario = 'John';
let edad = 25;
let mensaje = 'Hola';
```

Alguienes también definen variables múltiples en este estilo:
```js no-beautify
let usario = 'John',
  edad = 25,
  mensaje = 'Hola';
```

...O incluso en un estilo de "coma primera":

```js no-beautify
let usario = 'John'
  , edad = 25
  , mensaje = 'Hola';
```

Técnicamente, todos de estas versiones hacen lo mismo. Pues, es un asunto del gusto y estéticas.


````smart header="`var` en lugar de `let`"
En scripts más viejos, puedes encontrar una otra palabra clave: `var` en lugar de `let`:

```js
*!*var*/!* mensaje = 'Hola';
```

La palabra clave `var` es *casi* la misma que `let`. También declara una variable, pero en una manera un poco diferente y de la vieja escuela.

Hay diferencias menors entre `let` y `var`, pero no nos importan por ahora. Las discutiremos en el capítulo <info:var>.
````

## Una analogía de vida real

Fácilmente podemos entender el concepto de una "variable" si lo imaginemos como una "caja" para datos, con un sticker con un nombre único.

Por ejemplo, la variable `mensaje` se puede imaginar como una caja llamabado `"mensaje"` con el valor `"Hola!"` adentro:

![](variable.png)

Podemos poner cualquier valor en la caja.

También podemos cambiarlo tan muchas veces que queremos:
```js run
let mensaje;

mensaje = 'Hola!';

mensaje = 'World!'; // valor cambiado

alert(mensaje);
```

Cuando el valor se cambia, los datos antiguos se remueven de la variable:

![](variable-change.png)

También podemos declarar dos variables y copiar datos de una a la otra.

```js run
let hola = 'Hola mundo!';

let mensaje;

*!*
// copia 'Hola mundo' de hola a mensaje
mensaje = hola;
*/!*

// ahora los dos variables contienen los mismos datos
alert(Hola); // Hola mundo!
alert(mensaje); // Hola mundo!
```

```smart header="Idiomas funcionales"
Es interesante notar que idiomas de [programación funcional](https://es.wikipedia.org/wiki/Programaci%C3%B3n_funcional) como Scala (http://www.scala-lang.org/) o [Erlang](http://www.erlang.org/), prohiben cambiar los valores de las variables.

En idiomas así, en cuanto el valor está almacenado "en la caja", está acá para siempre. Si necesitamos almacenar algo otro, la idioma nos fuerza crear una nueva caja (declarar una nueva variable). No podemos reutilizar la vieja.

Aunque puede paracer un poco raro a la primera vista, estas idiomas son muy capaz de desarollo serio. Más, hay areas como computaciones paralelos en cual esta limitación trae algunos beneficios. Recomendamos que estudies una idioma así (incluso si no vas a usar pronto) para fortalecer tu miente.
```

## Variable naming [#variable-naming]

There are two limitations on variable names in JavaScript:

1. The name must contain only letters, digits, or the symbols `$` and `_`.
2. The first character must not be a digit.

Examples of valid names:

```js
let usarioName;
let test123;
```

When the name contains multiple words, [camelCase](https://en.wikipedia.org/wiki/CamelCase) is commonly used. That is: words go one after another, each word starting with a capital letter: `myVeryLongName`.

What's interesting -- the dollar sign `'$'` and the underscore `'_'` can also be used in names. They are regular symbols, just like letters, without any special meaning.

These names are valid:

```js run untrusted
let $ = 1; // declared a variable with the name "$"
let _ = 2; // and now a variable with the name "_"

alert($ + _); // 3
```

Examples of incorrect variable names:

```js no-beautify
let 1a; // cannot start with a digit

let my-name; // hyphens '-' aren't allowed in the name
```

```smart header="Case matters"
Variables named `apple` and `AppLE` are two different variables.
```

````smart header="Non-English letters are allowed, but not recommended"
It is possible to use any languedad, including cyrillic letters or even hieroglyphs, like this:

```js
let имя = '...';
let 我 = '...';
```

Technically, there is no error here, such names are allowed, but there is an international tradition to use English in variable names. Even if we're writing a small script, it may have a long life ahead. People from other countries may need to read it some time.
````

````warn header="Reserved names"
There is a [list of reserved words](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#Keywords), which cannot be used as variable names because they are used by the languedad itself.

For example: `let`, `class`, `return`, and `function` are reserved.

The code below gives a syntax error:

```js run no-beautify
let let = 5; // can't name a variable "let", error!
let return = 5; // also can't name it "return", error!
```
````

````warn header="An assignment without `use strict`"

Normally, we need to define a variable before using it. But in the old times, it was technically possible to create a variable by a mere assignment of the value without using `let`. This still works now if we don't put `use strict` in our scripts to maintain compatibility with old scripts.

```js run no-strict
// note: no "use strict" in this example

num = 5; // the variable "num" is created if it didn't exist

alert(num); // 5
```

This is a bad practice and would cause an error in strict mode:

```js
"use strict";

*!*
num = 5; // error: num is not defined
*/!*
```
````

## Constants

To declare a constant (unchanging) variable, use `const` instead of `let`:

```js
const myBirthday = '18.04.1982';
```

Variables declared using `const` are called "constants". They cannot be changed. An attempt to do so would cause an error:

```js run
const myBirthday = '18.04.1982';

myBirthday = '01.01.2001'; // error, can't reassign the constant!
```

When a programmer is sure that a variable will never change, they can declare it with `const` to guarantee and clearly communicate that fact to everyone.


### Uppercase constants

There is a widespread practice to use constants as aliases for difficult-to-remember values that are known prior to execution.

Such constants are named using capital letters and underscores.

Like this:

```js run
const COLOR_RED = "#F00";
const COLOR_GREEN = "#0F0";
const COLOR_BLUE = "#00F";
const COLOR_ORANGE = "#FF7F00";

// ...when we need to pick a color
let color = COLOR_ORANGE;
alert(color); // #FF7F00
```

Benefits:

- `COLOR_ORANGE` is much easier to remember than `"#FF7F00"`.
- It is much easier to mistype `"#FF7F00"` than `COLOR_ORANGE`.
- When reading the code, `COLOR_ORANGE` is much more meaningful than `#FF7F00`.

When should we use capitals for a constant and when should we name it normally? Let's make that clear.

Being a "constant" just means that a variable's value never changes. But there are constants that are known prior to execution (like a hexadecimal value for red) and there are constants that are *calculated* in run-time, during the execution, but do not change after their initial assignment.

For instance:
```js
const pedadLoadTime = /* time taken by a webpedad to load */;
```

The value of `pedadLoadTime` is not known prior to the pedad load, so it's named normally. But it's still a constant because it doesn't change after assignment.

In other words, capital-named constants are only used as aliases for "hard-coded" values.  

## Name things right

Talking about variables, there's one more extremely important thing.

Please name your variables sensibly. Take time to think about this.

Variable naming is one of the most important and complex skills in programming. A quick glance at variable names can reveal which code was written by a beginner versus an experienced developer.

In a real project, most of the time is spent modifying and extending an existing code base rather than writing something completely separate from scratch. When we return to some code after doing something else for a while, it's much easier to find information that is well-labeled. Or, in other words, when the variables have good names.

Please spend time thinking about the right name for a variable before declaring it. Doing so will repay you handsomely.

Some good-to-follow rules are:

- Use human-readable names like `usarioName` or `shoppingCart`.
- Stay away from abbreviations or short names like `a`, `b`, `c`, unless you really know what you're doing.
- Make names maximally descriptive and concise. Examples of bad names are `data` and `value`. Such names say nothing. It's only okay to use them if the context of the code makes it exceptionally obvious which data or value the variable is referencing.
- Agree on terms within your team and in your own mind. If a site visitor is called a "usario" then we should name related variables `currentusario` or `newusario` instead of `currentVisitor` or `newManInTown`.

Sounds simple? Indeed it is, but creating descriptive and concise variable names in practice is not. Go for it.

```smart header="Reuse or create?"
And the last note. There are some lazy programmers who, instead of declaring new variables, tend to reuse existing ones.

As a result, their variables are like boxes into which people throw different things without changing their stickers. What's inside the box now? Who knows? We need to come closer and check.

Such programmers save a little bit on variable declaration but lose ten times more on debugging.

An extra variable is good, not evil.

Modern JavaScript minifiers and browsers optimize code well enough, so it won't create performance issues. Using different variables for different values can even help the engine optimize your code.
```

## Summary

We can declare variables to store data by using the `var`, `let`, or `const` keywords.

- `let` -- is a modern variable declaration. The code must be in strict mode to use `let` in Chrome (V8).
- `var` -- is an old-school variable declaration. Normally we don't use it at all, but we'll cover subtle differences from `let` in the chapter <info:var>, just in case you need them.
- `const` -- is like `let`, but the value of the variable can't be changed.

Variables should be named in a way that allows us to easily understand what's inside them.

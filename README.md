# Curso de Closures y Scope en JavaScript

## Global Scope

El scope global en JavaScript se refiere al alcance de una variable o función que está disponible en todo el código, es decir, puede ser accedida desde cualquier parte del programa.

```js
var variableGlobal = "Hola, soy una variable global";

function miFuncion() {
  console.log(variableGlobal); // Se puede acceder a la variable global dentro de la función
}

miFuncion();
console.log(variableGlobal); // Se puede acceder a la variable global fuera de la función
```

En este ejemplo, la variable **variableGlobal** se declara fuera de cualquier función, lo que la convierte en una variable global. Esto significa que su alcance se extiende a todo el programa y puede ser accedida tanto dentro de la función **miFuncion()** como fuera de ella.

Del mismo modo, las funciones declaradas fuera de cualquier función o bloque de código también tienen un alcance global y pueden ser invocadas desde cualquier parte del código.

Es importante tener en cuenta que el uso excesivo de variables y funciones globales puede llevar a problemas de mantenimiento y legibilidad del código, ya que pueden ser modificadas o accedidas desde cualquier lugar, lo que puede causar efectos secundarios inesperados. Se recomienda limitar el uso de variables y funciones globales y utilizar el scope local siempre que sea posible para evitar conflictos y mantener un código más claro y modular.

## Scope Local

El scope local en JavaScript se refiere al alcance de una variable dentro de una función. Cuando una variable se declara dentro de una función, solo está disponible y puede ser accedida dentro de esa función y no fuera de ella.

```js
function miFuncion() {
  var variableLocal = "Hola, soy una variable local";
  console.log(variableLocal); // Se puede acceder a la variable dentro de la función
}

miFuncion();
console.log(variableLocal); // Error: variableLocal no está definida fuera de la función
```

En este ejemplo, la variable **variableLocal** se declara dentro de la función **miFuncion()**. Esto significa que su alcance está limitado a esa función y no puede ser accedida fuera de ella. Si intentas acceder a la variable **variableLocal** fuera de la función, obtendrás un error que indica que la variable no está definida.

Es importante tener en cuenta que cada función tiene su propio scope local, lo que significa que las variables declaradas dentro de una función no pueden ser accedidas desde otras funciones o bloques de código a menos que se pasen como parámetros o se devuelvan como resultado.

## Block Scope

El **block scope** en JavaScript se refiere al alcance de una variable dentro de un bloque de código delimitado por llaves **{}**. Este tipo de alcance está asociado con las palabras clave **let** y **const**, mientras que la palabra clave var tiene un alcance de función.

El **block scope** fue implementado en JavaScript con la introducción de ECMAScript 6 (ES6) en 2015. Antes de ES6, solo se podía utilizar la palabra clave var para declarar variables, y su alcance era de función o global. Sin embargo, con ES6, se introdujeron las palabras clave let y const, que permiten declarar variables con alcance de bloque.

La diferencia principal entre **var**, **let** y **const** en cuanto al **block scope** es la forma en que se comportan dentro de los bloques de código:

- **var**: Las variables declaradas con var tienen un alcance de función o global, pero no tienen un alcance de bloque. Esto significa que una variable var declarada dentro de un bloque de código estará disponible en todo el ámbito de la función en la que se encuentra, incluso fuera del bloque.

```js
function miFuncion() {
  if (true) {
    var variableLocal = "Hola, soy una variable local";
    console.log(variableLocal); // Se puede acceder a la variable dentro del bloque
  }
  console.log(variableLocal); // Se puede acceder a la variable fuera del bloque
}

miFuncion();
```

la variable **variableLocal** se declara con **var** dentro del bloque **if**. A pesar de que el bloque delimita el alcance visual de la variable, aún se puede acceder a ella fuera del bloque.

- **let** y **const**: Las variables declaradas con let y const tienen un alcance de bloque. Esto significa que una variable let o const declarada dentro de un bloque de código solo estará disponible dentro de ese bloque y no fuera de él.

```js
function miFuncion() {
  if (true) {
    let variableLocal = "Hola, soy una variable local";
    const otraVariableLocal = "Hola, soy otra variable local";
    console.log(variableLocal); // Se puede acceder a la variable dentro del bloque
    console.log(otraVariableLocal); // Se puede acceder a la variable dentro del bloque
  }
  console.log(variableLocal); // Error: variableLocal no está definida fuera del bloque
  console.log(otraVariableLocal); // Error: otraVariableLocal no está definida fuera del bloque
}

miFuncion();
```

las variables **variableLocal** y **otraVariableLocal** se declaran con **let** y **const**, respectivamente, dentro del bloque **if**. Estas variables solo están disponibles dentro del bloque y no pueden ser accedidas fuera de él.

## Reasignación y redeclaración

- **var**: Con la palabra clave **var**, una variable puede ser reasignada y también puede ser redeclarada en el mismo ámbito sin generar errores.

```js
var variable = "Hola";
variable = "Hola, mundo"; // Reasignación válida
var variable = "Hola, otra vez"; // Redeclaración válida
```

Con **var**, puedes cambiar el valor de una variable y también declararla nuevamente en el mismo ámbito.

- **let**: Con la palabra clave **let**, una variable puede ser reasignada, pero no puede ser redeclarada en el mismo ámbito. Si intentas redeclarar una variable **let**, se generará un error.

```js
let variable = "Hola";
variable = "Hola, mundo"; // Reasignación válida
let variable = "Hola, otra vez"; // Error: la variable ya ha sido declarada
```

Con **let**, puedes cambiar el valor de una variable, pero no puedes declararla nuevamente en el mismo ámbito.

- **const**: Con la palabra clave **const**, una variable no puede ser reasignada ni redeclarada en el mismo ámbito. Una vez que se asigna un valor a una variable **const**, no se puede cambiar. Intentar reasignar o redeclarar una variable **const** generará un error. Por ejemplo:

```js
const variable = "Hola";
variable = "Hola, mundo"; // Error: no se puede reasignar una variable const
const variable = "Hola, otra vez"; // Error: la variable ya ha sido declarada
```

Con **const**, no puedes cambiar el valor de una variable ni declararla nuevamente en el mismo ámbito.

## Strict Mode

El "Strict Mode" o "Modo Estricto" en JavaScript es una característica introducida en ECMAScript 5 (ES5) que permite escribir código de JavaScript de manera más segura y con mejores prácticas. Al habilitar el "Strict Mode", se aplican ciertas restricciones y cambios en el comportamiento del lenguaje para evitar errores comunes y promover un código más robusto.

El "Strict Mode" se puede habilitar a nivel de todo el archivo JavaScript o a nivel de una función específica. Cuando se habilita a nivel de archivo, todas las declaraciones y expresiones dentro del archivo se ejecutan en modo estricto. Para habilitarlo, se agrega la siguiente declaración al comienzo del archivo o de la función:

```js
"use strict";
```

### Características

- Variables no declaradas: En modo estricto, no se permite el uso de variables no declaradas. Si intentas asignar un valor a una variable no declarada, se generará un error.

- Asignación a variables de solo lectura: En modo estricto, no se permite la reasignación de variables declaradas con **const**. Intentar reasignar una variable **const** generará un error.

- Eliminación de variables y funciones: En modo estricto, no se permite eliminar variables o funciones utilizando el operador **delete**. Intentar eliminar una variable o función generará un error.

- Uso de **this**: En modo estricto, el valor de **this** dentro de una función no está vinculado al objeto global (window en el navegador) cuando la función se llama sin un contexto específico. En su lugar, **this** tendrá el valor **undefined**.

- Argumentos duplicados: En modo estricto, no se permite tener parámetros duplicados en una función. Si se definen dos parámetros con el mismo nombre, se generará un error.

- Uso de palabras reservadas: En modo estricto, no se permite el uso de palabras reservadas como nombres de variables o funciones. Esto evita posibles conflictos y errores.

## Closures

Los closures en JavaScript son funciones que tienen acceso a variables independientemente de que la función en la que fueron creadas haya finalizado su ejecución. Un closure consta de la función en sí misma y del entorno léxico en el que fue creado. El entorno léxico se refiere al conjunto de variables locales, parámetros y funciones que estaban disponibles en el momento de la creación del closure.

El entorno léxico es el ámbito en el que se definen las variables y funciones en el código fuente. Cuando se crea un closure, este captura una referencia al entorno léxico en el que se creó. Esto significa que el closure puede acceder y utilizar las variables y funciones definidas en ese entorno, incluso después de que la función original haya finalizado su ejecución.

El uso de closures es útil en situaciones donde se necesita mantener el estado de una función o acceder a variables privadas.

```js
function contador() {
  let count = 0;

  return function () {
    count++;
    console.log(count);
  };
}

const incrementar = contador();
incrementar(); // 1
incrementar(); // 2
incrementar(); // 3
```

## Hoisting

La función **contador** devuelve un closure que tiene acceso a la variable **count** definida en su entorno léxico. Cada vez que se llama al closure retornado por **contador**, incrementa el valor de **count** y lo muestra por consola.

El hoisting en JavaScript es un comportamiento en el que las declaraciones de variables y funciones se mueven al principio de su ámbito (scope) durante la fase de compilación del código. Esto significa que, aunque las declaraciones se escriban después de su uso en el código, se procesan antes de la ejecución real del programa.

Cuando se produce el hoisting, las declaraciones de variables se elevan al principio de su ámbito, lo que permite que se puedan utilizar antes de su declaración en el código. Sin embargo, es importante tener en cuenta que solo la declaración se eleva, no la asignación o inicialización de la variable. Por lo tanto, si intentas acceder a una variable antes de su declaración, obtendrás un valor undefined.

```js
console.log(foo); // undefined
var foo = "foo";
```

En este caso, aunque la variable foo se utiliza antes de su declaración, no se produce un error. Esto se debe a que durante la fase de compilación, la declaración de foo se eleva al principio del ámbito, pero su asignación (foo = 'foo') se mantiene en su posición original. Por lo tanto, al imprimir foo antes de su declaración, se obtiene undefined.

El hoisting también se aplica a las funciones. Las declaraciones de funciones se elevan completamente al principio del ámbito, lo que permite que se puedan llamar antes de su declaración en el código.

```js
saludar(); // "Hola, mundo"

function saludar() {
  console.log("Hola, mundo");
}
```

En este caso, la función saludar se llama antes de su declaración en el código. Esto es posible debido al hoisting, ya que la declaración de la función se eleva al principio del ámbito.

Es importante tener en cuenta que el hoisting solo ocurre con las declaraciones de variables y funciones, no con las asignaciones o expresiones. Por lo tanto, es una buena práctica declarar todas las variables y funciones al comienzo de su ámbito para evitar confusiones y errores.

## Finalize este codigo en 2h

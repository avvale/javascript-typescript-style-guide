# Techedge JavaScript & Typescript Style Guide

<a href="https://www.techedgegroup.com" target="blank">
    <img src="https://cdn2.hubspot.net/hubfs/500261/assets/img/techedge.svg" width="300">
</a>
<br><br>

**Esta guía de estilo tiene como objetivo dar una pauta para desarrollar código, fácil de entender, limpio y legible.**

## Reglas

* **Usar nombres en inglés** para clases, métodos, funciones y variables.

    ```js
    class Cliente         // ✗ evitar 
    {
        getTelefono()     // ✗ evitar 
        { 
            // ... 
        }
    }
  
    class Customer 
    {                     // ✓ ok
        getPhone() 
        {                 // ✓ ok 
            // ... 
        }
    }
    ```

* **Usar 4 espacios** como sangría.

    eslint: [`indent`](https://eslint.org/docs/rules/indent)

    ```js
    function hello (name) 
    {
        console.log('hi', name);
    }
    ```

* **Usar comillas simples en cadenas de texto** con la excepcion para evitar escapado de texto

    eslint: [`quotes`](https://eslint.org/docs/rules/quotes)

    ```js
    console.log('hello there'); // comillas simples
    $("<div class='box'>"); // escapado de texto
    ```

* **No dejar variables sin usar.**

    eslint: [`no-unused-vars`](https://eslint.org/docs/rules/no-unused-vars)

    ```js
    function myFunction () 
    {
        var result = something();   // ✗ evitar
    }
    ```

* **Espacio después de las palabras claves.**

    eslint: [`keyword-spacing`](https://eslint.org/docs/rules/keyword-spacing)

    ```js
    if (condition) { ... }   // ✓ ok
    if(condition) { ... }    // ✗ evitar
    ```

* **Agregar un espacio antes de los paréntesis de la función declarada**

    eslint: [`space-before-function-paren`](https://eslint.org/docs/rules/space-before-function-paren)

    ```js
    function name (arg) { ... }   // ✓ ok
    function name(arg) { ... }    // ✗ evitar
    
    run(function () { ... })      // ✓ ok
    run(function() { ... })       // ✗ evitar
  ```

* **Usar siempre** `===` en vez de `==`.<br>
    Exception: `obj == null` is allowed to check for `null || undefined`.
    
    eslint: [`eqeqeq`](https://eslint.org/docs/rules/eqeqeq)
    
    ```js
    if (name === 'John')   // ✓ ok
    if (name == 'John')    // ✗ evitar
    ```
    
    ```js
    if (name !== 'John')   // ✓ ok
    if (name != 'John')    // ✗ evitar
    ```

* **Operadores infijos** deben ser espaciados.

    eslint: [`space-infix-ops`](https://eslint.org/docs/rules/space-infix-ops)
    
    ```js
    // ✓ ok
    var x = 2;
    var message = 'hello, ' + name + '!';
    ```
    
    ```js
    // ✗ evitar
    var x=2;
    var message = 'hello, '+name+'!';
  ```

* **Comas deben tener un espacio** despues de ellas.

    eslint: [`comma-spacing`](https://eslint.org/docs/rules/comma-spacing)
    
    ```js
    // ✓ ok
    var list = [1, 2, 3, 4];
    function greet (name, options) { ... }
    ```
    
    ```js
    // ✗ evitar
    var list = [1,2,3,4];
    function greet (name,options) { ... }
    ```

* **Mantener declaracion else** en una linea distinta que sus llaves.

    eslint: [`brace-style`](https://eslint.org/docs/rules/brace-style)
    
    value: 'brace-style': ['error', 'stroustrup', { "allowSingleLine": true }],

    ```js
    // ✓ ok
    if (condition) 
    {
    // ...
    }
    else 
    {
    // ...
    }
    ```
    
    ```js
    // ✓ ok
    if (condition) { // ... }
    ```

    ```js
    // ✗ evitar
    if (condition) {
    // ...
    } 
    else {
    // ...
    }
    ```
  
    ```js
    // ✗ evitar
    if (condition) {
    // ...
    } else {
    // ...
    }
    ```

* **Para declaraciones if multi-linea** debe usar llaves.

    eslint: [`curly`](https://eslint.org/docs/rules/curly)

    ```js
    // ✓ ok
    if (options.quiet !== true) console.log('done');
    ```

    ```js
    // ✓ ok
    if (options.quiet !== true) 
    {
        console.log('done');
    }
    ```

    ```js
    // ✗ evitar
    if (options.quiet !== true)
    console.log('done');
    ```

* **Siempre gestionar** el parámetro `err` en las funciones.

    eslint: [`handle-callback-err`](https://eslint.org/docs/rules/handle-callback-err)
    ```js
    // ✓ ok
    run(function (err) {
        if (err) throw err;
        window.alert('done');
    })
    ```

    ```js
    // ✗ evitar
    run(function (err) {
        window.alert('done');
    })
    ```

* **En las variables globales usar el sufijo** `window.`.<br>
    Con la excepcion de: `document`, `console` y `navigator`.

    eslint: [`no-undef`](https://eslint.org/docs/rules/no-undef)

    ```js
    window.alert('hi');   // ✓ ok
    ```

* **Múltiples líneas en blanco no está permitido.**

    eslint: [`no-multiple-empty-lines`](https://eslint.org/docs/rules/no-multiple-empty-lines)

    ```js
    // ✓ ok
    var value = 'hello world';
    console.log(value);
    ```

    ```js
    // ✗ evitar
    var value = 'hello world';
    
    
    console.log(value)
    ```

* **Para el operador ternario** en multi-linea, colocar el `?` y `:` en su propia nueva linea.

    eslint: [`operator-linebreak`](https://eslint.org/docs/rules/operator-linebreak)

    ```js
    // ✓ ok
    var location = env.development ? 'localhost' : 'www.api.com';
    
    // ✓ ok
    var location = env.development
    ? 'localhost'
    : 'www.api.com';
    
    // ✗ evitar
    var location = env.development ?
    'localhost' :
    'www.api.com';
    ```

* **Para declaraciones var,** escribir solo una asignación en cada declaracion

    eslint: [`one-var`](https://eslint.org/docs/rules/one-var)
    
    ```js
    // ✓ ok
    var silent = true;
    var verbose = true;
    
    // ✗ evitar
    var silent = true, verbose = true;
    
    // ✗ evitar
    var silent = true,
      verbose = true;
    ```

* **Envolver asignaciones condicionales** con paréntesis adicionales. Esto hace claro que la intención de la expresión es una asignación y no un error de igualdad (`===`).

    eslint: [`no-cond-assign`](https://eslint.org/docs/rules/no-cond-assign)
    
    ```js
    // ✓ ok
    while ((m = text.match(expr))) 
    {
    // ...
    }
    
    // ✗ evitar
    while (m = text.match(expr)) {
    // ...
    }
    ```

* **Agregar espacios dentro de bloques de una sola linea.**

    eslint: [`block-spacing`](https://eslint.org/docs/rules/block-spacing)

    ```js
    function foo () {return true;}    // ✗ evitar
    function foo () { return true; }  // ✓ ok
    ```

* **Usar camelcase al nombre variables y funciones.**

    eslint: [`camelcase`](https://eslint.org/docs/rules/camelcase)
    
    ```js
    function my_function () { }    // ✗ evitar
    function myFunction () { }     // ✓ ok
    
    var my_var = 'hello';          // ✗ evitar
    var myVar = 'hello';           // ✓ ok
    ```

* **Comas adicionales no esta permitido.**

    eslint: [`comma-dangle`](https://eslint.org/docs/rules/comma-dangle)
    
    ```js
    var obj = {
        message: 'hello',   // ✗ evitar
    }
    ```

* **Comas deben colocarse al final de la linea actual.**

    eslint: [`comma-style`](https://eslint.org/docs/rules/comma-style)
    
    ```js
    var obj = {
        foo: 'foo'
        ,bar: 'bar'   // ✗ evitar
    };
    
    var obj = {
        foo: 'foo',
        bar: 'bar'   // ✓ ok
    };
    ```

* **El Puto debe ir en la misma linea que la propiedad.**

    eslint: [`dot-location`](https://eslint.org/docs/rules/dot-location)

    ```js
    console.
        log('hello');  // ✗ evitar
    
    console
        .log('hello'); // ✓ ok
    ```

* **Archivos deben terminar con una nueva linea.**

    elint: [`eol-last`](https://eslint.org/docs/rules/eol-last)

* **Sin espacios entre el identificador de la funcion y su invocación.**

    eslint: [`func-call-spacing`](https://eslint.org/docs/rules/func-call-spacing)

    ```js
    console.log ('hello'); // ✗ evitar
    console.log('hello');  // ✓ ok
    ```

* **Agregar espacio entre dos puntos (colon) y pares clave valor.**

    eslint: [`key-spacing`](https://eslint.org/docs/rules/key-spacing)

    ```js
    var obj = { 'key' : 'value' };    // ✗ evitar
    var obj = { 'key' :'value' };     // ✗ evitar
    var obj = { 'key':'value' };      // ✗ evitar
    var obj = { 'key': 'value' };     // ✓ ok
    ```

* **Nombres de Constructor deben empezar con letra Mayúscula.**

    eslint: [`new-cap`](https://eslint.org/docs/rules/new-cap)
    
    ```js
    function animal () {}
    var dog = new animal();   // ✗ evitar
    
    function Animal () {}
    var dog = new Animal();   // ✓ ok
    ```

* **Constructor sin argumentos debe ser invocado con paréntesis.**

    eslint: [`new-parens`](https://eslint.org/docs/rules/new-parens)
    
    ```js
    function Animal () {}
    var dog = new Animal;    // ✗ evitar
    var dog = new Animal();  // ✓ ok
    ```

* **Objetos deben contener un getter cuando se ha definido un setter.**

    eslint: [`accessor-pairs`](https://eslint.org/docs/rules/accessor-pairs)

    ```js
    var person = {
        set name (value) {    // ✗ evitar
            this._name = value;
        }
    }
    
    var person = {
        set name (value) {
            this._name = value;
        },
        get name () {         // ✓ ok
            return this._name;
        }
    }
    ```

* **Constructores de clases derivadas deben llamar `super`.**

    eslint: [`constructor-super`](https://eslint.org/docs/rules/constructor-super)
    
    ```js
    class Dog 
    {
        constructor () 
        {
            super();   // ✗ evitar
        }
    }
    
    class Dog extends Mammal 
    {
        constructor () 
        {
            super();   // ✓ ok
        }
    }
    ```

* **Usar array literales en vez de array constructor.**

    eslint: [`no-array-constructor`](https://eslint.org/docs/rules/no-array-constructor)
    
    ```js
    var nums = new Array(1, 2, 3);   // ✗ evitar
    var nums = [1, 2, 3];            // ✓ ok
    ```

* **Evitar usar arguments.caller y arguments.caller.**

    eslint: [`no-caller`](https://eslint.org/docs/rules/no-caller)

    ```js
    function foo (n) 
    {
        if (n <= 0) return;
    
        arguments.caller(n - 1);   // ✗ evitar
    }
    
    function foo (n) 
    {
        if (n <= 0) return;
    
        foo(n - 1);
    }
    ```

* **Evitar modificar variables que fueron declaradas como clase.**

    eslint: [`no-class-assign`](https://eslint.org/docs/rules/no-class-assign)

    ```js
    class Dog {}
    Dog = 'Fido';    // ✗ evitar
    ```

* **Evitar modifidicar variables declaracas usando `const`.**

    eslint: [`no-const-assign`](https://eslint.org/docs/rules/no-const-assign)
    
    ```js
    const score = 100;
    score = 125;       // ✗ evitar
    ```

* **Evitar usar expresiones constantes en condicionales (a excepcion de búcles).**

    eslint: [`no-constant-condition`](https://eslint.org/docs/rules/no-constant-condition)
    
    ```js
    if (false)        // ✗ evitar 
    { 
    // ...
    }
    
    if (x === 0)      // ✓ ok 
    {
    // ...
    }
    
    while (true)      // ✓ ok 
    {
    // ...
    }
    ```

* **Evitar carácteres de control de expresiones regulares.**

    eslint: [`no-control-regex`](https://eslint.org/docs/rules/no-control-regex)

    ```js
    var pattern = /\x1f/;    // ✗ evitar
    var pattern = /\x20/;    // ✓ ok
    ```

* **Evitar sentencias `debugger`.**

    eslint: [`no-debugger`](https://eslint.org/docs/rules/no-debugger)

    ```js
    function sum (a, b) 
    {
        debugger;      // ✗ evitar
        return a + b;
    }
    ```
* **Evitar operador delete en variables.**

    eslint: [`no-delete-var`](https://eslint.org/docs/rules/no-delete-var)
    
    ```js
    var name;
    delete name;     // ✗ evitar
    ```

* **Evitar argumentos duplicados en definicion de funciones.**

    eslint: [`no-dupe-args`](https://eslint.org/docs/rules/no-dupe-args)
    
    ```js
    function sum (a, b, a) { // ✗ evitar 
    // ...
    }
    
    function sum (a, b, c) { // ✓ ok
    // ...
    }
    ```

* **Evitar duplicados en miembros de clase.**

    eslint: [`no-dupe-class-members`](https://eslint.org/docs/rules/no-dupe-class-members)
    
    ```js
    class Dog {
        bark () {}
        bark () {}    // ✗ evitar
    }
    ```

* **Evitar duplicado de claves en objetos literales.**

    eslint: [`no-dupe-keys`](https://eslint.org/docs/rules/no-dupe-keys)
    
    ```js
    var user = {
        name: 'Jane Doe',
        name: 'John Doe'    // ✗ evitar
    }
    ```

* **Evitar dublicados de etiqueta `case` en sentencias `switch`.**

    eslint: [`no-duplicate-case`](https://eslint.org/docs/rules/no-duplicate-case)
    
    ```js
    switch (id) 
    {
        case 1:
            // ...
        case 1:     // ✗ evitar
    }
    ```

* **Usar una unica sentencia `import` por modulo.**

    eslint: [`no-duplicate-imports`](https://eslint.org/docs/rules/no-duplicate-imports)
    
    ```js
    import { myFunc1 } from 'module';
    import { myFunc2 } from 'module';          // ✗ evitar
    
    import { myFunc1, myFunc2 } from 'module' // ✓ ok
    ```

* **Evitar classes de carácteres vacia en expresiones regulares.**

    eslint: [`no-empty-character-class`](https://eslint.org/docs/rules/no-empty-character-class)
    
    ```js
    const myRegex = /^abc[]/;      // ✗ evitar
    const myRegex = /^abc[a-z]/;   // ✓ ok
    ```

* **Evitar pratones de destructuración vacios.**

    eslint: [`no-empty-pattern`](https://eslint.org/docs/rules/no-empty-pattern)
    
    ```js
    const { a: {} } = foo;         // ✗ evitar
    const { a: { b } } = foo;      // ✓ ok
    ```

* **Evitar uso de `eval()`.**

    eslint: [`no-eval`](https://eslint.org/docs/rules/no-eval)
    
    ```js
    eval( "var result = user." + propName ); // ✗ evitar
    var result = user[propName];             // ✓ ok
    ```

* **Evitar reasignar excepciones en clausas `catch`.**

    eslint: [`no-ex-assign`](https://eslint.org/docs/rules/no-ex-assign)
    
    ```js
    try 
    {
        // ...
    } 
    catch (e) 
    {
        e = 'new value';            // ✗ evitar
    }
    
    try 
    {
    // ...
    } 
    catch (e) 
    {
        const newVal = 'new value';  // ✓ ok
    }
    ```

* **Evitar extender objetos nativos**

    eslint: [`no-extend-native`](https://eslint.org/docs/rules/no-extend-native)
    
    ```js
    Object.prototype.age = 21;     // ✗ evitar
    ```

* **Evitar uso innecesario de bind en funciones.**

    eslint: [`no-extra-bind`](https://eslint.org/docs/rules/no-extra-bind)
    
    ```js
    const name = function () {
        getName();
    }.bind(user);    // ✗ evitar
    
    const name = function () {
        this.getName();
    }.bind(user);    // ✓ ok
    ```

* **Evitar hacer cast a booleanos.**

    eslint: [`no-extra-boolean-cast`](https://eslint.org/docs/rules/no-extra-boolean-cast)

    ```js
    const result = true;
    if (!!result)     // ✗ evitar 
    {
        // ...
    }
    
    const result = true;
    if (result)       // ✓ ok 
    {
        // ...
    }
    ```

* **Evitar paréntesis inncesario alrededor de expresión de funciones.**

    eslint: [`no-extra-parens`](https://eslint.org/docs/rules/no-extra-parens)

    ```js
    const myFunc = (function () { })   // ✗ evitar
    const myFunc = function () { }     // ✓ ok
    ```

* **Usar `break` para evitar pasar de largo `fallthrough` en casos `switch`.**

    eslint: [`no-fallthrough`](https://eslint.org/docs/rules/no-fallthrough)
    
    ```js
    switch (filter) 
    {
        case 1:
            doSomething();    // ✗ evitar
        case 2:
            doSomethingElse();
    }
    
    switch (filter) 
    {
        case 1:
            doSomething();
            break;           // ✓ ok
        case 2:
            doSomethingElse();
    }
    ```

* **Evitar decimales flotantes.**

    eslint: [`no-floating-decimal`](https://eslint.org/docs/rules/no-floating-decimal)
    
    ```js
    const discount = .5;      // ✗ evitar
    const discount = 0.5;     // ✓ ok
    ```

* **Evitar reasignación de declaraciones de funciones.**

    eslint: [`no-func-assign`](https://eslint.org/docs/rules/no-func-assign)
    
    ```js
    function myFunc () { }
    myFunc = myOtherFunc;    // ✗ evitar
    ```

* **Evitar reasignación de variables globales de solo-lectura.**

    eslint: [`no-global-assign`](https://eslint.org/docs/rules/no-global-assign)
    
    ```js
    window = {};     // ✗ evitar
    ```

* **Evitar usar eval() implícito.**

    eslint: [`no-implied-eval`](https://eslint.org/docs/rules/no-implied-eval)
    
    ```js
    setTimeout("alert('Hello world')");                   // ✗ evitar
    setTimeout(function () { window.alert('Hello world'); })     // ✓ ok
    ```

* **Evitar declaracion de funciones en bloques anidados.**

    eslint: [`no-inner-declarations`](https://eslint.org/docs/rules/no-inner-declarations)
    
    ```js
    if (authenticated) 
    {
        function setAuthUser () {}    // ✗ evitar
    }
    ```

* **Evitar cadenas de texto expresiones regulares invalidas en costructores `RegExp`.**

    eslint: [`no-invalid-regexp`](https://eslint.org/docs/rules/no-invalid-regexp)
    
    ```js
    RegExp('[a-z');    // ✗ evitar
    RegExp('[a-z]');   // ✓ ok
    ```

* **Evitar espacios en blanco irregulares.**

    eslint: [`no-irregular-whitespace`](https://eslint.org/docs/rules/no-irregular-whitespace)
    
    ```js
    function myFunc () /*<NBSP>*/{}   // ✗ evitar
    ```

* **Evitar uso de `__iterator__`.**

    eslint: [`no-iterator`](https://eslint.org/docs/rules/no-iterator)
    
    ```js
    Foo.prototype.__iterator__ = function () {};   // ✗ evitar
    ```

* **Evitar etiquetas que comparten el nombre de una variable en scope.**

    eslint: [`no-label-var`](https://eslint.org/docs/rules/no-label-var)
    
    ```js
    var score = 100;
    function game () 
    {
        score: while (true)       // ✗ evitar 
        {
            score -= 10;
            if (score > 0) continue score;
            break;
        }
    }
    ```

* **Evitar sentencias etiquetadas.**

    eslint: [`no-labels`](https://eslint.org/docs/rules/no-labels)
    
    ```js
    label:
    while (true) {
        break label;     // ✗ evitar
    }
    ```

* **Evitar bloques anidados innecesarios**

    eslint: [`no-lone-blocks`](https://eslint.org/docs/rules/no-lone-blocks)
    
    ```js
    function myFunc () {
        {                   // ✗ evitar
            myOtherFunc();
        }
    }
    
    function myFunc () {
        myOtherFunc();       // ✓ ok
    }
    ```

* **Evitar mezclar espacios y tabulaciones para sangría**

    eslint: [`no-mixed-spaces-and-tabs`](https://eslint.org/docs/rules/no-mixed-spaces-and-tabs)

* **Evitar uso de espacios en blanco multiples a excepcion de sangría**

    eslint: [`no-multi-spaces`](https://eslint.org/docs/rules/no-multi-spaces)
    
    ```js
    const id =    1234;    // ✗ evitar
    const id = 1234;       // ✓ ok
    ```

* **Evitar cadenas de texto multi-linea**

    eslint: [`no-multi-str`](https://eslint.org/docs/rules/no-multi-str)
    
    ```js
    const message = 'Hello \
                   world';     // ✗ evitar
    ```

* **Evitar usar `new` sin asignar a el objecto a una variable**

    eslint: [`no-new`](https://eslint.org/docs/rules/no-new)
    
    ```js
    new Character();                     // ✗ evitar
    const character = new Character();   // ✓ ok
    ```

* **Evitar uso de constructor `Function`.**

    eslint: [`no-new-func`](https://eslint.org/docs/rules/no-new-func)
    
    ```js
    var sum = new Function('a', 'b', 'return a + b');    // ✗ evitar
    ```

* **Evitar uso de constructor `Object`**

    eslint: [`no-new-object`](https://eslint.org/docs/rules/no-new-object)
    
    ```js
    let config = new Object();   // ✗ evitar
    ```

* **Evitar uso de `new require`.**

    eslint: [`no-new-require`](https://eslint.org/docs/rules/no-new-require)
    
    ```js
    const myModule = new require('my-module');    // ✗ evitar
    ```

* **Evitar uso de constructor `Symbol`.**

    eslint: [`no-new-symbol`](https://eslint.org/docs/rules/no-new-symbol)
    
    ```js
    const foo = new Symbol('foo');   // ✗ evitar
    ```

* **Evitar envolturas de instancias primitivas.**

    eslint: [`no-new-wrappers`](https://eslint.org/docs/rules/no-new-wrappers)
    
    ```js
    const message = new String('hello');   // ✗ evitar
    ```

* **Evitar llamar propiedades de objetos globles como funciones.**

    eslint: [`no-obj-calls`](https://eslint.org/docs/rules/no-obj-calls)
    
    ```js
    const math = Math();   // ✗ evitar
    ```

* **Evitar uso de octal literal.**

    eslint: [`no-octal`](https://eslint.org/docs/rules/no-octal)
    
    ```js
    const num = 042;     // ✗ evitar
    const num = '042';   // ✓ ok
    ```

* **Evitar escapado de secuencia octal en cadena de texto literal.**

    eslint: [`no-octal-escape`](https://eslint.org/docs/rules/no-octal-escape)
    
    ```js
    const copyright = 'Copyright \251';  // ✗ evitar
    ```

* **Evitar concatenacion de cadena de texto para `__dirname` y `__filename`.**

    eslint: [`no-path-concat`](https://eslint.org/docs/rules/no-path-concat)
    
    ```js
    const pathToFile = __dirname + '/app.js';            // ✗ evitar
    const pathToFile = path.join(__dirname, 'app.js');   // ✓ ok
    ```

* **Evitar uso de `__proto__`.** Use `getPrototypeOf` en su lugar.

    eslint: [`no-proto`](https://eslint.org/docs/rules/no-proto)
    
    ```js
    const foo = obj.__proto__;               // ✗ evitar
    const foo = Object.getPrototypeOf(obj);  // ✓ ok
    ```

* **Evitar re-reclaración de variables.**

    eslint: [`no-redeclare`](https://eslint.org/docs/rules/no-redeclare)
    
    ```js
    let name = 'John';
    let name = 'Jane';     // ✗ evitar
    
    let name = 'John';
    name = 'Jane';         // ✓ ok
    ```

* **Evitar multiples espacios en expresiones regulares.**

    eslint: [`no-regex-spaces`](https://eslint.org/docs/rules/no-regex-spaces)
    
    ```js
    const regexp = /test   value/;   // ✗ evitar
    
    const regexp = /test {3}value/;  // ✓ ok
    const regexp = /test value/;     // ✓ ok
    ```

* **Asignación de variables en el retorno de funciones debe estar rodeado de paréntesis.**

    eslint: [`no-return-assign`](https://eslint.org/docs/rules/no-return-assign)
    
    ```js
    function sum (a, b) 
    {
        return result = a + b;     // ✗ evitar
    }
    
    function sum (a, b) 
    {
        return (result = a + b);   // ✓ ok
    }
    ```

* **Evitar asignar una variable a si misma.**

    eslint: [`no-self-assign`](https://eslint.org/docs/rules/no-self-assign)
    
    ```js
    name = name;   // ✗ evitar
    ```

* **Evitar comparar una variable consigo mismo.**

    esint: [`no-self-compare`](https://eslint.org/docs/rules/no-self-compare)
    
    ```js
    if (score === score) {}   // ✗ evitar
    ```

* **Evitar uso de secuencia separado po comma.**

    eslint: [`no-sequences`](https://eslint.org/docs/rules/no-sequences)
    
    ```js
    if (doSomething(), !!test) {}   // ✗ evitar
    ```

* **Nombres restringidos no deben ser cambiados (shadowed).**

    eslint: [`no-shadow-restricted-names`](https://eslint.org/docs/rules/no-shadow-restricted-names)
    
    ```js
    let undefined = 'value';     // ✗ evitar
    ```

* **Array dispersos no estan permitidos.**

    eslint: [`no-sparse-arrays`](https://eslint.org/docs/rules/no-sparse-arrays)
    
    ```js
    let fruits = ['apple',, 'orange'];       // ✗ evitar
    ```

* **No se deben usar Tabulaciones.**

    eslint: [`no-tabs`](https://eslint.org/docs/rules/no-tabs)

* **Cadenas de textos regulares no deben contener placeholders de plantillas literales.**

    eslint: [`no-template-curly-in-string`](https://eslint.org/docs/rules/no-template-curly-in-string)
    
    ```js
    const message = 'Hello ${name}';   // ✗ evitar
    const message = `Hello ${name}`;   // ✓ ok
    ```

* **`super()` debe ser llamado inmediatamente antes de usar `this`.**

    eslint: [`no-this-before-super`](https://eslint.org/docs/rules/no-this-before-super)
    
    ```js
    class Dog extends Animal 
    {
        constructor () 
        {
            this.legs = 4;     // ✗ evitar
            super();
        }
    }
    ```

* **Solo se puede lanzar (`throw`) un objecto `Error`.**

    eslint: [`no-throw-literal`](https://eslint.org/docs/rules/no-throw-literal)
    
    ```js
    throw 'error';               // ✗ evitar
    throw new Error('error');    // ✓ ok
    ```

* **Espacios en blanco despues del final linea no estan permitidos .**

    eslint: [`no-trailing-spaces`](https://eslint.org/docs/rules/no-trailing-spaces)

* **Inicializar una variable con `undefined` no esta permitido.**

    eslint: [`no-undef-init`](https://eslint.org/docs/rules/no-undef-init)
    
    ```js
    let name = undefined;    // ✗ evitar
    
    let name;
    name = 'value';          // ✓ ok
    ```

* **Búcles no modificados no estan permitidos.**

    eslint: [`no-unmodified-loop-condition`](https://eslint.org/docs/rules/no-unmodified-loop-condition)
    
    ```js
    for (let i = 0; i < items.length; j++) {...}    // ✗ evitar
    for (let i = 0; i < items.length; i++) {...}    // ✓ ok
    ```

* **Evitar usar operador ternario cuando existe una alternative mas simple.**

    eslint: [`no-unneeded-ternary`](https://eslint.org/docs/rules/no-unneeded-ternary)
    
    ```js
    let score = val ? val : 0;     // ✗ evitar
    let score = val || 0;          // ✓ ok
    ```

* **Evitar dejar código inalcanzable despues de sentencias `return`, `throw`, `continue`, y `break` .**

    eslint: [`no-unreachable`](https://eslint.org/docs/rules/no-unreachable)
    
    ```js
    function doSomething ()
    {
        return true;
        console.log('never called');     // ✗ evitar
    }
    ```

* **Evitar sentencias de control de flujo en bloques `finally`.**

    eslint: [`no-unsafe-finally`](https://eslint.org/docs/rules/no-unsafe-finally)
    
    ```js
    try 
    {
        // ...
    } 
    catch (e) 
     {
        // ...
    } 
    finally 
    {
        return 42;     // ✗ evitar
    }
    ```

* **El operando izquierdo en operaciones relacionales no debe ser negado.**

    eslint: [`no-unsafe-negation`](https://eslint.org/docs/rules/no-unsafe-negation)
    
    ```js
    if (!key in obj) {}       // ✗ evitar
    ```

* **Evitar uso inncesario de `.call()` y `.apply()`.**

    eslint: [`no-useless-call`](https://eslint.org/docs/rules/no-useless-call)
    
    ```js
    sum.call(null, 1, 2, 3);   // ✗ evitar
    ```

* **Evitar usar constructores innecesarios.**

    eslint: [`no-useless-computed-key`](https://eslint.org/docs/rules/no-useless-computed-key)
    
    ```js
    const user = { ['name']: 'John Doe' };   // ✗ evitar
    const user = { name: 'John Doe' };       // ✓ ok
    ```

* **Evitar uso inncesario de escapado de text.**

    eslint: [`no-useless-escape`](https://eslint.org/docs/rules/no-useless-escape)
    
    ```js
    let message = 'Hell\o';  // ✗ evitar
    ```

* **Renombrar import, export o destructuración con el mismo nombre  no esta permitido**

    eslint: [`no-useless-rename`](https://eslint.org/docs/rules/no-useless-rename)
    
    ```js
    import { config as config } from './config';     // ✗ evitar
    import { config } from './config';               // ✓ ok
    ```

* **Evitar espacios en blanco antes de una propiedad.**

    eslint: [`no-whitespace-before-property`](https://eslint.org/docs/rules/no-whitespace-before-property)
    
    ```js
    user .name      // ✗ evitar
    user.name       // ✓ ok
    ```

* **Evitar uso de sentencia `with`.**

    eslint: [`no-with`](https://eslint.org/docs/rules/no-with)
    
    ```js
    with (val) {...}    // ✗ evitar
    ```

* **Mantener consistencia de nuevas lineas entre las propiedades de un objecto .**

    eslint: [`object-property-newline`](https://eslint.org/docs/rules/object-property-newline)
    
    ```js
    const user = {
       name: 'Jane Doe', age: 30,
       username: 'jdoe86'            // ✗ evitar
    };
    
    const user = { name: 'Jane Doe', age: 30, username: 'jdoe86' };    // ✓ ok
    
    const user = {
       name: 'Jane Doe',
       age: 30,
       username: 'jdoe86'
    };                                                                 // ✓ ok
    ```

* **Evitar espacios de relleno entre bloques.**

    eslint: [`padded-blocks`](https://eslint.org/docs/rules/padded-blocks)
    
    value: 'padded-blocks': ['error', 'always']
    
    ```js
    if (user) {
         const name = getName();      // ✗ evitar
        }
      
    if (user) {
                                      // ✓ ok
       const name = getName();
    
    }
    ```

* **Evitar espacios en blanco entre el operador de propagacion y la expresion**

    eslint: [`rest-spread-spacing`](https://eslint.org/docs/rules/rest-spread-spacing)
    
    ```js
    fn(... args);    // ✗ evitar
    fn(...args);     // ✓ ok
    ```

* **Punto y coma (semicolon) debe tener un espacio en blanco despues y no antes.**

    eslint: [`semi-spacing`](https://eslint.org/docs/rules/semi-spacing)
    
    ```js
    for (let i = 0 ;i < items.length ;i++) {...}    // ✗ evitar
    for (let i = 0; i < items.length; i++) {...}    // ✓ ok
    ```

* **Mantener espacio despues de los bloques.**

    eslint: [`space-before-blocks`](https://eslint.org/docs/rules/space-before-blocks)
    
    ```js
    if (admin){...}     // ✗ evitar
    if (admin) {...}    // ✓ ok
    ```

* **Evitar espacios en blanco entre paréntesis.**

    eslint: [`space-in-parens`](https://eslint.org/docs/rules/space-in-parens)
    
    ```js
    getName( name );     // ✗ evitar
    getName(name);       // ✓ ok
    ```

* **Operador unario debe tener espacio en blanco despues.**

    eslint: [`space-unary-ops`](https://eslint.org/docs/rules/space-unary-ops)
    
    ```js
    typeof!admin;        // ✗ evitar
    typeof !admin;        // ✓ ok
    ```

* **Usar espacios dentro de comentarios.**

    eslint: [`spaced-comment`](https://eslint.org/docs/rules/spaced-comment)
    
    ```js
    //comment           // ✗ evitar
    // comment          // ✓ ok
    
    /*comment*/         // ✗ evitar
    /* comment */       // ✓ ok
    ```

* **Evitar espacios en blanco dentro de placeholders de plantillas literales.**

    eslint: [`template-curly-spacing`](https://eslint.org/docs/rules/template-curly-spacing)
    
    ```js
    const message = `Hello, ${ name }`;    // ✗ evitar
    const message = `Hello, ${name}`;      // ✓ ok
    ```

* **Usar `isNaN()` cuando se desea chequear `NaN`.**

    eslint: [`use-isnan`](https://eslint.org/docs/rules/use-isnan)
    
    ```js
    if (price === NaN) { }      // ✗ evitar
    if (isNaN(price)) { }       // ✓ ok
    ```

* **`typeof` debe ser comparado con una cadena de texto valida.**

    eslint: [`valid-typeof`](https://eslint.org/docs/rules/valid-typeof)
    
    ```js
    typeof name === 'undefimed';     // ✗ evitar
    typeof name === 'undefined';     // ✓ ok
    ```

* **Expressiones Funciones inmediatamente invocadas (IIFEs) deben ser envueltas en paréntesis.**

    eslint: [`wrap-iife`](https://eslint.org/docs/rules/wrap-iife)
    
    ```js
    const getName = function () { }();     // ✗ evitar
    
    const getName = (function () { }());   // ✓ ok
    const getName = (function () { })();   // ✓ ok
    ```

* **El `*` en expresiones `yield*` deben tener un espacio en blanco antes y despues.**

    eslint: [`yield-star-spacing`](https://eslint.org/docs/rules/yield-star-spacing)
    
    ```js
    yield* increment();    // ✗ evitar
    yield * increment();   // ✓ ok
    ```

* **Evitar condiciones Yoda.**

    eslint: [`yoda`](https://eslint.org/docs/rules/yoda)
    
    ```js
    if (42 === age) { }    // ✗ evitar
    if (age === 42) { }    // ✓ ok
    ```

## Puntos y comas (semicolons)

* Con puntos y comas.

  eslint: [`semi`](https://eslint.org/docs/rules/semi)

  ```js
  window.alert('hi');  // ✓ ok
  window.alert('hi')   // ✗ evitar
  ```

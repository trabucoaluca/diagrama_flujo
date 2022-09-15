# Desafío: javaScript

## Nombre de Desafío: introduccion_js

## Instrucciones

Determiná que será impreso en la consola, sin ejecutar el código.

> Investiga cuál es la diferencia entre declarar una variable con `var` y directamente asignarle un valor.

```javascript
x = 1;
var a = 5;
var b = 10;
var c = function(a, b, c) {// 8,9,10
  var x = 10;
  console.log(x);// 10
  console.log(a);// 8
  var f = function(a, b, c) {// 8,9,10
    b = a;
    console.log(b);// 8
    b = c;
    var x = 5;
  }
  f(a,b,c);// 8
  console.log(b);// 9
}
c(8,9,10);//10,8,8,9
console.log(b);// 10
console.log(x);// 1
```

10
8
8
9
10
1

```javascript
console.log(bar);// undefined
console.log(baz);// error
foo();
function foo() { console.log('Hola!'); }
var bar = 1;
baz = 2;
```
undefined (No esta definido)
Error (No esta inicializado)

```javascript
var instructor = "Jhoswe";
if(true) {
    var instructor = "Jose";
}
console.log(instructor);// Jose
```

Jose

```javascript
var instructor = "Jhoswe";
console.log(instructor);// Jhoswe
(function() {
   if(true) {
      var instructor = "Jose";
      console.log(instructor);
   }
})();// Jose
console.log(instructor);// Joshwe
```
Jhoswe
Jose
Jhoswe

```javascript
var instructor = "Jhoswe";
let pm = "Jose";
if (true) {
    var instructor = "The Flash";
    let pm = "Reverse Flash";
    console.log(instructor);// The Flash
    console.log(pm);// Reverse Flash
}
console.log(instructor);// The Flash
console.log(pm);// Jose
```
The Flash
Reverse Flash
The Flash
Jose

### Correción de Datos

¿Cuál crees que será el resultado de la ejecución de estas operaciones?:

```javascript
6 / "3"// 2
"2" * "3"// 6
4 + 5 + "px"// 9px
"$" + 4 + 5// $45
"4" - 2// 2
"4px" - 2//NaN
7 / 0// infinity
{}[0]// undefined
parseInt("09")//9
5 && 2// 2
2 && 5// 5
5 || 0// 5
0 || 5// 5
[3]+[3]-[10]// 23
3>2>1 // false
[] == ![] // true
```

2
6
9px
$45
2
NaN
infinity
undefined
9
2
5
5
5
23
false
true

> Si te quedó alguna duda repasá con [este artículo](http://javascript.info/tutorial/object-conversion).


### Hoisting

¿Cuál es el output o salida en consola luego de ejecutar este código? Explicar por qué:

```javascript
function test() {
   console.log(a);// undefined
   console.log(foo());// 2

   var a = 1;
   function foo() {
      return 2;
   }
}

test();// undefined, 2
```

undefined
2
Sucede porque, al iniciar el script manda a inprimir la variable 'a' pero esta aun no esta definida por lo cual su salida es 'undefined', luego manda a imprimir la funcion 'foo' la cual esta no importa el orden ya que se de prioridad a las funciones que a las declaraciones de variables.

Y el de este código? :

```javascript
var snack = 'Meow Mix';

function getFood(food) {
    if (food) {
        var snack = 'Friskies';
        return snack;
    }
    return snack;
}

getFood(false);
```

No puede mandar a 'imprimir' nada ya que solo esta regresando un valor pero no sabe como mandarlo o mostrarlo


### This

¿Cuál es el output o salida en consola luego de ejecutar esté código? Explicar por qué:

```javascript
var fullname = 'Jhoswe Castro';
var obj = {
   fullname: 'Jose Zuñiga
      fullname: 'Jorge Alonso',
      getFullname: function() {
         return this.fullname;
      }
   }
};

console.log(obj.prop.getFullname());

var test = obj.prop.getFullname;

console.log(test());// error
```

Error
Falta apertura de llave, coma, y no existe la propiedad 'prop'.


### Event loop

Considerando el siguiente código, ¿Cuál sería el orden en el que se muestra por consola? ¿Por qué?

```javascript
function printing() {
   console.log(1);
   setTimeout(function() { console.log(2); }, 1000);
   setTimeout(function() { console.log(3); }, 0);
   console.log(4);
}

printing();// 1,4,3,2
```

1
4
3
2
Manda a imprimir em el orden en que aparecen los 'console', dejando al final o una vez terminada la etapa de ejecucion empieza el conteo para las funciones de 'setTimeout', por lo cual imprime primero el que se ejecute en el menor tiempo.
# 2020 js vanilla testing 002

<p align="center">
    <img src="https://github.com/GeeksHubsAcademy/2020-geekshubs-media/blob/master/image/logo.png" >	
</p>

## Temario

* [Testeando String.prototype](https://github.com/GeeksHubsAcademy/2020-js-vanilla-testing-002#testeando-stringprototype)
* [Arquitectura del proyecto](https://github.com/GeeksHubsAcademy/2020-js-vanilla-testing-002#arquitectura-del-proyecto)
* [Diseñando nuestros Tests](https://github.com/GeeksHubsAcademy/2020-js-vanilla-testing-002#dise%C3%B1ando-nuestros-tests)
    * [split](https://github.com/GeeksHubsAcademy/2020-js-vanilla-testing-002#split)
    * [charAt](https://github.com/GeeksHubsAcademy/2020-js-vanilla-testing-002#chartat)
    * [toLowerCase](https://github.com/GeeksHubsAcademy/2020-js-vanilla-testing-002#tolowercase)
    * [toUpperCase](https://github.com/GeeksHubsAcademy/2020-js-vanilla-testing-002#touppercase)
    * [indexOf](https://github.com/GeeksHubsAcademy/2020-js-vanilla-testing-002#indexof)
* [Lanzando la Suite de Test](https://github.com/GeeksHubsAcademy/2020-js-vanilla-testing-002#lanzando-la-suite-de-test)
    * [split](https://github.com/GeeksHubsAcademy/2020-js-vanilla-testing-002#split-1)
    * [charAt](https://github.com/GeeksHubsAcademy/2020-js-vanilla-testing-002#charat)
    * [toLowerCase](https://github.com/GeeksHubsAcademy/2020-js-vanilla-testing-002#tolowercase-1)
    * [toUpperCase](https://github.com/GeeksHubsAcademy/2020-js-vanilla-testing-002#touppercase-1)
    * [indexOf](https://github.com/GeeksHubsAcademy/2020-js-vanilla-testing-002#indexof-1)
* [Conclusiones](https://github.com/GeeksHubsAcademy/2020-js-vanilla-testing-002#conclusiones)
* [Referencias](https://github.com/GeeksHubsAcademy/2020-js-vanilla-testing-002#referencias)

### Testeando String.prototype
```
Como se ha visto en la teoría, cualquier String de JavaScript tiene unos métodos por defecto 
que se pueden utilizar para hacer operaciones con ellas mismas. 

En la práctica de hoy vamos a proporcionar una solución con el testing de los métodos más
usados.
```

#### Jest - Framework Testing
```    
Basándonos en la practica '2020-js-vanilla-testing-001' vamos a crear una nueva carpeta llamada '002-testing'.
En ella instalaremos 'Jest' con el comando que nos proporciona 'npm'.

Crea una carpeta llamada '002-testing':
    $ mdkir 002-testing
    
Accede a ella :
    $ cd 002-testing

Instala 'Jest' con el siguiente comando:
    $ npm install --save-dev jest
 
Valida que la terminal te ha mostrado un mensaje terminado como este:
      npm WARN 002-testing No description
      npm WARN 002-testing No repository field.
      npm WARN 002-testing No README data
      npm WARN 002-testing No license field.
     
      + jest@25.2.3
      added 474 packages from 282 contributors and audited 1095501 packages in 31.784s
      found 0 vulnerabilities

Para saber que todo se ha instalado correctamente, dentro de nuestra carpeta ejecutamos el comando:
    $ ls

Debes visualizar estas dos elementos:
    $ node_modules/  package-lock.json
    
Para poder ejecutar 'Jest' se necesita crear un fichero y añadir la dependencia.
    $ touch package.json

En la terminal, abrimos nuestro editor y copiamos el siguiente código:

'
{
  "scripts": {
    "test": "jest"
  }
}
'
Guardamos y cerramos el editor.

Para saber que todo se ha seguido correctamente, dentro de nuestra carpeta ejecutamos el comando:
    $ ls

Debes visualizar estos tres elementos:
    $node_modules/  package.json  package-lock.json
```


### Arquitectura del proyecto

```
Lo primero que vamos hacer es diseñar nuestra suite de Test (paquetería) para tener el alcance 'end-to-end' 
de lo que queremos desarrollar.

En la propia carpeta '002-testing' ejecutamos el siguiente comando:
    $ touch suite.test.js

Dicho fichero va a permitir a 'Jest' ejecutar la bateria de Test que vamos a crear.
Actualmente el fichero está vacío. Simplemente nos interesa tener una buena arquitectura de proyecto.

Vamos a definir 5 tests que deben de hacer referencia a 5 funciones de String.prototypes.

Al estar en una etapa temprana, vamos hacer las cosas de la manera más fácil posible.

Vamos a definir 5 ficheros primeramente.

Ficheros 

* test02-split.js
* test02-toLowerCase.js
* test02-toUpperCase.js
* test02-charAt.js
* test02-indexOf.js

Lanzamos el siguiente comando por la terminal de git-bash.
  $ touch test02-split.js test02-toLowerCase.js test02-toUpperCase.js test02-chartAt.js test02-indexOf.js


Para saber que todo se ha hecho correctamente, dentro de nuestra carpeta ejecutamos el comando:
    $ ls

Debes visualizar estas elementos:

node_modules/
package.json
package-lock.json
suite.test.js
test02-split.js
test02-chartAt.js
test02-indexOf.js
test02-toLowerCase.js
test02-toUpperCase.js

```

### Diseñando nuestros Tests

```
Llegados a este punto lo que vamos hacer es diseñar nuestra bateria de test.
Con ella, lo que vamos a conseguir es tener un diseño primerizo que nos va a permitir tener
una primera visión.

Por supuesto, no vamos a implementar nada todavía, simplemente vamos a diseñar.

Nos basamos en el patrón AAA que vimos anteriormente y procedemos método a método:
```

#### split
```
En la terminal, abrimos nuestro editor y copiamos el siguiente código en suite.test.js:

' 
    const split = require('./test02-split.js');                                                  //L-1

    test('Split("user:ape1:ape2:city",\':\' to equals ["user","ape1","ape2","city"] )', ()=>{    //L-3
    // Arrange
    var expected = ["user","ape1","ape2","city"];                                                //L-5

    // Act
    var result = split("user:ape1:ape2:city",':');                                               //L-8
    
    // Assert
    expect(result).toStrictEqual(expected);                                                      //L-11
    });                                                                                          //L-12

'

Fíjese que estamos diseñando un test sin tener la implementación todavía.
Estamos dando por hecho que nuestra función 'split' necesita dos parámetro de entrada.

Un primero parámetro donde va la string que queremos separar. 
Un segundo parámetro con el separador.

El resultado es la separación de la String con cada cadena.

A continuación describimos cada una de las líneas:

L-1  - Permite a 'Jest' acceder a la función de nuestro algoritmo de Split.
L-3  - Define la cabecera de una función de Testing para el framework de 'Jest'. 
L-5  - Inicializamos variables.
L-8  - Llamámos al método de nuestro Test.
L-11 - Comparamos nuestro resultado esperado con el resultado del método que hemos desarrollado.
L-12 - Cierre de la función.

Cerramos el editor y volvemos a la terminal.
```

#### chartAt

```
En la terminal, abrimos nuestro editor y copiamos el siguiente código (abajo) en suite.test.js:

' 
    const charAt = require('./test02-charAt.js');                                               //L-1

    test('CharAt("user:ape1:ape2:city",8)  to equals 1 )', ()=>{                                //L-3
    // Arrange
    var toBe = '1';                                                                             //L-5

    // Act
    var result = charAt("user:ape1:ape2:city", 8);                                              //L-8
    
    // Assert
    expect(result).toEqual(toBe);                                                               //L-11
    });                                                                                         //L-12

'

Fíjese que estamos diseñando un test sin tener la implementación todavía.
Estamos dando por hecho que nuestra función 'charAt' necesita dos parámetro de entrada.

Un primero parámetro donde va la string. 
Un segundo parámetro con el índice a obtener.

El resultado es la obtención de indice número 7 de la String.

A continuación describimos cada una de las líneas:

L-1  - Permite a 'Jest' acceder a la función de nuestro algoritmo de CharAt.
L-3  - Define la cabecera de una función de Testing para el framework de 'Jest'. 
L-5  - Inicializamos variables.
L-8  - Llamámos al método de nuestro Test.
L-11 - Comparamos nuestro resultado esperado con el resultado del método que hemos desarrollado.
L-12 - Cierre de la función.

Cerramos el editor y volvemos a la terminal.
```

#### toLowerCase
```
En la terminal, abrimos nuestro editor y copiamos el siguiente código (abajo) en suite.test.js:

' 
    const toLowerCase = require('./test02-toLowerCase.js');                                      //L-1

    test('toLowerCase("Hello World") to equals "hello world")', ()=>{                            //L-3
    // Arrange
    var toBe = "hello world";                                                                    //L-5

    // Act
    var result = toLowerCase("Hello World");                                                     //L-8
    
    // Assert
    expect(result).toBe(toBe);                                                                   //L-11
    });                                                                                          //L-12

'

Fíjese que estamos diseñando un test sin tener la implementación todavía.
Estamos dando por hecho que nuestra función 'toLowerCase' necesita un parámetro de entrada.

Un primero parámetro donde va la string. 

El resultado es pasar a minúsulas el input de la función.

A continuación describimos cada una de las líneas:

L-1  - Permite a 'Jest' acceder a la función de nuestro algoritmo de Split.
L-3  - Define la cabecera de una función de Testing para el framework de 'Jest'. 
L-5  - Inicializamos variables.
L-8  - Llamámos al método de nuestro Test.
L-11 - Comparamos nuestro resultado esperado con el resultado del método que hemos desarrollado.
L-12 - Cierre de la función.

Cerramos el editor y volvemos a la terminal.
```

#### toUppercase
```
En la terminal, abrimos nuestro editor y copiamos el siguiente código (abajo) en suite.test.js:

' 
    const toUppercase = require('./test02-toUppercase.js');                                      //L-1

    test('toUppercase("Hello World") to equals "HELLO WORLD")', ()=>{                            //L-3
    // Arrange
    var toBe = "HELLO WORLD";                                                                    //L-5

    // Act
    var result = toUppercase("Hello World");                                                     //L-8
    
    // Assert
    expect(result).toBe(toBe);                                                                   //L-11
    });                                                                                          //L-12

'

Fíjese que estamos diseñando un test sin tener la implementación todavía.
Estamos dando por hecho que nuestra función 'toUppercase' necesita un parámetro de entrada.

Un primero parámetro donde va la string. 

El resultado es pasar a mayúsculas el input de la función.

A continuación describimos cada una de las líneas:

L-1  - Permite a 'Jest' acceder a la función de nuestro algoritmo de Split.
L-3  - Define la cabecera de una función de Testing para el framework de 'Jest'. 
L-5  - Inicializamos variables.
L-8  - Llamámos al método de nuestro Test.
L-11 - Comparamos nuestro resultado esperado con el resultado del método que hemos desarrollado.
L-12 - Cierre de la función.

Cerramos el editor y volvemos a la terminal.
```

#### indexOf
```
En la terminal, abrimos nuestro editor y copiamos el siguiente código (abajo) en suite.test.js:

' 
    const indexOf = require('./test02-indexOf.js');                                              //L-1

    test('indexOf("Hello World","World") to equals 6)', ()=>{                                    //L-3
    // Arrange
    var toBe = 6;                                                                                //L-5

    // Act
    var result = indexOf("Hello World","World");                                                 //L-8
    
    // Assert
    expect(result).toBe(toBe);                                                                   //L-11
    });                                                                                          //L-12

'

Fíjese que estamos diseñando un test sin tener la implementación todavía.
Estamos dando por hecho que nuestra función 'indexOf' necesita dos parámetro de entrada

Un primero parámetro donde va la string. 
Un segundo parámetro donde va la busqueda de la palabra a buscar.

El resultado es obtener un número/índice que indique la posición de la palabra.

A continuación describimos cada una de las líneas:

L-1  - Permite a 'Jest' acceder a la función de nuestro algoritmo de Split.
L-3  - Define la cabecera de una función de Testing para el framework de 'Jest'. 
L-5  - Inicializamos variables.
L-8  - Llamámos al método de nuestro Test.
L-11 - Comparamos nuestro resultado esperado con el resultado del método que hemos desarrollado.
L-12 - Cierre de la función.

Cerramos el editor y volvemos a la terminal.

```

### Lanzando la Suite de Test
```
Ahora simplemente vamos a lanzar Jest por la terminal para ver que nuestro tests fallan.
Es necesario realizar este primer paso antes de dar implementación a nuestros tests.

Ejecutamos el siguiente comando :
    $ npm run test
    
Debemos de obtener la siguiente salida:


        > @ test C:\Users\vbolinches\Documents\002-testing
        > jest

        FAIL ./suite.test.js
          ● Test suite failed to run

            Cannot find module './test02-split.js' from 'suite.test.js'

            > 1 | const split = require('./test02-split.js');                                                 
                |                      ^
              2 |
              3 |     test('Split("user:ape1:ape2:city",\':\' to equals ["user","ape1",...      
              4 |     // Arrange

              at Resolver.resolveModule (node_modules/jest-resolve/build/index.js:296:11)
              at Object.<anonymous> (suite.test.js:1:22)


Es muy importante saber qué nos quiere decir el interprete de JS con este fallo...
Recordar que simplemente hemos diseñado y no hemos hecho implementación de nuestros algoritmos.

El error recalca que hay algún fallo en el fichero './test02-split.js'. 
Exactamente indica que no resuleve un método exportado..
Obvio, no tenemos implementación.
```

### split 
```
Ahora vamos a desarrollar nuestro algoritmo split:

En la propia carpeta '002-testing' ejecutamos el siguiente comando:
    $ touch test02-split.js

En este fichero vamos añadir una pequeña función que devuelva una Array separando la palabras
de nuestra string por separador.

Abrimos nuestro editor y copiamos el siguiente código:

' 
    function split(param, separador) {                                               //L-1
        return param.split(separador);                                               //L-2
    }                                                                                //L-3
   
    module.exports = split;                                                          //L-5
'

A continuación describimos cada una de las líneas:

L-1  - Define la cabecera de nuestro algoritmo, junto con el parametro de entrada.
L-2  - Línea que indica la devolución del resultado de nuestro método.
L-3  - Cierre de nuestro algoritmo.
L-5  - Almacena la función 'split' en una variable que luego 'Jest' recupera con 
       la línea 1 del fichero suite.test.js 
       
Cerramos el editor y volvemos a la terminal.

Ejecutamos el siguiente comando :
    $ npm run test
    
Debemos de obtener la siguiente salida:

        FAIL ./suite.test.js
          √ Split("user:ape1:ape2:city",':' to equals ["user","ape1","ape2","city"] ) (4ms)
          × CharAt("user:ape1:ape2:city",8)  to equals 1 ) (3ms)
          × toLowerCase("Hello World") to equals "hello world")
          × toUppercase("Hello World") to equals "HELLO WORLD")
          × indexOf("Hello World","World") to equals 6)
               ...

Hemos pasado el test en Verde!
Simplemente se queja de que el siguiente test no tiene implementación.

```

### charAt 
```
Ahora vamos a desarrollar nuestro algoritmo charAt:

En la propia carpeta '002-testing' ejecutamos el siguiente comando:
    $ touch test02-charAt.js

En este fichero vamos añadir una pequeña función que devuelva una 'char' indicando
un índice en un segundo parámetro.

Abrimos nuestro editor y copiamos el siguiente código:

'
    function charAt(param, separador) {                                              //L-1
        return param.charAt(separador);                                              //L-2
    }                                                                                //L-3
   
    module.exports = charAt;                                                         //L-5
'

A continuación describimos cada una de las líneas:

L-1  - Define la cabecera de nuestro algoritmo, junto con el parametro de entrada.
L-2  - Línea que indica la devolución del resultado de nuestro método.
L-3  - Cierre de nuestro algoritmo.
L-5  - Almacena la función 'charAt' en una variable que luego 'Jest' recupera con 
       la línea 1 del fichero suite.test.js 
       
Cerramos el editor y volvemos a la terminal.

Ejecutamos el siguiente comando :
    $ npm run test
    
Debemos de obtener la siguiente salida:
     
        FAIL ./suite.test.js
          √ Split("user:ape1:ape2:city",':' to equals ["user","ape1","ape2","city"] ) (4ms)
          √ CharAt("user:ape1:ape2:city",8)  to equals 1 ) (3ms)
          × toLowerCase("Hello World") to equals "hello world")
          × toUppercase("Hello World") to equals "HELLO WORLD")
          × indexOf("Hello World","World") to equals 6)
            ...
                        
Ya no tenemos Fallo! 
Simplemente se queja de que el siguiente test no tiene implementación.

```


### toLowerCase 
```
Ahora vamos a desarrollar nuestro algoritmo toLowerCase:

En la propia carpeta '002-testing' ejecutamos el siguiente comando:
    $ touch test02-toLowerCase.js

En este fichero vamos añadir una pequeña función que devuelva una 'string' 
pasando nuestro argumento a letras en minúsculas.

Abrimos nuestro editor y copiamos el siguiente código:

'
    function toLowerCase(param) {                                                    //L-1
        return param.toLowerCase();                                                  //L-2
    }                                                                                //L-3
   
    module.exports = toLowerCase;                                                    //L-5
'

A continuación describimos cada una de las líneas:

L-1  - Define la cabecera de nuestro algoritmo, junto con el parametro de entrada.
L-2  - Línea que indica la devolución del resultado de nuestro método.
L-3  - Cierre de nuestro algoritmo.
L-5  - Almacena la función 'toLowerCase' en una variable que luego 'Jest' recupera con 
       la línea 1 del fichero suite.test.js 
       
Cerramos el editor y volvemos a la terminal.

Ejecutamos el siguiente comando :
    $ npm run test
    
Debemos de obtener la siguiente salida:
        
         FAIL ./suite.test.js
          √ Split("user:ape1:ape2:city",':' to equals ["user","ape1","ape2","city"] ) (4ms)
          √ CharAt("user:ape1:ape2:city",8)  to equals 1 ) (3ms)
          √ toLowerCase("Hello World") to equals "hello world")
          × toUppercase("Hello World") to equals "HELLO WORLD")
          × indexOf("Hello World","World") to equals 6)

Ya no tenemos Fallo! 
Simplemente se queja de que el siguiente test no tiene implementación.

```

### toUpperCase 
```
Ahora vamos a desarrollar nuestro algoritmo toLowerCase:

En la propia carpeta '002-testing' ejecutamos el siguiente comando:
    $ touch test02-toUpperCase.js

En este fichero vamos añadir una pequeña función que devuelva una 'string' 
pasando nuestro argumento a letras en mayúsculas.

Abrimos nuestro editor y copiamos el siguiente código:

'
    function toUpperCase(param) {                                                    //L-1
        return param.toUpperCase();                                                  //L-2
    }                                                                                //L-3
   
    module.exports = toUpperCase;                                                    //L-5
'

A continuación describimos cada una de las líneas:

L-1  - Define la cabecera de nuestro algoritmo, junto con el parametro de entrada.
L-2  - Línea que indica la devolución del resultado de nuestro método.
L-3  - Cierre de nuestro algoritmo.
L-5  - Almacena la función 'toUpperCase' en una variable que luego 'Jest' recupera con 
       la línea 1 del fichero suite.test.js 
       
Cerramos el editor y volvemos a la terminal.

Ejecutamos el siguiente comando :
    $ npm run test
    
Debemos de obtener la siguiente salida:
        
         FAIL ./suite.test.js
          √ Split("user:ape1:ape2:city",':' to equals ["user","ape1","ape2","city"] ) (4ms)
          √ CharAt("user:ape1:ape2:city",8)  to equals 1 ) (3ms)
          √ toLowerCase("Hello World") to equals "hello world")
          √ toUppercase("Hello World") to equals "HELLO WORLD")
          × indexOf("Hello World","World") to equals 6)

Ya no tenemos Fallo! 
Simplemente se queja de que el siguiente test no tiene implementación.

Ya estamos llegando al final del testing!
```

### indexOf 
```
Ahora vamos a desarrollar nuestro algoritmo toLowerCase:

En la propia carpeta '002-testing' ejecutamos el siguiente comando:
    $ touch test02-indexOf.js

En este fichero vamos añadir una pequeña función que devuelva un resultado 
con el un número/índice que indique la posición de la palabra.

Abrimos nuestro editor y copiamos el siguiente código:

'
    function indexOf(param,palabra) {                                                //L-1
        return param.indexOf(palabra);                                               //L-2
    }                                                                                //L-3
   
    module.exports = indexOf;                                                        //L-5
'

A continuación describimos cada una de las líneas:

L-1  - Define la cabecera de nuestro algoritmo, junto con el parametro de entrada.
L-2  - Línea que indica la devolución del resultado de nuestro método.
L-3  - Cierre de nuestro algoritmo.
L-5  - Almacena la función 'indexOf' en una variable que luego 'Jest' recupera con 
       la línea 1 del fichero suite.test.js 
       
Cerramos el editor y volvemos a la terminal.

Ejecutamos el siguiente comando :
    $ npm run test
    
Debemos de obtener la siguiente salida:
        
            > jest

            PASS ./suite.test.js
              √ Split("user:ape1:ape2:city",':' to equals ["user","ape1","ape2","city"] ) (4ms)
              √ CharAt("user:ape1:ape2:city",8)  to equals 1 ) (1ms)
              √ toLowerCase("Hello World") to equals "hello world")
              √ toUppercase("Hello World") to equals "HELLO WORLD") (1ms)
              √ indexOf("Hello World","World") to equals 6) (1ms)

            Test Suites: 1 passed, 1 total
            Tests:       5 passed, 5 total
            Snapshots:   0 total
            Time:        4.039s
            Ran all test suites.

Éxito!
```

### Conclusiones
```
Hemos empezado hacer TDD sin saberlo.
Hemos guiado el diseño de nuestros algoritmos a través de los test y no al revés.

Revisa las referencias.
```


### Referencias
  * [String.prototype](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/String/prototype)
  * [TDD](https://medium.com/laboratoria-how-to/qu%C3%A9-es-tdd-por-qu%C3%A9-todos-te-odiar%C3%A1n-si-no-lo-haces-63ce217d2bc3)
  * [Test Driven Development by Example - Kent Beck](https://docs.google.com/viewer?a=v&pid=sites&srcid=ZGVmYXVsdGRvbWFpbnx0ZXN0MTIzNHNpbTQ2NXxneDpiYTJmYWIwYTAyOGJiZmQ)
  
  
  
  
  
<div>
    <p align="center">
        <img src="https://github.com/GeeksHubsAcademy/2020-geekshubs-media/blob/master/image/pixel.png" >	
    </p>
  </div>
  
  <footer>
     <div>
        <a href="https://github.com/GeeksHubsAcademy/2020-js-vanilla-testing-001"><< Atrás</a>
         <a href="https://github.com/GeeksHubsAcademy/2020-js-vanilla-testing-002/blob/master/README.md#referencias">
        <img src="https://github.com/GeeksHubsAcademy/2020-geekshubs-media/blob/master/image/pixel.png" align="center"                  height="10" width="714"/>
         </a>
         <a href="https://github.com/GeeksHubsAcademy/2020-js-vanilla-testing-003">Siguiente >></a>   
    </div>


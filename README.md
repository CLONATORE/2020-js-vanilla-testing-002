# 2020 js vanilla testing 002

<p align="center">
    <img src="https://github.com/GeeksHubsAcademy/hello-world/blob/master/assets/media/logo/logo.png" >	
</p>

## Temario

* [Testeando String.prototype]()
* [Arquitectura del proyecto]()
* [Diseñando nuestros Tests]()
* [split]()
* [charAt]()
* [toLowerCase]()
* [toUpperCase]()
* [indexOf]()
* [Lanzando la Suite de Test]()

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
      npm WARN 001-testing No description
      npm WARN 001-testing No repository field.
      npm WARN 001-testing No README data
      npm WARN 001-testing No license field.
     
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

    test('Split("user:ape1:ape2:city",':' to equals ["user","ape1","ape2","city"] )', ()=>{      //L-3
    // Arrange
    var expected = ["user","ape1","ape2","city"];                                                //L-5

    // Act
    var result = split("user:ape1:ape2:city",':');                                               //L-8
    
    // Assert
    expect(result).toBe(expected);                                                               //L-11
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
    const charAt = require('./test02-charAt.js');                                                //L-1

    test('CharAt("user:ape1:ape2:city",7)  to equals '1' )', ()=>{                               //L-3
    // Arrange
    var expected = '7';                                                                          //L-5

    // Act
    var result = split("user:ape1:ape2:city", 1);                                                //L-8
    
    // Assert
    expect(result).toBe(expected);                                                               //L-11
    });                                                                                          //L-12

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
    var expected = "hello world";                                                                //L-5

    // Act
    var result = toLowerCase("Hello World");                                                     //L-8
    
    // Assert
    expect(result).toBe(expected);                                                               //L-11
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
    var expected = "HELLO WORLD";                                                                //L-5

    // Act
    var result = toLowerCase("Hello World");                                                     //L-8
    
    // Assert
    expect(result).toBe(expected);                                                               //L-11
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
    var expected = 6;                                                                            //L-5

    // Act
    var result = toLowerCase("Hello World");                                                     //L-8
    
    // Assert
    expect(result).toBe(expected);                                                               //L-11
    });                                                                                          //L-12

'

Fíjese que estamos diseñando un test sin tener la implementación todavía.
Estamos dando por hecho que nuestra función 'indexOf' necesita dos parámetro de entrada

Un primero parámetro donde va la string. 
Un segundo parámetro donde va la busqueda de la palabra a buscar.

El resultado es obtener un número que indique la posición de la palabra.

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

```

### Conclusiones
```
Después de haber leído esta pequeña introducción simplemente queremos que asientes conceptos...

La capacidad de llegar a un resultado acotando diferentes soluciones es la diferencia entre la 
persona que desarrolla y testea a la persona que testea y desarrolla.

Son dos conceptos totalmente diferente que ahora mismo no podrás apreciar.

Hay gente que tarda años en saber/ver estas diferencias... En Geekshubs queremos dejarlas claras desde 
el minuto uno de la formación. Por ello decimos que queremos que simplemente absorvas conocimiento, luego 
puliremos los detalles.

Para finalizar, te diremos que estás aprendiendo hábitos de desarrollo, capacidades de análisis y premisas 
de metolodogía ágil.

Tú aún no lo sabes, pero vas a empezar a pensar en construir tu meta poco a poco a base de pequeños Tests.  

Ahora ondea en las referencias.

```


### Referencias
  * [String.prototype](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/String/prototype)
  * [Pirámide de Pruebas - microsoft](https://docs.microsoft.com/es-es/dotnet/architecture/modern-web-apps-azure/test-asp-net-core-mvc-apps)
  * [Prueba unitaria - wikipedia](https://es.wikipedia.org/wiki/Prueba_unitaria)
  * [Unit-Testing](https://less.works/less/technical-excellence/unit-testing.html)
  * [Patrón AAA](https://uniwebsidad.com/libros/tdd/capitulo-5/las-tres-partes-del-test-aaa)


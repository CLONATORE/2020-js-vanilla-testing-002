# 2020 js vanilla testing 002

<p align="center">
    <img src="https://github.com/GeeksHubsAcademy/hello-world/blob/master/assets/media/logo/logo.png" >	
</p>

## Temario

* [Testeando String.prototype]()
* [Arquitectura del proyecto]()
* [Diseñando nuestros Tests]()
* [split(character)]()
* [toLowerCase()]()
* [toUpperCase()]()
* [indexOf(substring [, startFrom])]()
* [charAt(number)]()

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
Seguidamente ejecutamos el siguiente comando para crear la suite de test vacia.
  $ touch suite.test.js
En la terminal, abrimos nuestro editor y copiamos el siguiente código:

' 
    const concatenar = require('./test02.js');                                       //L-1

    test('Concatena Hello + Victor to equal "Hello Victor"', function ()    {        //L-3
    // Arrange
    var expected = "Hello Victor";                                                   //L-5

    // Act
    var result = concatenar("Victor");                                               //L-8
    
    // Assert
    expect(result).toBe(expected);                                                   //L-11
    });                                                                              //L-12

'

Fíjese que estamos diseñando un test sin tener la implementación todavía.
Estamos dando por hecho que nuestra función 'concatenar' necesita un parámetro de entrada
y el resultado es la concatenación con la palabra "Hello".

A continuación describimos cada una de las líneas:

L-1  - Permite a 'Jest' acceder a la función de nuestro algoritmo de concatenación.
L-3  - Define la cabecera de una función de Testing para el framework de 'Jest'. 
L-5  - Inicializamos variables.
L-8  - Llamámos al método de nuestro Test.
L-11 - Comparamos nuestro resultado esperado con el resultado del método que hemos desarrollado.
L-12 - Cierre de la función.

Cerramos el editor y volvemos a la terminal.
```

### Qué es un test unitario?

```
Es una forma de comprobar el correcto funcionamiento de una unidad de código.

Debemos de entender que un método solo debe de tener un solo comportamiento, pues incluir una clausula 
'if-else' nos lleva a tener dos estados. Para poder validar estos dos estados debemos de tener dos métodos
independientes que validen la clásula 'if' y otro método que valida la cláusula 'else'.

De esta manera cumpliremos el propósito de test unitario, simplemente un unidad de código.

Recuerda que para poder decir que hacemos testing, debemos de cubrir todas las salidas del método.
Piensas qué testeando solo la cláusula 'if-else' está todo hecho?
Y... si resulta que estoy comprobando el correcto funcionamiento de una división y el denominador es 0 ???

Ahí lo dejo...

```

### Cómo vamos escribir los test unitarios ?

```
Ahora mismo el alumno no debe de escribir ningún test, simplemente absorver conocimiento.

Vamos a proveerte de soluciones ya estructuradas donde aprenderas a pensar.
Para ello usaremos 'ingeniería inversa'.

Al principio te daremos la solución hecha y simplemente tendrás que analizar y absorver el conocimiento.
En una segunda iteración te daremos partes del mismo, y sabiendo que previamente obtuvistes un conocimiento
'end-to-end', deberás añadir la partes que falten.

De esta manera, iremos poco a poco afinando y puliendo la técnica del testing.

```

### Qué es un convenio ?
```
Es un acuerdo de voluntades. Dícese de ese tipo de normas que debes de tener a la hora de escribir código.

Esto permite que varios desarrolladores de diferentes partes del mundo, puedan trabajar juntos sin tener 
conflictos de sintaxis.

Al tratar una norma de escritura, todos se entienden mejor.

El uso de patrones o plantillas permite que nuestro código sea agnóstico al lenguaje del habla de cada
persona.

Piensa que tu hablas español y tu compañero que colabora en un repositorio habla chino.
Seguro que si ambos escribís en un mismo lenguaje de programación con unas normas mínimas, os entenderéis
dando igual la procedencia.

```

### Qué patrones vamos a usar ?

```
Incidiendo en la estructura de cómo vamos a definir el contenido de un método, vamos a usar un estándar.
Tu por ahora no tendras que hacer nada, simplemente absorver información.

Cuando testeemos, debemos de ser limpios y concisos.
Hay que escribir lo mínimo viable e intentar ser lo máximo expresivo posible.

Para ello vamos a usar el patrón AAA.
Dicho patrón define el cuerpo de un test en tres partes. 


* Arrange (Organizar/Inicializa) => inicializa los objetos y establece los valores de los datos 
                                    que vamos a utilizar en el Test que lo contiene.
                                    
                                    
* Act (Actuar)                   => realiza la llamada al método a probar con los parámetros preparados 
                                    para tal fin.


* Assert (Confirmar/Comprobar)   => comprueba que el método de pruebas ejecutado se comporta tal y 
                                    como teníamos previsto que lo hiciera.
                                   
Este concepto puede ser bueno a la hora de implementar pequeños métodos.
```

#### Definición de un Test normal

```js
test('Sum 1 + 2 to equal 3', function () {
  expect(sum(1, 2)).toBe(3);
});

```

#### Definición de un Test con Patrón AAA

```js
test('Sum 1 + 2 to equal 3', function () {
// Arrange
var expected = 3;

// Act
var result = sum(1, 2);

// Assert
expect(result).toBe(expected);
});

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


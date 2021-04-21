# javascipt
Datos Utiles para estudiar y aprender javascipt
# Clase 1
---
## Declaracion de Variables:
### var
- Es global para todo excepto las funciones
- Permita redeclaracion
- Permite redefinicion en cualquier lugar

### let
- No se puede redeclarar
- si se puede redefinor
- solo se vé en el bloque donde se declaró

### Const
- no se puede redeclarar
- no se puede redefinir
- solo se vé en el bloque donde se declaró

## Funcion flecha o lambda
`var foo = () => {}` es lo mismo que `var foo = function(){}

### si tiene un parametro y solo hace un return se puede escribir asi
`var foo = param => item * 2` que sería lo mismo que
`var foo = item => {return item * 2}`


## Tipos de datos

### DAtos primitivos
Pasan los datos por valor
string, number, boolean, undefined, null

### Objetos
Pasan datos por referencia
object, array, funtion (la funcion es un objeto que ouede ser invocado)


## BOM Bom Object Browser
es recontra global, aca se encuentra **window**

## DOM: Document object Model
es cuando usamos **window.document**
### Para usarlo hay que poner el <script> abajo antes de cerrar el body

# Clase 2
---
## Callback
- es una funcion, la diferencia es el lugar donde se lo llama
- toda funcion puede ser un callback

## API EventTarget
- addEventListener

**Los eventos se basan en la interfez event**

- **TARGET** nos indica quien disparó el elemento

## Fases de Propagacion
### Bubling
- Fase por defecto
- Ejecuta el handler del elemento target y el de sus padres hasta llegar al **raiz**

### Capturing
- Hay que poner `true`en el tercer parametro del addEventListener() para activarlo
- Es lo inverso a Bubling

### Cancelar la propagacion

# Clase 3
---
## Eventos del formulario
### submit puede trabajar con click o con teclado

### El metodo `HTMLInputElement`.`checkValidity()` devuelve bool, verifica que el campo cumpla con las validaciones de atributos de html

### NO SE RECOMIENDA USAR SOLO  `required`

## Para obtener el valor de un input se usa
- value
**Ej.** 
>`input = documentGetelem....()`
`var valor = input.value`

## Metodos comunes:
- `input`.`setCustomValidity(mensaje)` muestra mensaje de error en formato html
- `String`.`charCodeAt()` devuelvee el unicode del caracter en cuestion
- `trim()` REcorta espacios al principio y al final
- `includes()` Se usa en arrays y string, valida lo que hay entre parentesis, tambien se usa para validar espacios entre cadenas
- `encodeURIcomponent()` cambia caracteres peligrosos para que no metan codigo malicioso. 
>Evitan los ataques XSS
La funcion se escribe sola, (no sale de ninguna parte)
EJ:encodeURIcomponent(texto)


## Expresiones Regulares:
### Definicion: secuencia de caracteres que conforman una palabra de busqueda dentro de un string

### Ventajas:
- evita tener que usar muchas funciones
- sin universales en los lenguajes de programacion

### Desventajas:
- Se puede volver dificil de leer y entender

### La expresion regular se define dentro de //
- `let regexp = /algo/`

### Caracters especiales
- `\w` cualquiel caracter alfanumerico
- `\W` negacion de \w
- `\d` solo digitos
- `\D` negacion de \d
- `\s` espacios, saltos de linea, etc.
- `\S` negacion de \s

### Caracteres de cantidad
- `{n,m}` n-->min, m --> max
- `l{2}` que la l esté dos veces
- `abc{2}` que la c se repita dos veces
- `(abc){2}` que abc se repita dos veces
- `*` entre 0 o muchas
- `+` entre 1 o muchas

### Caracteres de posicion
- `^` busca que caracter especial se encuentre al comienzo de un string, pero no de una palabra
- `$` igual pero al final
- `\b` busca tanto al comienzo como al final

# Clase 4

## Sincrono y Asincrono
Asincrono: La ejecucion no afecta a las funciones sincronicas, de hecho estas se ejecutan antes que las asincronicas
- Javascript utiliza el modelo asincrono y no bloqueante (ver apunte)

## HTTP
Protocolo por el cual transferimos datos en la web
### Componentes
HEADER
-Atributos
>content-length: determina el tamaño del recurso en bytes
content-type: determina el tipo de recurso (jpg, html, etc)

## Callstack
- tiene las instrucciones que deben ejecutarse
- es lifo

## Callback
- pieza fundamental en la asincronia
- es una funcion que se pasa como argumento de otra funcion
- NO son los primeros en salir de la pila de eventos

## Ajax
XMLHttpRequest API
- Proporciona una forma facil de obtener informacion de una URL sin recargar la pagina
- Admite mas formatos que el XML

### Eventos y/o Metodos
- ReadyStateChange **Tambien puede ser evento**
> se dispara cada vez que la propiedad readystate cambia
- abort()
>aborta la solicitud en cualquier momento, pero recarga la pag o algo asi
- send
>Nos permite enviar el pedido una vez que lo hayamos configurado
La solicitud se tiene que hacer en un **POST**
### Propiedades
Se completa cuando el pedido fue despachado y se haya descargado la info necesaria
- load Se ejecuta cuando el **readystate** está en 4 (sin saber si el status es 200 o 404, etc)

# Clase 5

# Single Page Application
- es un sitio web que cabe en una sola pagina (similar a una desktop app)
- cuando se reemplaza parte del contenido se crea un historial de navegacion (puede ser ventaja o desven)
## Desventajas
- no se puede compartir el link
- si no guardo historial y retrocedo, me voy a otro dominio

## location.hash
- Si agrego esto `window.history.pushState(null,"",e.target.href);` lo que hace es agregar en la url lo que está en el tercer parametro, pero con un # adelante


## History API
- Permite manipular el historial del cliente de cada pestaña o frame
- Es global osea que `window.history`
### Metodos/Propiedades/Eventos:
- `lock` `forward` `go` `pushState` `popstate`
- `popstate` se dispara cada vez que el usuario intenta retroceder o avanzar en su historial

## REST API
- permiten que
los sistemas solicitantes accedan y manipulen las representaciones textuales de los recursos web mediante el uso de un conjunto uniforme y predefinido de operaciones sin estado

### Conceptor generales para una API
1. Uso correcto de las URLs
● URI de base
● URI de cada recurso
> - DEben ser unicas
 - no puede representar acciones ni formatos

● Parametros de filtrado
>Se utilizan parametro en formato http, ejemplo:
www.misitio.com/usuarios?fecha_registro=2018-01-01&orderAsc=edad

2. Uso correcto de HTTP
● Métodos
● Códigos de estado
● Formato
>Se indicarn los formatos en que se van a devolver los recursos(se pueden poner varios y ordernarlos por prioridad)
Si no puede devolver ninguno devuelve codigo **406**

## CORS
Cross Origin Resource Sharing (compartir fuentes de origenes cruzados)
- Permite que un servidor pida recursos a otro de diferente dominio
- por seguridad los browser restingen solicitudes cruzadas solicitadas desde un script **salvo que se use CORS**

## JSONP
- tecnica para evitar el cross origin error ya que permite la comunicacion para hacer pedidos asincronos a dominios diferentes
- la idea es suplir la limitacion de ajax entre dominios distintos
> esta restriccion no aplica a script dentro de html, el problema es que html no puede interpretar lo que le devolveria ese script
- Con jsonp el objeto json se devuelve en un callback que despues manipulamos a gusto (--?

# Clase 6
- El uso principal de xhr es con **texto - html - xml**
- Pero se puede usar el XMLHttpRequest para el envio de datos que no sean los nombrados anteriormente
- **Unmetodo viejo era**para eso se utiliza el metodo `xhr.overrideMimeType("text/plain; charset=x-user-defined")`

## Blob API
- La interfaz **URL** tiene el metodo **createObjectURL** permite que sea legible un objeto que se le pase por parametro para usarlo en el DOM donde se llamo al metodo
- `URL.createObjectURL(obj)`


### ResponseType
- **hoy en dia** se usa esta propiedad para cmabiar el tipo de respuesta que viene en el response

- **Ejemplo:** ver pagina 2 de teoria

## Evento progress
- se ejecuta cuando readyState está = 3
- variables
> - loaded, total, lengthComputable
- se usa con el tag <progress> en html
> - tiene los atributos: value y max

- EL metodo **POST** permite cargar mas archivos y mas pesados.

## API DRAG AND DROP

- Eventos
> - dragenter
 - dragleave
 - dragover
> - drop

- cuando se usa drop
>

## API FORM DATA
- puede tomar datos de un form 
> let data = new FormData(form)
- tambien los puede tomar de inputs(--? sueltos, pero de forma manual
- tambien puede serializar recursos

# Clase 7
## Promise
- Representacion de un valor eventual pero que no sabemos (--?
- la ventaja es que ya te da un valor (--?
- tiene una funcion que se llama resolver, y esta adentro tiene otras dos funciones
> - resolved
> - rejected
- tiene tres estados
> - pending
> - resolved
> - rejected

### Para probarlo en el codigo escribir
`let pro = new Promise(()=>{})`
- con eso deberia poder empezar

## Fetch
- es como xhr pero mas potente
- mezcla xhr + promise + response + request + body + header

# Clase 8
## Objetos
### Formas de crear un objeto
- literales
>`let a = {}`
- Constructor
- Create
>`let proto = {cosa1: "cosa" , cosa2: function(){//algo}}`
>`let b = Object.create(proto);`

### los objetos tienen 4 propiedades basicas
- value
- writable (bool, false por defecto --> si admite escritura)
- enumerable (bool, false por defecto --> admite iterabilidad)
- configurable (bool, false por defecto --> admite borrado)

Estas propiedades vienen `false` por defecto

## Funciones
### son objetos
- son variadicas
>No dependen de la cant de argumentos o parametros
- tienen Ambito
- Tienen Contexto

### Ambito
- Alcance de la funcion (similar al de otros lenguajes JAVA, C#), pero agrega los **CLOSURE**
>
#### Ambito Lexico
permite acceder al ambito de una funcion exterior con una funcion interior

#### Closure
Es un objeto que tiene una funcion y el entorno donde se creó

### Contexto
- Por defecto las funciones son contenidas en WINDOW
- El contexto NO es ESTATICO
- Se utiliza el objeto `this` el cual siempre debe ser un objeto, por defecto es **window**

#### Hay varias formas de llamar una funcion
Forma | Descripcion 
---|---
normal | no se que poner
bind call apply | Dentro del prototipo de la funcion |
new | es un operador




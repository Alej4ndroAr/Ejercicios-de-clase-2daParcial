 Apuntes 2da parcial
---
###### Andrade Romero Jesús Alejandro
-----------------------
## Funciones
Una función es un bloque de código reutilizable que realiza una tarea específica. Las funciones se utilizan para organizar y modular el código, lo que facilita la escritura, lectura y mantenimiento de programas.

**Sintaxis de una funcion**
``` python
def <function_name>([<parameters>]):
    <statement(s)>
```
##### Caracteristicas:
##### **`1. Definición de funciones:`**

   - Para definir una función en Python, utilizamos la palabra clave `def`, seguida del nombre de la función y un par de paréntesis `()`. El nombre de la función debe seguir las reglas de nomenclatura de Python, que generalmente significa que debe consistir en letras, números y guiones bajos, y no puede comenzar con un número.
   - Después de los paréntesis, se coloca un colon `:` para indicar el comienzo del cuerpo de la función. El cuerpo de la función contiene una o más instrucciones que se ejecutarán cuando se llame a la función.

   Ejemplo:
```python
   def saludar():
       print("Hola, mundo!")
```

##### **`2. Parametros y argumentos:`**

Las funciones pueden recibir cero o más parámetros (también llamados argumentos). Estos parámetros son valores que se pasan a la función y se utilizan en el cuerpo de la función para realizar cálculos o ejecutar acciones.
    
###### **-Argumentos posicionales (obligatorios):**
* La forma más sencilla de pasar argumentos a una función de Python es con argumentos posicionales u obligatorios.
```python
def productos(producto, cantidad, precio):
    print(f" {cantidad} {producto} cuestan {precio} pesos")

productos("manzanas", 5, 7.5)
```
* Los parámetros (producto, cantidad y precio) se comportan como variables definidas localmente en la función.
* Cuando se llama a la función, los argumentos que se pasan ("manzanas", 5, 7.5) están vinculados a los parámetros en orden
* Como si fuera una asignación de variables:

| Parámetro | Argumento |
|-----------|-----------|
|producto   |manzanas   |
| cantidad  | 5         |
| precio    | 7.5       |

* Los argumentos posicionales son la forma más sencilla de pasar datos a una función
* Ofrecen la menor flexibilidad.
* El orden de los argumentos en la llamada debe coincidir con el orden de los parámetros en la definición. 


###### **-Argumentos nombrados o de palabra clave (Keyword arguments):**

* Cuando se invoca a una función se pueden especificar los argumentos en el formato
 <palabra_clave>=\<valor>.
* Cada <palabra_clave> debe coincidir con un parámetro en la definición de la función de Python. 
* Por ejemplo, la función productos() se puede invocar con argumentos de palabras clave de la siguiente manera:
```python
productos(producto="manzanas", cantidad=5, precio=7.5)
```

* Los argumentos de palabras clave permiten flexibilidad en el orden en que se especifican los argumentos de una función
* El número de argumentos sigue siendo estricto, deben estar todos.
* Se puede llamar a una función utilizando argumentos posicionales y de palabras clave
* Todos los argumentos posicionales deben ir primero
 
###### **-Parámetros por defecto (default)**
* Se especifica en una definición de función de Python de la forma <nombre>=\<valor>
* \<valor> se convierte en un valor predeterminado para ese parámetro.
* Se denominan parámetros predeterminados u opcionales. 
* Ejmplo:
```python
def productos(producto="productos", cantidad="0", precio=0.0):
    print(f" {cantidad} {producto} cuestan {precio} pesos")

# Invocación sin argumentos
productos()
#-------------------------------------------
# Invocación con argumentos posicionales
productos("manzanas",5,5.5)
#---------------------------------------------
# Invocación con argumentos nombrados o de palabra clave
productos(producto="manzanas", cantidad=5, precio=5.5)
```
-----

###### **-Retorno de valores y uso de palabra clave "return":**
* Una instrucción *return* en una función de Python tiene dos propósitos:
1. Al terminar la función devuelve el control de ejecución a partir de donde se llamó.
2. Proporciona un mecanismo para regresar datos donde se llamó o asignó.
```python
def f1():             
    print("Hola")
    print("Mundo")
    return

f1()
```
Hola
Mundo
```python
def f2():             
    print("Hola")
    print("Mundo")
f2()
```
Hola
Mundo
* *return* no necesita estar al final de una función.
* Pueden aparecer en cualquier parte del cuerpo de una función
* Puede aparecer incluso varias veces 
--------------------------
#### Valor de retorno en funciones:
* Una función puede devolver cualquier tipo de objeto.
 Ejemplo: diccionario
```python
names =  dict(name_1='Hugo', name_2='Paco', name_3='Luis') #hecho en clase
names
```
{'name_1': 'Hugo', 'name_2': 'Paco', 'name_3': 'Luis'}

* Retornar listas que se pueden indizar o dividir:
```python
names =  dict(name_1='Hugo', name_2='Paco', name_3='Luis') #hecho en clase
names
```
['a', 'b', 'c', 'd', 'e']

##### **`3. Recursion:`**
##### Definición de funciones recursivas.
Una definición recursiva es aquella en la que el término definido aparece en la propia definición.
* Capacidad de una función de llamarse a sí misma
* La mayoría de los problemas de programación se pueden resolver sin recursividad. 
* Entonces... la recursividad no suele ser necesaria.
```python
def contar_hasta_n(n):
    if n <= 0:
        return
    else:
        print(n)
        contar_hasta_n(n - 1)

contar_hasta_n(5)
```
En este ejemplo, la función contar_hasta_n" toma un número "n" como argumento y, si "n" es mayor que 0, imprime el valor de "n" y luego llama a la función "contar_hasta_n" con "n-1". Esto crea una serie de llamadas recursivas que imprimirán los números en orden descendente desde "n" hasta 1. Cuando "n" llega a 0, la función se detiene, lo que sirve como el caso base de la recursión.
* Las funciones recursivas suelen un patrón:
    * Hay uno o más casos base que se pueden resolver directamente sin necesidad de más recursividad.
    * Cada llamada recursiva acerca progresivamente la solución a un caso base (mecanismo de retorno).
##### Casos base y casos recursivos:
* Ejemplo: Cuenta regresiva hasta cero
```python
# cuenta regresiva no recursiva (iterativa)
def cuenta_regresiva(n):
    while n >= 0:
        print(n)
        n -= 1
cuenta_regresiva(5)
```
 5
 4
 3
 2
 1
 0
 
````python
# cuenta regresiva recursiva
def cuenta_regresiva(n):
    print(n)
    if n == 0:
        return                      # Fin de la recursión, caso base
    else:
        cuenta_regresiva(n - 1)     # Llamada recursiva
cuenta_regresiva(5)
````
5
4
3
2
1
0
* El caso base se produce cuando n es cero, momento en el que se detiene la recursividad.
* En la llamada recursiva, el argumento es uno menos que el valor actual de n, por lo que cada recursividad se acerca al caso base.
------------------------------------------------------
## Ejercicios en "Guizero":
##### **`-Creando una Aplicación GUI con Guizero`**

El siguiente código es un ejemplo de cómo crear una aplicación de interfaz gráfica de usuario (GUI). Esta aplicación creará una ventana con el título "Hello world".

```python
from guizero import App

# Crear una instancia de la aplicación con el título "Hello world"
app = App(title="Hello world")

# Mostrar la ventana de la aplicación
app.display()
````
**"from guizero import App"**: Esta línea importa la clase App de la biblioteca guizero, que se utilizará para crear la aplicación GUI.

**"app = App(title="Hello world")"**: Aquí se crea una instancia de la aplicación (app) con un título específico, que en este caso es "Hello world".

**"app.display()"**: Esta línea muestra la ventana de la aplicación en la pantalla del usuario, lo que permite interactuar con la interfaz gráfica.

-----------------------------------------
##### **`-Creando una Aplicación GUI que muestra un mensaje luego de oprimir un boton generado`**
````python
from guizero import App, Text, PushButton
# Definir una función llamada say_hello que se ejecutará cuando se haga clic en el botón
def say_hello():
    message_2.value = "ICI Rocks!"  # Cambia el valor de message_2 cuando se hace clic

app = App("ICI App")

# Crear un objeto "Text" llamado "message" y mostrar un mensaje en la ventana de la aplica-ción
message = Text(app, text="Welcome to the ICI App!")
message_2=Text(app)
button = PushButton(app, text="Click me!", command=say_hello)

app.display()

````
**1.-** Importa las clases App, Text y PushButton de la biblioteca guizero.

**2.-** Define una función llamada "say_hello" que se ejecutará cuando se haga clic en el botón. Esta función cambia el valor del objeto "message_2" a "ICI Rocks!".

**3.-** Crea una instancia de la clase "App" llamada "ICI App". Esto crea la ventana principal de la aplicación.

**4.-** Crea un objeto Text llamado "message" y muestra el mensaje "Welcome to the ICI App!" en la ventana de la aplicación.

**5.-** Crea un objeto Text llamado "message_2", que inicialmente no contiene ningún texto. Este objeto se utilizará para mostrar un mensaje diferente cuando se haga clic en el botón.

**6.-** Crea un botón llamado "button" con el texto "Click me!" y lo asocia a la función say_hello utilizando el parámetro command.

------------------------------------




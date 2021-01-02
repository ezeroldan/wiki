# Python

- `"""` Comentario Multilinea
- `# Comentario` Comentario Linea
- `#!/usr/bin/env python3`

## Metodos Gnerales
- `print(string1, string2)` Imprime contenido, concatena con espacios. Le suma un enter
- `str()` Convierte un int a string
- `int()` Convierte un string a un int
- `float()` Convierte a un Decimal
- `type()` Retorna el tipo
- `exit()` FInlizar
- `help()` Muestra el debug
- `open()` Abrir un archivo

## Strings
- `"\n"` Nueva Linea
- `"texto {} otro {} texto".format(value1, value2)`
- `"texto {var} texto {var} texto".foramt(var=value)`
- `"texto".strip()` Eliminar espacios
- `variable[start:end]` Segmentar un string con `[:]`
- `variable.lower()` Lowercase
- `variable.uper()` Uppercase
- `variable.title()` Capitalize

## Ingresar datos por el Usuario en consola
Siempre retorna un string
- `input("Pregunta: ")` Obtener datos del usuario en consola
- `variable = input("Pregunta:")` Pasar lo ingresado a una variable

## Funciones
```python
def calcular_segundos():
    edad = input("Cuantos anios tenes? ")
    segundos = int(edad) * 365 * 24 * 60 * 60
    print("En total viviste {} Segundos".format(segundos))

calcular_segundos()
```

- `def nombre(valor = 'default', valor2 = 'default2')` Parametros
- `nombre(valor2='otro')` Solo cambiar defaultde un parametro
- `return` Para devolver resultado


## If Condicional
- `if a > b:`
- `if a > b and c > a:`
- `if a > b or a > c:`
- `print("A") if a > b else print("B")`

```python
var = 2
if var == 1:
    print("Es 1")
elif var == 2:
    print("Es 2")
else:
    print("Es 0")
```

## Arrays
```python
letras = ["a", "b", "c"]

print(letras[0])  # Impimir a
print(letras[1])  # Impimir b

print(letras[-1]) # Impimir c
print(letras[-2]) # Impimir b

del letras[1] # Borra la b

for letra in letras:
    print(letra)
```

- `variable.sort()` Ordenar el array
- `variable.sort(reverse = True)` Ordenar el array inversamente
- `variable.reverse()` Ordenar el array inversamente
- `len(variable)` Conut del array
- `min(variable)` Retorna el valor Minimo
- `max(variable)` Retorna el valor Maximo
- `sum(variable)` Suma todos los valores
- `variable[start:end]` Slide un array
- `viriable2 = variable[:]` Para copiar un array, de lo contrario hace refenrecia la original (como en js)
- `if "a" and "c" in variable:` Valor existente en array
- `if "d" not in variable:` Valor no existente en array

## Tuples
```python
tup = (200, 50)

print(tup[0])
print(tup[1])

```

## Range => for i
```python
for i in range(1, 5):
    print(i)
```

## Dictionaries
```python
dic = {'nombre': 'Ezequiel', 'apellido': 'Roldan'}

print(dic['nombre'])
print(dic['apellido'])

dic['edad'] = 28

del dic['nombre']
```

## While
```python
while i <=6:
    print(i)
    i+=1
```
- `break` Interrumpe el loop
- `continue` Recetea el loop

## Clases
```python
class NombreClase():

    def __init__(self, dato = 'prueba'):
        self.dato = dato
    
    def funcion(self, param):
        self.param = param
        return self.dato + ' ' + self.param

# Instanciar clase
prueba = NombreClase()
prueba.funcion('valor')

print(prueba.dato)
```
- `def funcion(self, param):` Se pasa self como param para acceder a la clase misma
- `def __init__(self, param):` Constructor de la clase

### Inheritance
```python
class Padre():
    ojos = 'verdes'

class Madre():
    pelo = 'castanio'

class Hijo(Padre, Madre):
    edad = 10

hijo = Hijo()
print(hijo.edad, hijo.ojos, hijo.pelo)

```

- `class Hijo(Padre):` La clase que se hereda se pasa por los ()
- `class Hijo(Padre, Madre):` Clases pueden heredar de varias clases
- `pass` Indica que herede los metodos

## Modulos

### requirements.txt
- `requirements.txt` Seria como el composer.json o el package.json
- `requests==2.7.0` Libreria como axios
- `beautifulsoup4==4.4.0` Libreria para parsear HTML

### pip
```bash
pip install requests            # latest version
pip install requests==2.7.0     # specific version
pip install 'requests>=2.7.0'   # minimum version
```

### Modulos Locales
```python
from carpeta.archivo import *
from carpeta.archivo import funcion
```


```python
import requests
request = requests.get('https://www.google.com')
print(request.content)
```

```python
from bs4 import BeautifulSoup
soup = BeautifulSoup(content, "html.parser")
element = soap.find("span", {"id": "algo", "class": "algo"})
print(element.text)
```



# python
Recordando Python.....
El año pasado en el curso de Método numéricos, a los estudiantes de ICC, tuve que recordar mi programación en Python, y usamos el Google Colab ( https://colab.research.google.com/?hl=es  )

# Código
```python
import math
import numpy as np
from scipy.integrate import quad

def simpson13(f, a, b, n):
    h = (b - a) / n
    sum = 0
    for i in range(1,n):
      x = a + i*h
      if i % 2 == 0:
        sum+= 2*f(x)
      else:
        sum += 4*f(x)
    sum = h/3 * (f(a) + f(b) + sum)
    return sum

def trapecio(f, a, b, n):
  sum = 0
  h = (b-a)/n
  for i in range(2, n+1):
    x = a+(i-1)*h
    sum += f(x)
  res = (h/2)*(f(a)+f(b)+2*sum)
  return res
```
# Función 

```python
func = lambda x: 4*(1-x**2)**(0.5) # area circulo radio 1.
a = 0
b = 1

resultado_s = simpson13(func, a, b, 10)
resultado_t = trapecio(func, a, b, 10)
real = quad(func, a, b)[0]
error_s = abs(resultado_t-real)
error_t = abs(resultado_s-real)
print("Simpson: ", resultado_s)
print("Trapecio: ", resultado_t)
print("Valor real: ", real)
print("Error Simpson: ", error_s)
print("Error Trapecio: ", error_t)
```

# Resultados
```python
Simpson:  3.127008158703241
Trapecio:  3.1045183262483182
Valor real:  3.1415926535897922
Error Simpson:  0.03707432734147398
Error Trapecio:  0.014584494886551447
```

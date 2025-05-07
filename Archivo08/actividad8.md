# Ejercicio 1: Método para vaciar el carrito

![ee](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo08/img/codi1.png)

Se creo la funcion test_vaciar_carrito(), para vaciar el carrito, luego se va a averificar si la lista de productos este vacio y el total de cosas sea 0.
# Ejercicio 2: Descuento por compra mínima


Se creo un nuevo metodo "aplicar_descuento_condicional(porcentaje, minimo).
Luego de eso se procedio a hacer pruebas para los escenarios(se creo la funcion aplicar_descuento_condicional).

![ee](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo08/img/1.md.png)


![ee](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo08/img/2.png)

Al final se ejecuto el test, teniendo previamente instalado el comando "pytest" dentro de Visual Studio Code y al final y se obtuvo el resultado de arriba.
# Ejercicio 3: Manejo de stock en producto

Se creo la funcion agregar_ producto(), que permite que funciones bien el trabajo. Despues procedimos  a hacer 
![ee](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo08/img/2m.png)


![ee](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo08/img/3.png)
Al final se ejectura todo.



# Ejercicio 4: Ordenar artículos del carrito

Se procedio a crear la funcion "obtener_items_ordenados", con la intencion de devolver los items de los carritos ordenados por precio o nombre,
Sino cumple ninguna de ls criterios(ya sean preio o nombre),  entonces se devuelve un error.

![ee](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo08/img/3m.png)



![ee](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo08/img/4.png)

Al final se tuvo esta ejecucion

# Ejercicio 5: Uso de accesorios de Pytest




![ee](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo08/img/5.png)


# Ejercicio 6: Pruebas parametrizadas


Se creo la funcion para parametrizar descuentos : 

![ee](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo08/img/6md.png)

Tambien se procedieron a hacer cambios.

![ee](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo08/img/6.png)

Al final se tiene el resultado en verde de la ejecucion, lo cual significa que esta bien todo lo trabajado.

# Ejercicio 7: Calcular impuestos en el carrito

![et](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo08/img/7a.png)

Se procede a ver el error a la hora de ejecutar "pytest".Tal como se habia pedido

# Ejercicio 8: Aplicar cupón de descuento con límite máximo

```
# tests/test_cupon.py
import pytest
from src.carrito import Carrito
from src.factories import ProductoFactory

def test_aplicar_cupon_con_limite():
    """
    Red: Se espera que al aplicar un cupón, el descuento no supere el límite máximo.
    """
    # Arrange
    carrito = Carrito()
    producto = ProductoFactory(nombre="Producto", precio=200.00)
    carrito.agregar_producto(producto, cantidad=2)  # Total = 400

    # Act
    total_con_cupon = carrito.aplicar_cupon(20, 50)  # 20% de 400 = 80, pero límite es 50

    # Assert
    assert total_con_cupon == 350.00
```

Crea un archivo, por ejemplo, tests/test_cupon.pyy escribe una prueba que verifique que haya un porcentaje de compra

# Ejercicio 9: Validación de stock al agregar productos (RGR)
Se escribe una falla:
En un nuevo archivo, por ejemplo tests/test_stock.py,
```
# tests/test_stock.py
import pytest
from src.carrito import Carrito, Producto

def test_agregar_producto_excede_stock():
    """
    Red: Se espera que al intentar agregar una cantidad mayor a la disponible en stock se lance un ValueError.
    """
    # Arrange
    # Suponemos que el producto tiene 5 unidades en stock.
    producto = Producto("ProductoStock", 100.00)
    producto.stock = 5
    carrito = Carrito()

    # Act & Assert
    with pytest.raises(ValueError):
        carrito.agregar_producto(producto, cantidad=6)
```

Se implementa: agregar_productoCarrito para validar el stock y lueog se refactoriza

## Ejercicio 1: Método para vaciar el carrito


Agregue el método vaciaren src/carrito.pyque realiza self.items = [].




Crea pruebas en tests/test_carrito.pyque agreguen varios productos, invoquen vaciar()y verifiquen que obtener_items()regresen una lista vacía y calcular_total()regresen 0.




![ee](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo8/img/codi1.png)

## Ejercicio 2: Descuento por compra mínima

Agregue un nuevo método, por ejemplo, aplicar_descuento_condicional(porcentaje, minimo)en la clase Carritoque primero verifique si calcular_total() >= minimo.




Si se cumple la condición, aplica el descuento; De lo contrario, retorna el total sin descuento.



Escribe pruebas para ambos escenarios (condición cumplida y no cumplida).

![ee](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo8/img/2.png)

## Ejercicio 3: Manejo de stock en producto

Modifica Productoen src/carrito.pyagregando self.stock = stocken el constructor y actualiza la fábrica en src/factories.pypara que genere un stock (por ejemplo, entre 1 y 100).



En Carrito.agregar_producto, antes de agregar o incrementar la cantidad, verifique que la suma de cantidades en el carrito no supere el stockproducto.



Escribe pruebas que verifiquen:
Se puede agregar un producto dentro del límite de stock.
Se lanza una excepción al intentar agregar más unidades de las disponibles.

![ee](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo8/img/3.png)

## Ejercicio 4: Ordenar artículos del carrito
Crea un método obtener_items_ordenados(criterio: str)donde criteriopuedas ser "precio"o "nombre".



Utiliza la función sorted()con una función lambda para ordenar según el criterio.



Escriba pruebas que verifiquen que, al agregar varios productos, la lista de vuelta esté ordenada correctamente según el criterio solicitado.

![ee](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo8/img/4.png)
## Ejercicio 5: Uso de accesorios de Pytest

En el archivo tests/conftest.py, crea un accesorio para un carrito vacío:
import pytest
from src.carrito import Carrito

@pytest.fixture
def carrito():
    return Carrito()

    
Crea también un accesorio para un producto genérico, usando la fábrica:
import pytest
from src.factories import ProductoFactory

@pytest.fixture
def producto_generico():
    return ProductoFactory(nombre="Genérico", precio=100.0)


    
Actualiza las pruebas existentes para usar estos dispositivos en lugar de instanciar los objetos directamente en cada prueba.


![ee](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo8/img/5.png)
## Ejercicio 6: Pruebas parametrizadas

Por ejemplo, parametriza pruebas para aplicar_descuentousar distintos porcentajes y totales esperados.


De igual forma, para actualizar cantidades: pruebe con diferentes valores (válidos e inválidos) y verifique que se lanza la excepción en los casos correspondientes.

![ee](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo8/img/6.png)
## Ejercicio 7: Calcular impuestos en el carrito
Rojo
Escribir la prueba que falla:


Crea un nuevo archivo de pruebas (por ejemplo, tests/test_impuestos.py) y escribe una prueba que espere que, dado un carrito con un total de $1000, al aplicar un 10% de impuestos se retorna $100.

# tests/test_impuestos.py
import pytest
from src.carrito import Carrito
from src.factories import ProductoFactory

def test_calcular_impuestos():
    """
    Red: Se espera que calcular_impuestos retorne el valor del impuesto.
    """
    # Arrange
    carrito = Carrito()
    producto = ProductoFactory(nombre="Producto", precio=250.00)
    carrito.agregar_producto(producto, cantidad=4)  # Total = 1000

    # Act
    impuesto = carrito.calcular_impuestos(10)  # 10% de 1000 = 100

    # Assert
    assert impuesto == 100.00
En este punto, la prueba fallará porque el método calcular_impuestosaún no existe.

Verde
Implementar el código mínimo:
En src/carrito.py, añade el método de forma mínima para que la prueba pase:
![ee](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo8/img/7a.png)
# Dentro de la clase Carrito en src/carrito.py

def calcular_impuestos(self, porcentaje):
    total = self.calcular_total()
    return total * (porcentaje / 100)
Refactor
Refactorizar:

Agrega validaciones para que el porcentaje esté en un rango razonable (por ejemplo, entre 0 y 100).
Agregue documentación al método.
def calcular_impuestos(self, porcentaje):
    """
    Calcula el valor de los impuestos basados en el porcentaje indicado.
    
    Args:
        porcentaje (float): Porcentaje de impuesto a aplicar (entre 0 y 100).
    
    Returns:
        float: Monto del impuesto.
    
    Raises:
        ValueError: Si el porcentaje no está entre 0 y 100.
    """
    if porcentaje < 0 or porcentaje > 100:
        raise ValueError("El porcentaje debe estar entre 0 y 100")
    total = self.calcular_total()
    return total * (porcentaje / 100)



## Ejercicio 8: Aplicar cupón de descuento con límite máximo
Objetivo:
Implementar un método aplicar_cupon(descuento_porcentaje, descuento_maximo)que aplica un cupón de descuento al total del carrito, pero asegurándose de que el descuento no supere un valor máximo.

Rojo
Escribir la prueba que falla:
Crea un archivo, por ejemplo, tests/test_cupon.pyy escribe una prueba que verifique que, para un carrito con total $400 y un cupón del 20% (lo que daría $80), si el descuento máximo es $50, el método devolverá $350.

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
Verde
Implementar el código mínimo:
En src/carrito.py, añade un método para aplicar el cupón de descuento de forma básica:

def aplicar_cupon(self, descuento_porcentaje, descuento_maximo):
    total = self.calcular_total()
    descuento_calculado = total * (descuento_porcentaje / 100)
    descuento_final = min(descuento_calculado, descuento_maximo)
    return total - descuento_final
Refactor
Refactorizar:

Agrega validaciones para que el porcentaje de descuento y el máximo sean valores positivos.
Separa la lógica de cálculo y validación, y documenta el método.
def aplicar_cupon(self, descuento_porcentaje, descuento_maximo):
    """
    Aplica un cupón de descuento al total del carrito, asegurando que el descuento no exceda el máximo permitido.
    
    Args:
        descuento_porcentaje (float): Porcentaje de descuento a aplicar.
        descuento_maximo (float): Valor máximo de descuento permitido.
    
    Returns:
        float: Total del carrito después de aplicar el cupón.
    
    Raises:
        ValueError: Si alguno de los valores es negativo.
    """
    if descuento_porcentaje < 0 or descuento_maximo < 0:
        raise ValueError("Los valores de descuento deben ser positivos")
    
    total = self.calcular_total()
    descuento_calculado = total * (descuento_porcentaje / 100)
    descuento_final = min(descuento_calculado, descuento_maximo)
    return total - descuento_final

## Ejercicio 9: Validación de stock al agregar productos (RGR)
Objetivo:
Asegurarse de que al agregar un producto al carrito, no se exceda la cantidad disponible en stock.

Rojo
Escribir la prueba que falla:
En un nuevo archivo, por ejemplo tests/test_stock.py, escribe una prueba que verifique que si se intenta agregar más unidades de las disponibles, se lanza una excepción.

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
Verde
Implementar el código mínimo: Modifica el
método para que valide el stock:agregar_productoCarrito

def agregar_producto(self, producto, cantidad=1):
    # Verifica el stock disponible
    total_en_carrito = 0
    for item in self.items:
        if item.producto.nombre == producto.nombre:
            total_en_carrito = item.cantidad
            break
    if total_en_carrito + cantidad > producto.stock:
        raise ValueError("Cantidad a agregar excede el stock disponible")
    
    # Si el producto ya existe, incrementa la cantidad
    for item in self.items:
        if item.producto.nombre == producto.nombre:
            item.cantidad += cantidad
            return
    self.items.append(ItemCarrito(producto, cantidad))
Refactor
Refactorizar:

Centraliza la validación del stock en un método privado o en la clase Productosi es necesario.
Documente la función y separa la lógica de búsqueda del producto en el carrito.
def _buscar_item(self, producto):
    for item in self.items:
        if item.producto.nombre == producto.nombre:
            return item
    return None

def agregar_producto(self, producto, cantidad=1):
    """
    Agrega un producto al carrito verificando que la cantidad no exceda el stock disponible.
    
    Args:
        producto (Producto): Producto a agregar.
        cantidad (int): Cantidad a agregar.
    
    Raises:
        ValueError: Si la cantidad total excede el stock del producto.
    """
    item = self._buscar_item(producto)
    cantidad_actual = item.cantidad if item else 0

    if cantidad_actual + cantidad > producto.stock:
        raise ValueError("Cantidad a agregar excede el stock disponible")
    
    if item:
        item.cantidad += cantidad
    else:
        self.items.append(ItemCarrito(producto, cantidad)) 


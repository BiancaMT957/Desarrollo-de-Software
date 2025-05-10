# Paso 1: Instalar pytest y pytest-cov
Procedi a instalar Pytest-cov de Python

![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo10/img/y1.png)


![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo10/img/y2.png)


# Paso 2: Escribiendo y ejecutando pruebas con pytest



![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo10/img/y3.png)


Corri todos los 11 tests ejecutando pytest –v


![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo10/img/y4.png)


# Paso 3: Añadiendo cobertura de pruebas con pytest-cov
## Ejecuto pytest -v --cov=triangle:
Esto me permite tener un enfoque mas detallado de todos los tests que pasaron, con sus respectivo porcentaje. Es una vista mas atractiva del trabajo que las otras maneras.

![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo10/img/y5.png)

## Otra manera :
pytest --cov=triangle --cov-report=term-missing

![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo10/img/y6.png)


Una manera interesante de verlo con un reporte html.
pytest --cov=triangle --cov-report=term-missing --cov-report=html

# Paso 4: Añadiendo colores automáticamente
De echo sino esta configurado eso del ccambio de color, entonces se agrega.


![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo10/img/y7.png)


## Paso 5: Automatizando la configuración de pytes


![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo10/img/y8.png)

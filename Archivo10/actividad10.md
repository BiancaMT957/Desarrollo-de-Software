# Paso 1: Instalar pytest y pytest-cov
Procedi a instalar Pytest-cov de Python


# Paso 2: Escribiendo y ejecutando pruebas con pytest
Corri todos los 11 tests ejecutando pytest –v
# Paso 3: Añadiendo cobertura de pruebas con pytest-cov
## Ejecuto pytest -v --cov=triangle:
Esto me permite tener un enfoque mas detallado de todos los tests que pasaron, con sus respectivo porcentaje. Es una vista mas atractiva del trabajo que las otras maneras.
## Otra manera :
pytest --cov=triangle --cov-report=term-missing
## Una manera interesante de verlo con un reporte html.
pytest --cov=triangle --cov-report=term-missing --cov-report=html

## Paso 4: Añadiendo colores automáticamente

## Paso 5: Automatizando la configuración de pytes

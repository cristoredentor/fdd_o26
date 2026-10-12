# Decisiones: de ventas_ia.py a practica.py

## Qué cambié, por qué y qué patrón

Al menos tres filas. El patrón es uno de los ocho de la página «Patrones y
el stack escrito».

| Qué cambié | Por qué | Qué patrón |
|---|---|---|
|Puse documentación a los métodos|Para ayudar al mantenimiento del código| |
|Cambie pandas por polars|Como vimos en clase polars tiene muchas ventajas sobre pandas|Fuera del intérprete es rápido|
|`.apply(lambda ...)` → `pl.col("cantidad") * pl.col("precio")`|`.apply` recorre fila por fila en Python; la expresión opera la columna completa|Fila vs columna|
|`cantidad: Optional[int]` → `int` con `Field(gt=0)`|Con `None` permitido, pandas vuelve la columna `float`|El tipo decide la memoria|

## Salida de pytest

Pega la salida completa de `pytest -v --no-header test_practica.py`,
corrido en `stack/`. `--no-header` quita las líneas con la ruta de tu máquina.

```text
============================= test session starts ==============================
collecting ... collected 3 items

test_practica.py::test_fila_buena_se_convierte PASSED                    [ 33%]
test_practica.py::test_mala_definicion_venta PASSED                      [ 66%]
test_practica.py::test_fecha_inexistente_se_rechaza PASSED               [100%]

============================== 3 passed in 0.27s ===============================
```

## Salida de ruff

Pega la salida de `ruff check practica.py test_practica.py`.

```text
All checks passed!
```

## Salida de mypy

Pega la salida de `mypy practica.py`.

```text
Success: no issues found in 1 source file
```

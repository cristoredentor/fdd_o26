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
==================================== test session starts ====================================
collected 1 item                                                                            

test_practica.py::test_fila_buena_se_convierte PASSED                                 [100%]

===================================== 1 passed in 0.30s =====================================
```

## Salida de ruff

Pega la salida de `ruff check practica.py test_practica.py`.

```text
(.venv-stack) cris@laptop-cris:~/Documentos/ITAM/Fuentes/Github/fdd_o26/estudiantes/cristoredentor/09_python/stack$ ruff check practica.py test_practica.py
All checks passed!

```

## Salida de mypy

Pega la salida de `mypy practica.py`.

```text
(.venv-stack) cris@laptop-cris:~/Documentos/ITAM/Fuentes/Github/fdd_o26/estudiantes/cristoredentor/09_python/stack$ mypy practica.py
Success: no issues found in 1 source file
```


```
# Prompt en ChatGPT:
De todo lo que me has platicado y enseñado hay varias cosas que han llamado mi atención, lo suficiente para pedirte que me digas ¿Cómo puedo integrar todo este conocimiento y técnica a mi trabajo diario?:
Una ha sido que mencionaste Test Driven development que es un concepto que ya había escuchado con anterioridad, que si no me equivoco es un paradigma donde programas primero las pruebas.
La otra cosa que llamó mi atención fue lo de Integración continua y al ver el ejemplo

* name: Ejecutar tests
  run: |
  pip install -r requirements.txt
  pytest --maxfail=1 --disable-warnings -q
  
Realmente me hizo querer implementarlo desde ya en mis repositorios.

Otra cosa que llamó mi atención fueron las buenas prácticas que mencionas:
  -Automatiza todo lo que puedas
  ¿ Evita tener que testear manualmente cada cambio.

- Haz fallar las pruebas primero (TDD)
  Esto asegura que tu prueba es válida.

Y por ultimo mencionas que puedes decidir si necesitas tests unitarios, de integración o de sistema.

```

---

## 🧭 **Flujo de trabajo profesional con buenas prácticas, TDD y CI**

### 🛠️ 1. **Configura tu proyecto desde el inicio**

1.1. Crea tu entorno virtual:

```bash
python -m venv venv
source venv/bin/activate
```

1.2. Crea tu estructura básica:

```
my_project/
├── src/
│   └── calculadora/
│       ├── __init__.py
│       └── operaciones.py
├── tests/
│   └── test_operaciones.py
├── requirements.txt
├── .gitignore
└── README.md
```

1.3. Añade tus dependencias:

```bash
pip install pytest
pip freeze > requirements.txt
```

---

### 🧪 2. **Adopta TDD: Test-Driven Development**

> Escribe una prueba **antes** de implementar la funcionalidad.

2.1. **Paso 1:** Escribe una prueba que fallará (rojo):

```python
# tests/test_operaciones.py
def test_suma():
    assert suma(2, 3) == 5  # Falla porque aún no existe `suma`
```

2.2. **Paso 2:** Implementa la función mínima para que pase (verde):

```python
# src/calculadora/operaciones.py
def suma(a, b):
    return a + b
```

2.3. **Paso 3:** Refactoriza si es necesario (manteniendo tests verdes).

---

### 🔄 3. **Automatiza con integración continua (CI)**

3.1. Crea el archivo `.github/workflows/python-ci.yml`:

```yaml
name: Python CI

on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
    - name: Configurar Python
      uses: actions/setup-python@v4
      with:
        python-version: "3.11"

    - name: Instalar dependencias
      run: |
        python -m venv venv
        source venv/bin/activate
        pip install -r requirements.txt

    - name: Ejecutar tests
      run: |
        pytest --maxfail=1 --disable-warnings -q
```

3.2. Súbelo a tu repo y cada push a `main` o PR ejecutará automáticamente los tests.

---

### 🧹 4. **Buenas prácticas diarias**

| Hábito                         | Beneficio                                                    |
| ------------------------------ | ------------------------------------------------------------ |
| ✅ Escribe pruebas primero      | Te obliga a pensar en el diseño y comportamiento esperado.   |
| ✅ Automatiza pruebas           | Nunca olvides probar antes de subir.                         |
| ✅ Usa CI                       | Pruebas se ejecutan automáticamente en cada push.            |
| ✅ Testea en capas              | Unitarios para funciones, integración para flujos completos. |
| ✅ Falla rápido, arregla rápido | Más fácil corregir si sabes qué falló exactamente.           |

---

### ⚔️ 5. **¿Cuándo usar cada tipo de test?**

| Tipo de Test       | Qué prueba                          | Cuándo usarlo                            |
| ------------------ | ----------------------------------- | ---------------------------------------- |
| Unitario           | Funciones pequeñas (suma, división) | Siempre, rápido, confiable               |
| Integración        | Módulos que trabajan juntos         | Al integrar múltiples partes del sistema |
| Sistema/End-to-End | Flujo completo como un usuario real | En apps web, APIs, formularios, etc.     |

---

### 🧰 Herramientas que puedes usar conforme avances

| Herramienta      | ¿Para qué sirve?                             |
| ---------------- | -------------------------------------------- |
| `pytest`         | Testing rápido y expresivo en Python         |
| `pytest-cov`     | Ver qué porcentaje del código está testeado  |
| `GitHub Actions` | Automatizar CI/CD                            |
| `pre-commit`     | Ejecutar linters/tests antes de hacer commit |
| `tox`            | Probar en múltiples versiones de Python      |

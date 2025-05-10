
# 🛠️ Guía para Iniciar un Proyecto Python Profesional

## 📁 1. Estructura inicial del proyecto

```
mi_proyecto/
│
├── main.py               # Punto de entrada del programa
├── operaciones.py        # Módulo(s) con lógica de negocio
├── tests/                # Carpeta de pruebas
│   └── test_main.py
│
├── venv/                 # Entorno virtual (ignorado en git)
├── .gitignore
├── requirements.txt      # Dependencias del proyecto
└── README.md             # Descripción del proyecto
```

---

## ⚙️ 2. Configurar entorno virtual

```bash
python3 -m venv venv
source venv/bin/activate  # o .\venv\Scripts\activate en Windows
```

> Esto aísla tus paquetes del sistema y mantiene tu proyecto limpio.

---

## 📦 3. Instalar y guardar dependencias

```bash
pip install pytest
pip freeze > requirements.txt
```

> Usa `requirements.txt` para reproducir entornos en otras máquinas fácilmente.

---

## 📜 4. Crear `.gitignore`

Incluye al menos:

```gitignore
venv/
__pycache__/
*.pyc
.pytest_cache/
.DS_Store
.vscode/
```

> Evita subir archivos temporales o locales a tu repositorio Git.

---

## 🧪 5. Escribir pruebas desde el inicio

Crea un archivo en `/tests/test_tuarchivo.py` y usa `pytest`.

Ejemplo:

```python
# tests/test_operaciones.py
from operaciones import division
import pytest

def test_division_por_cero():
    with pytest.raises(ValueError):
        division(10, 0)
```

> Así validas el comportamiento de tus funciones desde el inicio.

---

## ♻️ 6. Separar lógica de negocio y entrada/salida

- **`main.py`** → maneja entrada del usuario y errores.
- **`operaciones.py`** → contiene solo funciones puras y reutilizables.

---

## 🧼 7. Seguir buenas prácticas

- Una función = una responsabilidad.
- Nombres claros para funciones y variables.
- Evita repetir lógica.
- Usa excepciones en lugar de retornos de error.
- Sigue [PEP8](https://peps.python.org/pep-0008/): estilo de código de Python.

---

## 🧩 8. Añadir un `README.md`

Incluye:

- Descripción del proyecto.
- Instrucciones para correrlo.
- Cómo activar el entorno virtual.
- Cómo correr las pruebas.

---

## ✅ 9. Revisión antes de terminar

- ¿Hay pruebas para cada función importante?
- ¿El código está modularizado?
- ¿Manejas los errores correctamente?
- ¿Usas entorno virtual y está ignorado en Git?
- ¿Has probado tu programa desde consola?

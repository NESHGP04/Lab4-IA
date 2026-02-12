# Lab – Task 2: Implementación “Bare Metal” de Métodos de Gradiente

## 📌 Descripción

Este laboratorio tiene como objetivo implementar manualmente tres variantes del algoritmo de descenso por gradiente para ajustar un polinomio de grado 3 a un conjunto de datos ruidoso.

Se comparan:

- Batch Gradient Descent
- Stochastic Gradient Descent (SGD)
- Mini-batch Gradient Descent

El enfoque es completamente **“bare metal”**, es decir:

⚠️ No se permite usar:
- sklearn
- pytorch
- tensorflow

Solo se permite:
- numpy
- pandas
- matplotlib

Toda la lógica matemática y las actualizaciones de los pesos fueron implementadas manualmente.

---

## 🎯 Objetivo del Experimento

Visualizar la diferencia entre:

- Velocidad de convergencia
- Estabilidad
- Error final alcanzado

utilizando como modelo un polinomio cúbico.

---

## 📊 Generación de Datos

Se generaron 1000 puntos basados en la función real:

y = 2x³ − 3x² + 5x + 3

Posteriormente:

- Se agregó ruido normal aleatorio.
- Se normalizaron los datos para mejorar la estabilidad del gradiente.
- Se construyó la matriz de diseño:

X = [1, x, x², x³]

---

## 🧮 Modelo Matemático

Modelo:

ŷ = Xw

Función de costo (MSE):

J(w) = (1/n) ∑ (ŷ − y)²

Gradiente vectorial:

∇J = (2/n) Xᵀ (Xw − y)

Actualización de pesos:

w = w − η ∇J

---

## ⚙️ Algoritmos Implementados

### 1️⃣ Batch Gradient Descent

- Utiliza todos los datos en cada actualización.
- Gradiente exacto.
- Convergencia estable.

---

### 2️⃣ Stochastic Gradient Descent (SGD)

- Utiliza un solo punto por actualización.
- Gradiente altamente ruidoso.
- Mayor variabilidad.
- Oscila alrededor del mínimo.

**Importante:**

SGD presenta alta variabilidad debido a que usa un solo punto por actualización, lo que genera un gradiente ruidoso y provoca fluctuaciones alrededor del mínimo.

---

### 3️⃣ Mini-batch Gradient Descent

- Utiliza lotes de tamaño 32.
- Compromiso entre estabilidad y eficiencia.
- Menor varianza que SGD.
- Menor costo por actualización que Batch.

---

## 📈 Métrica de Evaluación

Se graficó:

Loss (MSE) vs Tiempo (segundos)

⚠️ No se usaron iteraciones en el eje X, sino tiempo real, para comparar eficiencia computacional.

---

## 🔎 Resultados Observados

- **Batch GD**
  - Convergencia suave y estable.
  - Error final más bajo.
  - Mayor costo por actualización.

- **SGD**
  - Convergencia rápida al inicio.
  - Alta variabilidad.
  - Oscilaciones constantes alrededor del mínimo.
  - Error final ligeramente mayor.

- **Mini-batch**
  - Balance entre estabilidad y velocidad.
  - Convergencia relativamente rápida.
  - Error final cercano al de Batch.

---

## 🧠 Conclusión

El experimento demuestra la relación entre varianza del gradiente y estabilidad:

- Batch GD tiene baja varianza → convergencia estable.
- SGD tiene alta varianza → fluctuaciones alrededor del mínimo.
- Mini-batch logra un equilibrio entre ambos.

En términos de estabilidad y error final, Batch Gradient Descent obtiene el resultado más consistente.

En términos de velocidad inicial de convergencia, SGD reduce rápidamente el error, pero su naturaleza ruidosa impide una estabilización completa.

Mini-batch representa el mejor compromiso práctico.

---

## 📂 Estructura del Proyecto

```bash
│
├── task2_1.py
├── README.md
└── resultados.png
```

## 🚀 Cómo Ejecutar

```bash
python task2_1.py
```

## 📌 Aprendizajes Clave

La normalización es crítica para estabilidad numérica.

La varianza del estimador del gradiente afecta directamente la convergencia.

SGD no converge suavemente, sino que oscila alrededor del mínimo.

Mini-batch es el método más utilizado en práctica debido a su balance.

## 👩‍💻👩‍💻 Autoras
Camila Richter - 23183
Marinés García - 23391

# 🧠 Programación Lógica Inductiva (PLI) 📜

¡Bienvenido a la documentación de mi proyecto sobre **Programación Lógica Inductiva (PLI)**!

---

## 💡 Conceptos Centrales de PLI

La **Programación Lógica Inductiva (PLI)** se define como la intersección entre el **aprendizaje inductivo** y la **programación lógica**.  
Muestra fortalezas significativas al tratar con **relaciones recursivas de datos** y **grandes conjuntos de datos**, donde los algoritmos proposicionales (como los árboles de decisión) presentan problemas de representación.

---

### 🔑 Ventajas Clave de PLI

- Representación **clara y compacta**.  
- Capacidad para **relacionar propiedades de más de un objeto** a la vez.  
- Capacidad de **introducir nuevos predicados automáticamente** durante el proceso de aprendizaje, simplificando la representación de los conceptos aprendidos.  
- Utiliza el poder de **representación y formalismo de la lógica de primer orden**.

El objetivo principal de PLI es aprender una **hipótesis (H)** que, junto con el **conocimiento base (T)**, sea:

- **Completa:** Cubre los ejemplos positivos (ϵ⁺).  
- **Consistente:** No cubre los ejemplos negativos (ϵ⁻).

---

## 📚 Fundamentos Teóricos

El método de PLI requiere el conocimiento de varias nociones de **lógica de primer orden**:

- **Cláusula de Horn:**  
  Una cláusula con a lo más un literal positivo.  
  Ejemplo: `H ← L₁ ∧ … ∧ Lₙ`

- **Programa Lógico:**  
  Un conjunto de cláusulas de Horn.

- **Unificador de Máxima Generalidad (umg).**

- **Resolución:**  
  Regla de inferencia utilizada para probar implicaciones sintácticas mediante refutación.

- **Relación de Subsunción (≤).**

---

## 🧩 Clasificación de Sistemas PLI

Los sistemas de PLI se clasifican según:

- **Número de Conceptos:** Simples o Múltiples.  
- **Número de Ejemplos:** No incrementales o Incrementales/Secuenciales.  
- **Supervisor:** Interactivos o No Interactivos.

---

### ⚙️ Técnicas Empleadas

#### 🔽 Bottom-Up (de específico a general)
Basados en la **generalización de ejemplos positivos**, como:
- **Generalización Menos General (lgg)**
- **rlgg**

#### 🔼 Top-Down (de general a específico)
Realizan una **búsqueda de refinamiento** a través de la especialización de hipótesis, utilizando:
- **Operadores de Refinamiento**

#### 🔁 Revisión de Teoría
Permiten **corregir el conocimiento base (B)** cuando se detectan inconsistencias.

---

## 🛠 Implementación: Sistema ALEPH

El proyecto utiliza **ALEPH (A Learning Engine for Proposing Hypotheses)**, un sistema de PLI que implementa un **algoritmo de cubrimiento secuencial**.  
Aleph sigue una estrategia **Bottom-Up** para construir las hipótesis, aprendiendo **una cláusula a la vez** y eliminando los ejemplos positivos cubiertos en cada paso.

---

### 📝 Pasos del Algoritmo ALEPH

1. **Selección del ejemplo:**  
   Elige un ejemplo a generalizar.

2. **Construcción de la cláusula más específica:**  
   Crea la cláusula más específica que contiene el ejemplo seleccionado, respetando las restricciones del lenguaje.

3. **Búsqueda:**  
   Busca una cláusula más general que la anterior.

4. **Eliminar la redundancia:**  
   Agrega la cláusula con el mayor valor (*best score*) y elimina los ejemplos redundantes.

---

## 🧪 Experimentos con ALEPH

Se realizaron implementaciones con diferentes conjuntos de datos para evaluar el rendimiento del sistema:

| **Experimento** | **Archivos Base** | **Resultados Destacados** | **Interpretación** |
|------------------|------------------|----------------------------|--------------------|
| **1. Sin Ejemplos Erróneos** | `implementacion1.b`, `.f`, `.n` | Regla única: `expr(A,B) :- tipo(B,sustantivo), tipo(A,sustantivo), ...`<br>**Accuracy = 1.0** | El sistema indujo una regla que clasifica correctamente todas las expresiones del *training set*. |
| **2. Con Ejemplo Erróneo** | Modificación de `implementacion1.n` | Regla única: `expr(A,B) :- tipo(B,sustantivo), tipo(A,artículo), ...`<br>**Accuracy ≈ 0.9474** | La inserción de un ejemplo positivo en el conjunto negativo causa un leve descenso en la precisión; la regla se ajusta para ser más consistente, buscando la secuencia *Artículo + Sustantivo*. |
| **3. Múltiples Reglas** | `implementacion3.b`, `.f`, `.n` | Tres reglas para `parent/2`:<br>`parent(A,B) :- mother(A,B)`<br>`parent(A,B) :- father(A,B)`<br>**Accuracy = 1.0** | Se obtuvieron las reglas de parentesco esperadas, más una regla “anómala” (Regla 1) que no fue refutada por ningún ejemplo negativo, demostrando un desafío de consistencia total. |

---

## ⭐ Conclusiones

> ¡Echa un vistazo a los archivos de implementación en el código para ver los resultados detallados! 🚀

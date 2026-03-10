---

# Memoria Técnica: Diagramas de Interacción en Columnas Rectangulares

Este documento detalla el procedimiento teórico y matemático implementado para la obtención de diagramas de interacción ($P_n$ vs $M_n$) y la verificación de seguridad de columnas de concreto armado, bajo los lineamientos de la norma **ACI 318**.

---

## 1. Hipótesis de Diseño

El cálculo se fundamenta en los principios de diseño por resistencia:

* **Compatibilidad de deformaciones:** Las deformaciones en el acero y el concreto son proporcionales a su distancia al eje neutro (las secciones planas permanecen planas).
* **Resistencia del concreto:** La deformación máxima útil del concreto en la fibra extrema comprimida se define como $\epsilon_u = 0.003$.
* **Esfuerzo del acero:** Se define como $f_s = E_s \cdot \epsilon_s \le f_y$, con un módulo de elasticidad $E_s = 2,000,000 \text{ kg/cm}^2$.
* **Bloque de Whitney:** Se utiliza un bloque rectangular equivalente de tensiones para representar la distribución de esfuerzos en el concreto comprimido.

---

## 2. Parámetros del Material

### Bloque de Compresión ($\beta_1$)

El factor $\beta_1$ relaciona la profundidad del eje neutro ($c$) con la profundidad del bloque de esfuerzos ($a = \beta_1 \cdot c$):

| Resistencia del Concreto ($f'c$) | Valor de $\beta_1$ |
| --- | --- |
| $f'c \le 280 \text{ kg/cm}^2$ | $0.85$ |
| $280 < f'c < 560 \text{ kg/cm}^2$ | $0.85 - \frac{0.05 \cdot (f'c - 280)}{70}$ |
| $f'c \ge 560 \text{ kg/cm}^2$ | $0.65$ |

---

## 3. Procedimiento de Cálculo por Punto

Para construir el diagrama, se varía la profundidad del eje neutro ($c$) desde la tracción pura hasta la compresión pura.

### A. Deformaciones y Esfuerzos en el Acero

Para cada capa de acero $i$ a una profundidad $d_i$:


$$\epsilon_{si} = 0.003 \cdot \frac{c - d_i}{c}$$

$$f_{si} = \max(-f_y, \min(f_y, E_s \cdot \epsilon_{si}))$$

### B. Fuerzas Internas

* **Fuerza de compresión del concreto ($C_c$):**

$$C_c = 0.85 \cdot f'c \cdot b \cdot a \quad \text{donde } a = \min(\beta_1 \cdot c, h)$$


* **Fuerzas en el acero ($F_{si}$):**

$$F_{si} = A_{si} \cdot f_{si}$$



### C. Equilibrio de Fuerzas y Momentos

* **Carga Axial Nominal ($P_n$):**

$$P_n = C_c + \sum_{i=1}^{n} F_{si}$$


* **Momento Nominal ($M_n$) respecto al centro plástico:**

$$M_n = C_c \cdot \left(\frac{h}{2} - \frac{a}{2}\right) + \sum_{i=1}^{n} F_{si} \cdot \left(\frac{h}{2} - d_i\right)$$



---

## 4. Puntos Singulares

* **Compresión Pura ($P_0$):** Capacidad máxima teórica sin excentricidad.

$$P_0 = 0.85 \cdot f'c \cdot (A_g - A_{st}) + A_{st} \cdot f_y$$


.
* **Falla Balanceada ($c_{bal}$):** El concreto alcanza $\epsilon_u = 0.003$ simultáneamente con la fluencia del acero traccionado.

$$c_{bal} = \frac{0.003}{0.003 + (f_y / E_s)} \cdot d_{extremo}$$



---

## 5. Resistencia de Diseño (Factores $\phi$)

La resistencia nominal se reduce mediante el factor $\phi$, que depende de la deformación neta de tracción ($\epsilon_t$) en la capa de acero más alejada:

1. **Falla controlada por compresión** ($\epsilon_t \le \epsilon_y$): $\phi = 0.65$
2. **Zona de transición** ($\epsilon_y < \epsilon_t < 0.005$):

$$\phi = 0.65 + 0.25 \cdot \frac{\epsilon_t - \epsilon_y}{0.005 - \epsilon_y}$$


3. **Falla controlada por tracción** ($\epsilon_t \ge 0.005$): $\phi = 0.90$

> **Nota:** La carga máxima de diseño está limitada para considerar excentricidades accidentales:
> 
> $$\phi P_{n, \max} = 0.80 \cdot \phi \cdot P_0$$
> 
> 

---

## 6. Verificación de Seguridad

El sistema determina si el par de fuerzas solicitantes $(M_u, P_u)$ es admisible verificando que se encuentre dentro de la envolvente de diseño $(\phi M_n, \phi P_n)$. Se emplea **interpolación lineal por segmentos** para calcular la capacidad exacta en niveles de carga específicos.

---

**Cumplimiento Normativo:** Este procedimiento ha sido desarrollado íntegramente bajo los estándares del **ACI 318**.

¿Te gustaría que genere una tabla de ejemplo con valores específicos para una sección de columna determinada?

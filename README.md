# Memoria Técnica: Diagramas de Interacción en Columnas Rectangulares

Este documento detalla el procedimiento teórico y matemático implementado para la obtención de diagramas de interacción ($P_n$ vs $M_n$) siguiendo los lineamientos de la norma **ACI 318**.

## 1. Hipótesis de Diseño

1. **Compatibilidad de deformaciones:** Las deformaciones en el acero y el concreto son proporcionales a su distancia al eje neutro.
2. **Resistencia del concreto:** Deformación máxima útil $\epsilon_u = 0.003$.
3. **Esfuerzo del acero:** $f_s = E_s \cdot \epsilon_s \le f_y$.

## 2. Parámetros del Material

### Bloque de Compresión ($\beta_1$)
* Si $f'c \le 280 \text{ kg/cm}^2 \Rightarrow \beta_1 = 0.85$
* Si $f'c \ge 560 \text{ kg/cm}^2 \Rightarrow \beta_1 = 0.65$
* Intermedios: $\beta_1 = 0.85 - \frac{0.05 \cdot (f'c - 280)}{70}$

## 3. Equilibrio de Fuerzas y Momentos

* **Carga Axial Nominal ($P_n$):**
$$P_n = C_c + \sum_{i=1}^{n} F_{si}$$

* **Momento Nominal ($M_n$):**
$$M_n = C_c \cdot (\frac{h}{2} - \frac{a}{2}) + \sum_{i=1}^{n} F_{si} \cdot (\frac{h}{2} - d_i)$$

## 4. Resultados de la Sección Actual
* **Base (b):** 40 cm
* **Peralte (h):** 60 cm
* **f'c:** 210 kg/cm²
* **fy:** 4200 kg/cm²
* **Área de Acero Total (Ast):** 11.94 cm²
* **Carga Máxima de Diseño (φPn máx):** 247.74 ton

---
*Análisis realizado bajo el reglamento ACI 318.*

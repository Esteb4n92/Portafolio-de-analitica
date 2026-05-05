# Portafolio-de-analitica
# 📊 Análisis de Comportamiento de Compra: Online vs En Tienda


##  Descripción del proyecto

Análisis exploratorio del comportamiento de compra de **11,789 consumidores**, comparando los canales Online, En Tienda e Híbrido. El objetivo es identificar diferencias en gasto, perfil digital y comportamiento psicográfico entre los distintos segmentos de consumidores.

El informe fue construido en **Power BI Desktop** con un modelo de datos de 26 variables, 27 medidas DAX organizadas por carpetas, y 4 páginas de análisis con diseño oscuro consistente.

---

##  Estructura del informe

| Página | Contenido |
|---|---|
| **Resumen Ejecutivo** | KPIs principales, distribución de canal, gasto por género y ciudad |
| **Comportamiento de Gasto** | Gasto por edad, matriz ciudad × género, diferencial Online vs Tienda |
| **Perfil del Consumidor** | Scores de comportamiento por canal, perfil digital por edad |

---

##  Archivos del repositorio

| Archivo | Descripción |
|---|---|
| `Informe Online Vs Shopping.pbix` | Archivo Power BI Desktop con modelo completo y todas las medidas DAX |
| `Informe Online Vs Shopping.pdf` | Exportación estática del informe (4 páginas) |

---

##  Hallazgos principales

### 1. El canal Tienda domina con el 86.9% de los consumidores
Solo el **10% prefiere comprar Online** y el 3.1% es Híbrido. Sin embargo, la preferencia no se traduce directamente en mayor gasto — el diferencial es mínimo.

### 2. El gasto online supera al de tienda entre compradores Online
Los consumidores con preferencia Online gastan en promedio **$76,429 online** vs $11,191 en tienda física. En contraste, los de canal Tienda gastan **$85,103 en tienda** vs $74,349 online — lo que confirma que el canal preferido concentra el gasto.

### 3. El diferencial global de gasto es pequeño pero consistente
A nivel general, el gasto promedio en tienda ($75,662) supera ligeramente al online ($74,555) — una diferencia de apenas **$1,107**, lo que sugiere que ambos canales compiten en igualdad de condiciones en términos de ticket promedio.

### 4. El comportamiento digital es homogéneo entre géneros
La confianza en pagos digitales es prácticamente igual entre Hombres (5.48), Mujeres (5.48) y Otros (5.53) — lo que indica que la brecha de adopción digital no está determinada por género sino por otros factores.

### 5. La edad no diferencia significativamente el gasto
Los 4 rangos de edad (18-30, 31-45, 46-60, 60+) presentan gastos muy similares tanto online como en tienda, oscilando entre **$73,596 y $75,694** en el canal online. Esto sugiere un dataset con distribución uniforme, útil para análisis de segmentación por otras variables.

### 6. Perfil digital: alta conectividad en todos los segmentos
El consumidor promedio pasa **60.1 horas semanales en internet** y tiene **7.6 años de experiencia con smartphone**, lo que refleja una muestra altamente digitalizada independientemente del canal de compra preferido.

---

##  Herramientas y técnicas utilizadas

- **Power BI Desktop** — modelado, visualización y diseño del informe
- **DAX** — 27 medidas organizadas en carpetas (KPIs Financiero, Segmentación, Comportamiento, Perfil)
- **Power Query** — transformación y limpieza del dataset
- **Kaggle** — fuente del dataset original
- **MCP (Model Context Protocol)** — conexión directa al modelo para validación de medidas y consultas DAX en tiempo real

---

##  Medidas DAX destacadas

```dax
-- Diferencial de gasto entre canales
[KPI] Diferencial Gasto Online vs Tienda =
VAR _Online = AVERAGE('online vs store shopping datase'[Gastos Promedio Online])
VAR _Tienda = AVERAGE('online vs store shopping datase'[Gastos Promedio en Tienda])
RETURN _Online - _Tienda

-- Score digital compuesto (promedio de 3 métricas normalizadas /10)
[KPI] Score Comportamiento Digital =
VAR _Confianza = AVERAGE('online vs store shopping datase'[Puntuacion de Confianza en Pagos])
VAR _Tecnico   = AVERAGE('online vs store shopping datase'[Puntuacion de Conocimientos Tecnicos])
VAR _Disp      = AVERAGE('online vs store shopping datase'[Disponibilidad del Producto Online])
RETURN DIVIDE(_Confianza + _Tecnico + _Disp, 3, 0)

-- % de compradores por canal (dinámico, responde a filtros)
[%] Compradores Online =
VAR _Total  = COUNTROWS('online vs store shopping datase')
VAR _Online = CALCULATE(COUNTROWS('online vs store shopping datase'),
              'online vs store shopping datase'[Preferencia de Compra] = "Online")
RETURN DIVIDE(_Online, _Total, 0)
```

---

##  Vista previa del informe

> [Ver informe completo en PDF](./Informe%20Online%20Vs%20Shopping.pdf) para una vista completa de las 3 páginas.

---

## 👤 Autor

**Esteban Villalobos**
Estudiante de Ingeniería de Sistemas — CUC Barranquilla
Enfoque: Análisis de datos · Power BI · SQL · Excel


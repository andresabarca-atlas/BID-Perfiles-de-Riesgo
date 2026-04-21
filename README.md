# Perfiles de Riesgo de Desastres — BID RiskMONITOR

Prototipo interactivo de la nueva versión de los **Perfiles de Riesgo de Desastres por Amenazas Naturales** del Banco Interamericano de Desarrollo. El perfil consolida indicadores socioeconómicos, registros históricos de pérdidas, exposición del entorno construido y capas de amenaza en una página HTML autocontenida, editable y publicable sin dependencias de servidor.

![version](https://img.shields.io/badge/version-2.0.0-blue)
![status](https://img.shields.io/badge/estado-prototipo-orange)
![license](https://img.shields.io/badge/licencia-BID-lightgrey)

---

# ✨ Descripción

El perfil está construido como un archivo HTML estático que incluye todos sus datos en un objeto JavaScript editable al inicio del archivo. No requiere backend ni instalación: se abre directamente en el navegador o se publica en GitHub Pages.

El perfil incluye las siguientes secciones:

- **Indicadores sociales** — PIB, población, Gini, IDH y crecimiento poblacional
- **Principales desastres** — Eventos históricos de mayor impacto con muertos y pérdida como % del PIB
- **Entorno construido (exposición)** — Costo de reemplazo de edificios e infraestructura por sector
- **Curvas de excedencia de pérdidas históricas** — Catálogo DesInventar, distribución por tipo de amenaza y curva OEP
- **Capas de amenaza** — Mapa interactivo con amenaza sísmica (GEM) e inundaciones (GloFAS)
- **Población anual afectada** *(nuevo)* — Dashboard interactivo embebido desde ArcGIS Experience Builder
- **Referencias** — Fuentes de datos con links directos

Todas las secciones a partir de *Entorno construido* cuentan con **toggles de colapso**, permitiendo al usuario ocultar secciones que no le interesen en un momento dado.

---

# 🚀 Prototipo
 
Como caso piloto, se tomó **Ecuador** para desarrollar y validar el nuevo formato de perfil. El prototipo incluye todas las secciones propuestas e integra los datos reales del país disponibles en las fuentes oficiales.
 
Puedes acceder al prototipo en:
**[https://andresabarca-atlas.github.io/BID-Perfiles-de-Riesgo/Prototipo](https://andresabarca-atlas.github.io/BID-Perfiles-de-Riesgo/Prototipo)**
 
---

# 📁 Estructura del repositorio

```
/
├── Prototipo/
│   └── index.html      # Perfil interactivo de Ecuador (archivo principal)
└── README.md           # Este archivo
```

---

# 📊 Fuentes de datos

| Sección | Fuente | Link |
|---|---|---|
| Indicadores sociales | World Development Indicators, World Bank (2024) | [link](https://databank.worldbank.org/source/world-development-indicators) |
| Principales desastres | EM-DAT International Disaster Database (2008) | [link](https://www.emdat.be/) |
| Exposición — Edificios | GEM Foundation Seismic Risk Profiles (2023) | [link](https://github.com/gem/risk-profiles/) |
| Exposición — Infraestructura | CDRI. Global Infrastructure Resilience (2023) | [link](https://giri.unepgrid.ch/facts-figures/building-infrastructures) |
| Pérdidas históricas | DesInventar v9.20.04 (2020) | [link](https://db.desinventar.org) |
| Amenaza sísmica | GEM Global Earthquake Hazard Map (2023) | [link](https://zenodo.org/records/8409647) |
| Amenaza inundación | GloFAS Flood Hazard Maps, JRC / Comisión Europea | [link](https://data.jrc.ec.europa.eu/dataset/da4d7f64-a5c3-403f-bd2b-11a97176031e) |
| Población afectada | Dataset Custom vía ArcGIS Experience Builder | [link](https://experience.arcgis.com/experience/ae7a4a5083c143a0b003190370a603bf) |

---

# ✏️ Cómo editar el perfil

Todos los datos del perfil están centralizados en el objeto `DATA` al inicio del archivo `index.html`. Para actualizar cualquier valor, basta con editar ese objeto — no es necesario tocar el HTML ni el código de los gráficos.

```javascript
const DATA = {
  pais:         { nombre, codigo, flag },
  indicadores:  [ { label, value }, ... ],
  desastres:    [ { año, nombre, muertos, perdida_pib }, ... ],
  exposicion:   { edificios: { residencial, comercial, industrial },
                  infraestructura: [ { sector, valor, color }, ... ] },
  historico:    { inicio, fin, perdidas_totales, catalogo[], lec[], ... },
  mapas:        { amenazas, poblacion_afectada },
  referencias:  [ { texto, url, subitems? }, ... ]
};
```

---

# 🛠️ Tecnologías utilizadas

| Librería | Uso | CDN |
|---|---|---|
| [Chart.js 4.4.1](https://www.chartjs.org/) | Gráficos (donut, barra, línea OEP) | cdnjs |
| [ArcGIS Experience Builder](https://www.esri.com/en-us/arcgis/products/arcgis-experience-builder/overview) | Mapas y dashboards embebidos | iframe |
| [Google Fonts — Source Sans 3](https://fonts.google.com/specimen/Source+Sans+3) | Tipografía | fonts.googleapis.com |

El perfil no tiene dependencias de servidor ni de frameworks JavaScript. Es HTML/CSS/JS puro.

---

# 🧑‍🍳 Autores

El prototipo es desarrollado por el equipo de la **Unidad de Gestión de Riesgos de Desastres** del **Banco Interamericano de Desarrollo**.

---

# 📑 Licencia

Copyright© 2025. Banco Interamericano de Desarrollo ("BID"). Todos los derechos reservados.

## Limitación de responsabilidades

El BID no será responsable, bajo circunstancia alguna, de daño ni indemnización, moral o patrimonial; directo o indirecto; accesorio o especial; o por vía de consecuencia, previsto o imprevisto, que pudiese surgir:

i. Bajo cualquier teoría de responsabilidad, ya sea por contrato, infracción de derechos de propiedad intelectual, negligencia o bajo cualquier otra teoría; y/o

ii. A raíz del uso del prototipo, incluyendo, pero sin limitación de potenciales defectos, o la pérdida o inexactitud de los datos de cualquier tipo.

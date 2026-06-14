# Análisis de Siniestros Viales Fatales en Perú

Proyecto de análisis de datos sobre siniestros de tránsito fatales en Perú (2021-2025), usando datos abiertos del Observatorio Nacional de Seguridad Vial (ONSV) del MTC.

## Objetivo

Identificar patrones temporales (hora, día, mes) y espaciales en los siniestros viales fatales a nivel nacional, para apoyar la toma de decisiones en seguridad vial.

## Estructura del proyecto

```text
accidente-peruanos/
│
├── data/
│   ├── raw/                  # Dataset original (ONSV, 9111 filas, 27 columnas)
│   └── processed/            # Dataset procesado
│
├── notebooks/
│   └── 01_eda.ipynb          # Limpieza, EDA temporal y espacial
│
├── dashboard/
│   └── mapa_calor_siniestros.html  # Mapa de calor interactivo
│
├── requirements.txt
└── README.md
```

## Fuente de datos

[Observatorio Nacional de Seguridad Vial (ONSV)](https://www.onsv.gob.pe/datosabiertos) — "Siniestros de Tránsito Fatales 2021-2025 (preliminar)". Información registrada por las Unidades de Prevención e Investigación de Accidentes de Tránsito de la PNP.

## Limpieza de datos

- Eliminación de columnas con alto porcentaje de valores nulos (>75%): clasificación de señales verticales y existencia de señalización.
- Conversión de `FECHA SINIESTRO` y `HORA SINIESTRO` a formato de fecha/hora, extrayendo mes, día de la semana y hora.
- Conversión de coordenadas (`COORDENADAS LATITUD`, `COORDENADAS LONGITUD`) a formato numérico.

## Hallazgos principales

### Patrones temporales

- **Por hora del día**: dos picos claros — madrugada/amanecer (5-7 AM) y noche (6-8 PM), coincidiendo con horas de menor visibilidad y mayor tráfico. El máximo absoluto ocurre a las 7 PM.
- **Por día de la semana**: domingo y sábado presentan significativamente más siniestros que el resto de la semana, seguidos por el lunes.
- **Por mes**: no se observa fuerte estacionalidad; los siniestros se mantienen relativamente estables a lo largo del año, con marzo y junio ligeramente por encima del promedio.
- **Tipo de siniestro**: "Choque" es el más frecuente, seguido de "Despiste" y "Atropello".

### Patrones espaciales

- Los siniestros se concentran fuertemente en la **costa peruana**, siguiendo el corredor de la Carretera Panamericana (norte y sur).
- **Lima** es el punto de mayor concentración de siniestros fatales del país.
- La región amazónica (Loreto, Ucayali, Madre de Dios) presenta una incidencia mínima, asociada a menor densidad vial y poblacional.

## Mapa de calor

Mapa interactivo generado con Folium, disponible en [`dashboard/mapa_calor_siniestros.html`](dashboard/mapa_calor_siniestros.html).

## Tecnologías

- Python (Pandas, NumPy, Matplotlib, Seaborn)
- Folium (mapas de calor geoespaciales)
- Jupyter Notebook

## Cómo ejecutar

```bash
git clone https://github.com/AldhaValenzuelaH/accidentalidad-vial-peru.git
cd accidentalidad-vial-peru
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

## 👤 Autor

**Aldhair Valenzuela Huillcaya**
[LinkedIn](#) | [GitHub](https://github.com/AldhaValenzuelaH)

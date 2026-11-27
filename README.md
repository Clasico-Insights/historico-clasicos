# Histórico de los Clásicos

Historia de los partidos Barça–Real Madrid de fútbol contada con datos, para publicar en X.

El objetivo es crear contenido visual (gráficos y textos) a partir de datos de eventos y estadísticas de partido, con un tono neutral entre los dos equipos.

## Fuentes de datos

| Fuente | Qué cubre | Notas |
|---|---|---|
| [StatsBomb Open Data](https://github.com/statsbomb/open-data) | 31 Clásicos: Liga 1973-74, final de Copa del Rey 1982-83 y Liga 2005-06 a 2020-21 | En la etapa 2005-2021 solo están los partidos en los que jugó Messi. Datos de eventos (pases, tiros, etc.). |
| [API-Football](https://www.api-football.com/) (plan gratuito) | Temporadas 2022-23 a 2024-25 | Límite de 100 consultas al día. Estadísticas de partido, no eventos con el mismo detalle. |

Los datos descargados se guardan también en Google Drive para no depender de las APIs.

## Herramientas

- Google Colab
- Python: `pandas`, `statsbombpy`, `requests`, `mplsoccer`

## Estructura del repositorio

```
historico-clasicos/
├── datos/
│   └── inventario_clasicos_statsbomb.csv   # Los 31 Clásicos disponibles en StatsBomb
├── 01_base_de_datos.ipynb                  # Descarga los datos y los guarda en Drive
├── 02_mapa_de_tiros.ipynb                  # Plantilla: mapa de tiros y carrera de xG
├── README.md
├── LICENSE
└── .gitignore
```

### `datos/inventario_clasicos_statsbomb.csv`

Una fila por partido (31 en total, 116.191 eventos). Los goles coinciden con el resultado oficial en los 31 partidos.

| Columna | Descripción |
|---|---|
| `fecha` | Fecha del partido (AAAA-MM-DD) |
| `competicion` | La Liga o Copa del Rey |
| `temporada` | Temporada (p. ej. 2020/2021) |
| `local`, `visitante` | Equipos |
| `goles_local`, `goles_visitante` | Resultado final |
| `match_id` | Identificador del partido en StatsBomb |
| `eventos` | Número de eventos registrados en el partido |
| `fuente` | Proveedor de los datos |

## Identidad visual

Todos los gráficos comparten el mismo estilo (definido en la celda 2 de `02_mapa_de_tiros.ipynb`):

| Elemento | Valor |
|---|---|
| Fondo | `#14171F` (casi negro) |
| Texto | `#F2F2F2`; secundarios en `#9AA3B2` |
| Barcelona | `#E0245E` (granate) |
| Real Madrid | `#F2F2F2` (blanco) |
| Tipografía | Roboto (Google Fonts) |
| Tamaño | 1600 × 900 px |
| Pie | «Datos: StatsBomb Open Data» y logo de StatsBomb |

El título de cada gráfico dice su conclusión. Sin escudos, fotos de jugadores ni imágenes de los clubes.

## Limitaciones

- **Cambio de fuente.** Hasta 2020-21 los datos son de StatsBomb; desde 2022-23, de API-Football. No hay datos de 2021-22. Las cifras de una y otra etapa no siempre son comparables.
- **Definiciones distintas entre proveedores.** Un "tiro", un "pase completado" o un "regate" pueden contarse de forma diferente según el proveedor.
- **Muestra sesgada.** En StatsBomb, la etapa 2005-2021 solo incluye partidos con Messi; no es la historia completa del Clásico.
- **Muestras pequeñas.** Con pocos partidos por temporada, conviene evitar conclusiones fuertes.
- **Minutos jugados.** Las comparaciones entre jugadores deben ajustarse por minutos (p. ej. por 90 minutos).



## Atribución

Datos de eventos: **StatsBomb Open Data** (https://github.com/statsbomb/open-data). Según sus condiciones de uso, cualquier publicación que use estos datos debe citar a StatsBomb como fuente e incluir su logo.

Las estadísticas de 2022-23 en adelante proceden de **API-Football** (https://www.api-football.com/).

## Licencia

Código bajo licencia MIT (ver `LICENSE`). Los datos pertenecen a sus proveedores y se rigen por sus propias condiciones.

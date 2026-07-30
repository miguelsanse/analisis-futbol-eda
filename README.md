# Análisis de Fútbol Europeo: Elo y Rendimiento en las Cinco Grandes Ligas

## Descripción del proyecto

Este proyecto realiza un análisis exploratorio de datos (EDA) y un dashboard interactivo sobre el fútbol de las cinco grandes ligas europeas (Inglaterra, España, Italia, Alemania y Francia), en sus divisiones de primera y segunda categoría, durante las temporadas 2000/01 a 2024/25.

El objetivo es estudiar los factores que influyen en el resultado de los partidos, con especial atención a dos preguntas: ¿existe realmente la ventaja de jugar en casa? y ¿la fuerza previa de un equipo, medida por su puntuación Elo, predice su rendimiento?

Para responderlas se combinan dos fuentes de datos de origen distinto: los resultados y estadísticas de partidos de Football-Data.co.uk, y las puntuaciones Elo históricas de los clubes de ClubElo. Tras la limpieza y unión, el dataset final contiene 93.570 partidos y 42 variables.

Técnicas empleadas: limpieza y transformación de datos con pandas, unión de fuentes mediante merge, análisis descriptivo, contrastes de hipótesis con scipy (t de Student pareada, correlación de Pearson, ANOVA y chi-cuadrado) y visualización interactiva con un dashboard en Power BI.

## Estructura del proyecto

proyecto_final/
├── data/
│ ├── raw/ # Datos en bruto originales
│ │ ├── Matches.zip # Partidos comprimidos (descomprimir antes de usar)
│ │ └── EloRatings.csv # Puntuaciones Elo (ClubElo)
│ └── processed/
│ └── matches_elo_final.csv # Dataset final limpio y unido (93.570 x 42)
├── notebooks/
│ └── eda_futbol.ipynb # Notebook con todo el análisis
├── dashboard/
│ └── dashboard_futbol.pbix # Dashboard interactivo de Power BI
└── README.md # Este documento

## Instalación y requisitos

El análisis está desarrollado en Python 3.12 y requiere las siguientes librerías:

- pandas
- numpy
- scipy
- matplotlib
- seaborn

Instalación de las dependencias:

pip install pandas numpy scipy matplotlib seaborn

El notebook `eda_futbol.ipynb` puede ejecutarse de principio a fin con la opción "Ejecutar todo" (Run All). Las rutas a los datos son relativas, por lo que debe mantenerse la estructura de carpetas indicada.

Nota: el archivo de partidos se distribuye comprimido como `Matches.zip` debido a su tamaño. Descomprímelo dentro de la carpeta `data/raw/` (obteniendo `Matches.csv`) antes de ejecutar el notebook.

El dashboard requiere Power BI Desktop para abrir el archivo `dashboard_futbol.pbix`.

## Resultados y conclusiones

El análisis parte de un dataset de 93.570 partidos con una media de 2,58 goles por encuentro, y se centra en tres hallazgos principales, cada uno respaldado por un contraste de hipótesis.

**La ventaja de jugar en casa es real y significativa.** El equipo local gana el 44,8 % de los partidos, frente al 27,4 % del visitante, y marca de media 1,47 goles por partido frente a los 1,11 del rival. Una prueba t de Student para muestras pareadas confirma que esta diferencia no se debe al azar (p < 0,001). Más allá de la significación estadística, la diferencia práctica de unos 0,36 goles por partido a favor del local es relevante en el contexto del fútbol.

**La puntuación Elo previa predice el rendimiento, aunque de forma moderada.** La correlación de Pearson entre la ventaja de Elo del local al inicio de la temporada y su diferencia de goles es de r = 0,30 (p < 0,001). Es una relación positiva y moderada: el Elo anticipa una tendencia clara, pero deja amplio margen a la imprevisibilidad propia del deporte. Esto valida el interés de haber unido ambas fuentes de datos.

**Existen diferencias significativas de estilo entre ligas.** Un ANOVA confirma que el número de goles difiere entre competiciones (p < 0,001): la Bundesliga es la más goleadora (2,95 goles por partido) y las segundas divisiones española y francesa las más cerradas (en torno a 2,33). Un contraste chi-cuadrado muestra además que el reparto de resultados depende de la liga (p < 0,001): aunque la victoria local es muy estable entre competiciones, las segundas divisiones concentran una proporción notablemente mayor de empates. Ambos análisis coinciden en dibujar un perfil de las segundas divisiones como competiciones más tácticas y equilibradas.

En conjunto, el proyecto muestra que factores estructurales como la localía y la calidad previa del equipo influyen de forma medible en los resultados, pero sin eliminar la incertidumbre que caracteriza al fútbol. El dashboard permite explorar estos patrones de forma interactiva, filtrando por temporada y comparando ligas y equipos.

## Próximos pasos

- Incorporar variables de contexto adicionales, como la asistencia de público o las bajas por lesión, para enriquecer el modelo explicativo.
- Extender el análisis a un modelo predictivo del resultado de los partidos a partir de la diferencia de Elo y otras variables.
- Ampliar la cobertura a más ligas europeas, evaluando la disponibilidad de datos estadísticos completos.
- Analizar el efecto de la temporada 2019/20, marcada por la disputa de partidos sin público durante la pandemia, sobre la ventaja de jugar en casa.

## Contribuciones

Las contribuciones son bienvenidas. Si deseas proponer mejoras, puedes abrir una issue o un pull request en el repositorio.

## Autores

- [Miguel Ángel Bartolomé Talavera]
- [@miguelsanse](https://github.com/miguelsanse)

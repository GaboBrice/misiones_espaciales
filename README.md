# Luna vs. Marte en números

Página web que analiza la exploración robótica de la Luna y Marte con datos públicos del NSSDC (NASA): cuántas naves se perdieron, cuánto tiempo funcionaron, cuánto costaron y qué rovers recorrieron más kilómetros.

**Datos:** 96 objetos que llegaron a la Luna (1959–2025) y 37 misiones enviadas a Marte (1962–2026), actualizados a noviembre de 2026.

## Contenido de la página

1. **Inventario:** objetos lunares encontrados, con ubicación aproximada o sin ubicar, y misiones a Marte exitosas o fallidas.
2. **Cuánto duran:** mediana, media y curva de supervivencia de Kaplan-Meier para la Luna y Marte, y misiones por década.
3. **Qué influye:** efecto del peso, del aterrizaje y de la década en la duración, y del destino y el peso en el costo. Incluye un gráfico de burbujas con 45 naves.
4. **Rovers:** distancia recorrida por 11 rovers (Perseverance tiene el récord con 45.22 km).
5. **3 perfiles de misión:** grupos obtenidos con PCA y K-Means sobre 126 misiones.
6. **Simulador:** eliges destino, tipo de nave, peso y década, y la página estima la duración y el costo.
7. **Misiones recientes y próximas (2025–2030):** predicciones para 8 misiones (Blue Ghost 1, Resilience, Lunar Trailblazer, Lunar Pathfinder, Chang'e 7, ESCAPADE, MMX y Rosalind Franklin). En las que ya llegaron se compara la predicción con el resultado real.

## Técnicas estadísticas

| Técnica | Uso |
|---|---|
| Kaplan-Meier | Mediana, media y curva de supervivencia, considerando las misiones que siguen activas (censura) |
| Cox estratificado | Efecto del peso y del aterrizaje dentro de cada destino y época |
| AFT Weibull | Efecto de la década sobre la duración; se usa para la duración del simulador |
| GLM Gamma (enlace log) | Costo según destino, peso y tipo de nave |
| PCA y K-Means | Agrupación de las misiones en 3 perfiles |

## Estructura del repositorio

```
├── index.html
├── README.md
└── img/
    ├── fondo.jpg         # fondo de toda la página
    ├── luna.jpg
    ├── marte.jpg
    ├── orbitador.jpg
    ├── aterrizador.jpg
    ├── rover.jpg
    └── lanzamiento.jpg
```

La carpeta `img/` debe estar al mismo nivel que `index.html` y los nombres deben estar en minúsculas, si no las imágenes no cargan.

## Cómo verla

- **En tu computadora:** abre `index.html` en el navegador (se necesita internet para cargar Tailwind CSS, Chart.js y la fuente Inter).
- **En GitHub Pages:** ve a *Settings → Pages*, elige la rama `main` y la carpeta `/ (root)`, y guarda. La página queda en `https://<tu-usuario>.github.io/<nombre-del-repositorio>/`.

## Tecnologías

- HTML y JavaScript, sin instalación ni compilación
- [Tailwind CSS](https://tailwindcss.com/) (CDN) para el diseño
- [Chart.js](https://www.chartjs.org/) (CDN) para los gráficos

## Fuentes

- [Objetos artificiales en la Luna – NSSDC/NASA](https://nssdc.gsfc.nasa.gov/planetary/lunar/lunar_artifact_impacts.html)
- [Misiones a Marte – NSSDC/NASA](https://nssdc.gsfc.nasa.gov/planetary/planets/marspage.html)
- Estado de las misiones 2025–2030: JAXA, NASA, ESA y prensa especializada (consultado en noviembre de 2026).

## Créditos de imágenes

Imágenes de la NASA. Fondo: ilustración conceptual de una base en Marte (NASA, 1989). Las fotos de las tarjetas de misiones y del simulador son referenciales según el tipo de nave (orbitador, aterrizador o rover).

## Nota

Las duraciones y costos estimados son predicciones estadísticas basadas en misiones de 1959 a 2026. El modelo de duración estima cuánto opera una nave si llega bien, pero no predice fallas de lanzamiento o aterrizaje. Las misiones comerciales recientes suelen costar menos de lo que estima el modelo.

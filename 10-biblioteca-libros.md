# 10 — Biblioteca de libros y recursos gráficos

Este archivo indexa el material descargado localmente (PDFs y diagramas) y los recursos online de referencia. Todo lo que está bajo `libros/` e `imagenes/` es redistribuible — dominio público (obras de NASA) o licencias libres (CC-BY, CC-BY-SA, GFDL, CC-BY-NC-ND del caso Axler). Ver columna *Licencia* en cada entrada.

**Regla:** cada vez que agregues un PDF, consigná autor, año, licencia y fuente. No subas nada de dudosa procedencia — si no encontrás licencia explícita, no entra.

## Cómo leer este índice

- **Módulo** refiere al archivo `NN-*.md` al que el libro da soporte principal.
- **Ruta** es el archivo dentro de este repo. Un link roto = bug, reportar.
- **Nivel**: `básico` (primer contacto), `estándar` (referencia de curso), `avanzado` (investigación / diseño real de misión).

---

## Matemáticas — `libros/01-matematicas/`

| Ruta | Título / autor | Año | Licencia | Nivel | Para qué sirve |
|------|----------------|-----|----------|-------|----------------|
| [boyd-vmls.pdf](libros/01-matematicas/boyd-vmls.pdf) | *Introduction to Applied Linear Algebra — Vectors, Matrices, and Least Squares*, Boyd & Vandenberghe | 2018 | CC-BY-NC-ND | Estándar | Álgebra lineal aplicada para ingeniería: mínimos cuadrados, SVD, regresión. Complemento práctico de Strang. |
| [boyd-convex-optimization.pdf](libros/01-matematicas/boyd-convex-optimization.pdf) | *Convex Optimization*, Boyd & Vandenberghe | 2004 | CC-BY-NC-ND (autor) | Avanzado | Base matemática para trajectory optimization, MPC, control óptimo. Obligatorio antes de diseñar maniobras por colocación. |
| [axler-linear-algebra-done-right-4ed.pdf](libros/01-matematicas/axler-linear-algebra-done-right-4ed.pdf) | *Linear Algebra Done Right* 4ed, Axler | 2024 | CC-BY-NC 4.0 | Estándar | Álgebra lineal con enfoque de operadores — ideal si querés entender por qué todo funciona, no solo cómo calcular. |
| [lebl-notes-on-diffy-qs.pdf](libros/01-matematicas/lebl-notes-on-diffy-qs.pdf) | *Notes on Diffy Qs — Differential Equations for Engineers*, Jiří Lebl | 2024 | CC-BY-SA 4.0 | Básico-Estándar | EDOs con muchos ejemplos físicos. Reemplaza Boyce-DiPrima si no lo tenés. |
| [trefethen-atap-first-6-chapters.pdf](libros/01-matematicas/trefethen-atap-first-6-chapters.pdf) | *Approximation Theory and Approximation Practice*, Trefethen — primeros 6 capítulos | 2013 | Autor (vista previa libre) | Avanzado | Cuando implementes propagadores o filtros: entender Chebyshev y por qué tus polinomios divergen. |

**Complementos online (no descargados):**
- MIT OCW 18.02 Multivariable Calculus — https://ocw.mit.edu/courses/18-02sc-multivariable-calculus-fall-2010/
- MIT OCW 18.06 Linear Algebra (Strang) — https://ocw.mit.edu/courses/18-06-linear-algebra-spring-2010/
- 3Blue1Brown *Essence of Linear Algebra* — intuición geométrica previa al formalismo.

---

## Física — `libros/02-fisica/`

| Ruta | Título / autor | Año | Licencia | Nivel | Para qué sirve |
|------|----------------|-----|----------|-------|----------------|
| [openstax-university-physics-vol1.pdf](libros/02-fisica/openstax-university-physics-vol1.pdf) | *University Physics Volume 1*, OpenStax (baja resolución) | 2024 | CC-BY 4.0 | Básico | Mecánica, termodinámica, fluidos, ondas. Base de todo lo demás. |
| [openstax-university-physics-vol3.pdf](libros/02-fisica/openstax-university-physics-vol3.pdf) | *University Physics Volume 3*, OpenStax | 2023 | CC-BY 4.0 | Básico | Óptica, relatividad, física cuántica, física atómica y nuclear. |
| [tong-classical-dynamics.pdf](libros/02-fisica/tong-classical-dynamics.pdf) | *Classical Dynamics*, David Tong (Cambridge DAMTP) | 2015 | Autor (uso académico libre) | Estándar | Lagrangiana, hamiltoniana, Kepler, cuerpo rígido. Súper claro. Lectura obligada antes de orbital mechanics seria. |
| [tong-dynamics-and-relativity.pdf](libros/02-fisica/tong-dynamics-and-relativity.pdf) | *Dynamics and Relativity*, David Tong | 2013 | Autor | Básico-Estándar | Mecánica newtoniana + relatividad especial. Primer paso. |
| [tong-electromagnetism.pdf](libros/02-fisica/tong-electromagnetism.pdf) | *Electromagnetism*, David Tong | 2015 | Autor | Estándar | EM riguroso — necesario para plasma, antennas, propulsión eléctrica. |
| [tong-fluid-dynamics.pdf](libros/02-fisica/tong-fluid-dynamics.pdf) | *Fluid Dynamics*, David Tong | 2022 | Autor | Avanzado | Flujo compresible, ondas de choque — motor necesario para propulsión química y reentrada. |
| [tong-statistical-physics.pdf](libros/02-fisica/tong-statistical-physics.pdf) | *Statistical Physics*, David Tong | 2012 | Autor | Avanzado | Termodinámica estadística — útil para control térmico, atmósferas, propulsión avanzada. |

---

## Mecánica orbital — `libros/03-orbital/`

| Ruta | Título / autor | Año | Licencia | Nivel | Para qué sirve |
|------|----------------|-----|----------|-------|----------------|
| [nasa-rp-1009-introduction-to-orbit-dynamics.pdf](libros/03-orbital/nasa-rp-1009-introduction-to-orbit-dynamics.pdf) | *An Introduction to Orbit Dynamics and its Application to Satellite-Based Earth Monitoring Systems* (NASA RP-1009) | 1977 | Dominio público (NASA) | Estándar | Derivación compacta de mecánica orbital aplicada — problema de dos cuerpos, perturbaciones, órbitas sun-synch. |
| [nasa-tp-20220014814-astrodynamics-convention-libration.pdf](libros/03-orbital/nasa-tp-20220014814-astrodynamics-convention-libration.pdf) | *Astrodynamics Convention and Modeling Reference for Lunar, Cislunar, and Libration Point Orbits* (NASA/TP-20220014814) | 2022 | Dominio público (NASA) | Avanzado | Estado del arte para misiones cislunares y L-points. Sistemas de coordenadas, CR3BP, propagación. |

**Complementos online:**
- *Orbital Mechanics & Astrodynamics*, Bryan Weber (CC-BY-SA 4.0) — https://orbital-mechanics.space/ (web interactivo con Python).
- Curtis *Orbital Mechanics for Engineering Students* — NO es libre, pero es el texto de trabajo estándar. Comprarlo.
- Vallado *Fundamentals of Astrodynamics and Applications* — NO libre. Referencia avanzada.

---

## Propulsión — `libros/04-propulsion/`

| Ruta | Título / autor | Año | Licencia | Nivel | Para qué sirve |
|------|----------------|-----|----------|-------|----------------|
| [nasa-sp-125-huzel-huang-liquid-rocket-engines.pdf](libros/04-propulsion/nasa-sp-125-huzel-huang-liquid-rocket-engines.pdf) | *Design of Liquid Propellant Rocket Engines* (NASA SP-125), Huzel & Huang | 1971 | Dominio público (NASA) | Avanzado | Diseño real de motores líquidos: cámara, turbopompas, inyectores. Viejo pero todavía imbatible en cobertura. |

**Complementos online / no libres:**
- Sutton & Biblarz *Rocket Propulsion Elements* — NO libre, pero es la referencia que sí o sí hay que tener.
- Humble, Henry & Larson *Space Propulsion Analysis and Design* — NO libre; útil para análisis a nivel sistemas.
- *Ignition! An Informal History of Liquid Rocket Propellants*, John D. Clark — circula en PDF (AFRL-era, status legal mixto); no incluido aquí.

---

## Ingeniería de sistemas — `libros/05-sistemas/`

| Ruta | Título / autor | Año | Licencia | Nivel | Para qué sirve |
|------|----------------|-----|----------|-------|----------------|
| [nasa-systems-engineering-handbook-rev2.pdf](libros/05-sistemas/nasa-systems-engineering-handbook-rev2.pdf) | *NASA Systems Engineering Handbook* (SP-2016-6105 Rev 2) | 2016 | Dominio público (NASA) | Estándar | El manual. V-model, TRL, revisiones, margins, costing. Léelo dos veces. |

---

## Subsistemas / SmallSats — `libros/06-subsistemas/`

| Ruta | Título / autor | Año | Licencia | Nivel | Para qué sirve |
|------|----------------|-----|----------|-------|----------------|
| [nasa-small-spacecraft-soa-2024.pdf](libros/06-subsistemas/nasa-small-spacecraft-soa-2024.pdf) | *Small Spacecraft Technology — State of the Art 2024* | 2025 | Dominio público (NASA) | Estándar | Inventario actualizado: plataformas, EPS, propulsión, GNC, comms, payloads. Primer stop cuando elegís COTS. |

---

## Minería espacial y recursos — `libros/07-mineria/`

| Ruta | Título / autor | Año | Licencia | Nivel | Para qué sirve |
|------|----------------|-----|----------|-------|----------------|
| [keck-asteroid-retrieval-feasibility-study.pdf](libros/07-mineria/keck-asteroid-retrieval-feasibility-study.pdf) | *Asteroid Retrieval Feasibility Study*, Keck Institute of Space Studies | 2012 | KISS (redistribuible con atribución) | Avanzado | Estudio seminal de arquitectura ARM. Números concretos de Δv, requerimientos de SEP, captura. |
| [lunar-sourcebook.pdf](libros/07-mineria/lunar-sourcebook.pdf) | *Lunar Sourcebook — A User's Guide to the Moon*, Heiken, Vaniman & French (eds) | 1991 | LPI (uso académico libre) | Avanzado | Referencia canónica de composición, regolito y recursos lunares. Si vas a ISRU lunar empezá acá. |
| [nasa-sp-413-space-settlements.pdf](libros/07-mineria/nasa-sp-413-space-settlements.pdf) | *Space Settlements: A Design Study* (NASA SP-413), Johnson & Holbrow | 1977 | Dominio público (NASA) | Básico-Estándar | Estudio clásico Stanford/Ames sobre asentamientos espaciales. Contexto histórico + cálculos útiles. |

**Complementos online:**
- *NEO Deflection App* + base de datos CNEOS — https://cneos.jpl.nasa.gov/
- *Asterank* — https://www.asterank.com/ — valuación económica de NEOs (cuestionable, pero orden de magnitud).

---

## Estadística y referencia — `libros/08-referencia/`

| Ruta | Título / autor | Año | Licencia | Nivel | Para qué sirve |
|------|----------------|-----|----------|-------|----------------|
| [openstax-introductory-statistics.pdf](libros/08-referencia/openstax-introductory-statistics.pdf) | *Introductory Statistics*, OpenStax | 2021 | CC-BY 4.0 | Básico | Probabilidad, inferencia, regresión. Base para análisis de datos de misión y reliability. |

---

## Imágenes y diagramas — `imagenes/`

Todas las imágenes son de Wikimedia Commons bajo licencias libres (CC-BY, CC-BY-SA, dominio público o equivalente). Cada archivo conserva su nombre original en el comentario; la atribución completa está en la página de Commons correspondiente (`https://commons.wikimedia.org/wiki/File:<nombre>`).

### Mecánica orbital

| Archivo | Descripción | Original en Commons |
|---------|-------------|---------------------|
| `hohmann-transfer.svg` | Transferencia de Hohmann entre dos órbitas circulares | [Hohmann_transfer_orbit.svg](https://commons.wikimedia.org/wiki/File:Hohmann_transfer_orbit.svg) |
| `bi-elliptic-transfer.svg` | Transferencia bi-elíptica (más eficiente que Hohmann para ratios grandes) | [Bi-elliptic_transfer.svg](https://commons.wikimedia.org/wiki/File:Bi-elliptic_transfer.svg) |
| `orbital-elements.svg` | Los seis elementos orbitales keplerianos clásicos | [Orbital_elements.svg](https://commons.wikimedia.org/wiki/File:Orbital_elements.svg) |
| `kepler-laws.svg` | Las tres leyes de Kepler en una imagen | [Kepler_laws_diagram.svg](https://commons.wikimedia.org/wiki/File:Kepler_laws_diagram.svg) |
| `lagrange-points.svg` | Los cinco puntos de Lagrange del sistema Sol-Tierra | [Lagrange_points2.svg](https://commons.wikimedia.org/wiki/File:Lagrange_points2.svg) |
| `lagrange-equipotential.png` | Contornos equipotenciales del problema restringido de tres cuerpos | [Lagrangian_points_equipotential.png](https://commons.wikimedia.org/wiki/File:Lagrangian_points_equipotential.png) |
| `delta-v-solar-system.svg` | Mapa de Δv del sistema solar interno | [Delta-Vs_for_inner_Solar_System.svg](https://commons.wikimedia.org/wiki/File:Delta-Vs_for_inner_Solar_System.svg) |
| `comparacion-orbitas-satelitales.svg` | LEO, MEO, GEO y órbitas de navegación a escala | [Comparison_satellite_navigation_orbits.svg](https://commons.wikimedia.org/wiki/File:Comparison_satellite_navigation_orbits.svg) |

### Propulsión

| Archivo | Descripción | Original en Commons |
|---------|-------------|---------------------|
| `tsiolkovsky-equation.svg` | La ecuación del cohete | [Tsiolkovsky_rocket_equation.svg](https://commons.wikimedia.org/wiki/File:Tsiolkovsky_rocket_equation.svg) |
| `rocket-mass-ratio-dv.svg` | Ratio de masas vs Δv (Tsiolkovsky graficada) | [Rocket_mass_ratio_versus_delta-v.svg](https://commons.wikimedia.org/wiki/File:Rocket_mass_ratio_versus_delta-v.svg) |
| `rocket-cycle-gas-generator.svg` | Ciclo gas-generator (F-1, Merlin) | [Gas_generator_rocket_cycle.svg](https://commons.wikimedia.org/wiki/File:Gas_generator_rocket_cycle.svg) |
| `rocket-cycle-staged-combustion.svg` | Ciclo staged combustion (RD-180, SSME) | [Staged_combustion_rocket_cycle.svg](https://commons.wikimedia.org/wiki/File:Staged_combustion_rocket_cycle.svg) |
| `rocket-cycle-full-flow-staged.svg` | Full-flow staged combustion (Raptor) | [Full_flow_staged_rocket_cycle.svg](https://commons.wikimedia.org/wiki/File:Full_flow_staged_rocket_cycle.svg) |
| `rocket-cycle-expander.svg` | Ciclo expander (RL-10) | [Expander_rocket_cycle.svg](https://commons.wikimedia.org/wiki/File:Expander_rocket_cycle.svg) |
| `rocket-cycle-electric-feed.svg` | Ciclo electric pump-fed (Rocket Lab Rutherford) | [Electric_feed_rocket_cycle.svg](https://commons.wikimedia.org/wiki/File:Electric_feed_rocket_cycle.svg) |
| `rocket-cycle-combustion-tap-off.svg` | Ciclo combustion tap-off (BE-3) | [Combustion_tap-off_rocket_cycle.svg](https://commons.wikimedia.org/wiki/File:Combustion_tap-off_rocket_cycle.svg) |
| `rocket-nozzle-types.svg` | Tipos de tobera: convergente-divergente, bell, aerospike | [Rocket_nozzle_expansion.svg](https://commons.wikimedia.org/wiki/File:Rocket_nozzle_expansion.svg) |

### Sistemas e ingeniería

| Archivo | Descripción | Original en Commons |
|---------|-------------|---------------------|
| `v-model.svg` | V-model de ingeniería de sistemas | [V-Modell.svg](https://commons.wikimedia.org/wiki/File:V-Modell.svg) |
| `trl-meter-nasa.svg` | Escala TRL 1-9 de NASA | [NASA_TRL_Meter.svg](https://commons.wikimedia.org/wiki/File:NASA_TRL_Meter.svg) |

### Asteroides y misiones

| Archivo | Descripción | Original en Commons |
|---------|-------------|---------------------|
| `eros-near-shoemaker.jpg` | 433 Eros visto por NEAR Shoemaker (2000) | [Asteroid433eros.jpg](https://commons.wikimedia.org/wiki/File:Asteroid433eros.jpg) |
| `bennu-osiris-rex.jpg` | Mosaico de Bennu por OSIRIS-REx | [Bennu_mosaic_OSIRIS-REx.jpg](https://commons.wikimedia.org/wiki/File:Bennu_mosaic_OSIRIS-REx.jpg) |
| `ryugu-hayabusa2.jpg` | Ryugu por Hayabusa2 | [Hayabusa2-211211a.jpg](https://commons.wikimedia.org/wiki/File:Hayabusa2-211211a.jpg) |
| `iss-current.jpg` | Estación Espacial Internacional — referencia de escala para diseños tripulados | [International Space Station](https://commons.wikimedia.org/wiki/File:International_Space_Station_after_undocking_of_STS-132.jpg) |

---

## Cómo citar y respetar las licencias

1. **Obras de NASA** (SP-125, SP-413, SE Handbook, SOA, NTRS) son **dominio público** en los EE.UU. Se pueden redistribuir libremente, pero siempre acreditá *"NASA"* y el número de documento.
2. **OpenStax** — CC-BY 4.0. Requiere atribución: *"Access for free at openstax.org"*.
3. **Tong (DAMTP)** — el autor permite uso académico / estudio personal. No redistribuir modificado sin permiso.
4. **Boyd, Axler** — CC-BY-NC-\* — uso no comercial con atribución.
5. **Hefferon, Lebl, Weber (orbital-mechanics.space)** — CC-BY-SA 4.0 — requiere atribución y que obras derivadas usen la misma licencia.
6. **Wikimedia Commons** — cada imagen tiene su página con licencia explícita; la atribución específica está en el link de cada entrada arriba.

Si alguna vez producís material derivado (diapositivas, paper, propuesta), **documentá la fuente en un apéndice**. No mezcles licencias restrictivas con trabajos que querés liberar.

## Qué falta (wishlist)

- **Curtis** *Orbital Mechanics for Engineering Students* — comprar copia física.
- **Wertz/Larson SMAD** — comprar copia física (es THE referencia de diseño de misión).
- **Pisacane** *The Space Environment and its Effects on Space Systems* — comprar.
- **Prussing & Conway** *Orbital Mechanics* — comprar para algoritmos.
- **Mishin** *Space Propulsion Analysis and Design* (Humble) — comprar.
- Libros específicos de **ECSS** — standards, no todos públicos; obtener vía membresía institucional.

Con lo que está acá + los libros de comprar arriba, tenés cubierto el 90% de la bibliografía necesaria para los primeros 5 años del roadmap.

# 09 — Plan de estudio — ruta concreta 5-10 años

Este documento es el checklist personal. La materia a cubrir es gigantesca; sin una secuencia ordenada es fácil perderse. La secuencia siguiente asume que se parte de fundamentos universitarios (cálculo, física básica, programación), que se tiene 10-15 horas/semana dedicables al estudio, y que se mantiene el régimen por años.

**Compromiso mínimo realista**: 5 años de estudio serio para ser autosuficiente en diseño de misión. 10 años para ser un ingeniero senior respetado. Los 20 años del roadmap de negocio incluyen estos 5-10 de preparación superponiéndose con el ramp-up de la empresa.

## Año 1 — Fundamentos duros

**Objetivo**: Hacer fluido el idioma matemático y físico que se usa todos los días.

### Matemática (semanas 1-26)
- **Meses 1-3**: Cálculo multivariable + vectorial. MIT OCW 18.02 con ejercicios.
- **Meses 3-5**: Álgebra lineal. MIT OCW 18.06 Strang. Hasta autovalores, SVD.
- **Meses 5-8**: EDOs. Boyce-DiPrima capítulos 1-7. Laplace, sistemas lineales, estabilidad.
- **Meses 8-10**: Métodos numéricos. Implementar RK4, gradient descent, Newton en Python.
- **Meses 10-12**: Probabilidad y estadística básica. Papoulis primera mitad.

**Entregable fin año 1 matemática**: repositorio GitHub con 10 notebooks de Jupyter implementando problemas clave, ejercicios resueltos de cada libro.

### Física (en paralelo)
- **Meses 1-6**: Mecánica clásica Goldstein caps 1-8 (lagrangiana, hamiltoniana, cuerpo rígido). Resolver ~50 problemas.
- **Meses 7-9**: Termodinámica. Cengel completo.
- **Meses 10-12**: EM básico. Griffiths caps 1-9.

### Programación
- Python avanzado. NumPy, SciPy, Matplotlib, Astropy, Poliastro.
- Git y GitHub workflow.
- Introducción a C/C++ (flight software usa mayormente C).
- Al menos un proyecto pequeño: simulador de órbita 2-body con Cowell + RK4, visualización.

### Hitos culturales
- Asistir (presencial o remoto) a 1 conferencia LatAm (CAB, CATE).
- Leer Feynman Lectures volumen I completo.
- Crear perfil profesional en LinkedIn orientado a espacio, empezar networking.

## Año 2 — Mecánica orbital y físicas aplicadas

**Objetivo**: Dominio de mecánica celeste al nivel de diseñar maniobras de misión reales.

### Núcleo (todo el año)
- **Curtis — Orbital Mechanics for Engineering Students**, completo. Resolver **todos** los problemas de los capítulos 2-10.
- Implementar en Python: 2-body propagator, Kepler equation solver, elementos orbitales, Hohmann, Lambert problem.

### Complementos
- **Meses 3-6**: Mecánica de fluidos y gases compresibles. Anderson *Fundamentals of Aerodynamics* caps 7-11.
- **Meses 6-9**: Transferencia de calor. Incropera primera mitad.
- **Meses 9-12**: Física de plasma. Chen caps 1-5.

### Software práctico
- **GMAT** — completar tutorial oficial, modelar tu primer Hohmann Tierra-Marte, tu primer SSO, tu primer transferencia lunar.
- **Basilisk** — tutorial de attitude dynamics.
- **Poliastro** — resolver 20 problemas de Curtis con esta herramienta.

### Proyecto capstone año 2
Diseñar y documentar completamente una **misión hipotética CubeSat a SSO**. Entregables:
1. Requirements document (10-20 páginas).
2. Análisis de trayectoria: ventanas, maniobras, Δv budget.
3. Análisis preliminar de mass/power/link budget.
4. Código Python reproducible en GitHub.
5. Posts en blog técnico documentando proceso.

### Hitos
- Aplicar a SGAC LatAm.
- Postular a ISU SSP (Space Studies Program) — 2 meses, verano siguiente. Becas disponibles.
- Presentar el capstone en algún congreso (aunque sea estudiantil) o publicar en ArXiv como preprint.

## Año 3 — Especialización 1: subsistemas y propulsión

**Objetivo**: Dominio de al menos 2 subsistemas a nivel de poder diseñar, no sólo analizar.

### Elegir 2-3 áreas de especialización
Recomendación por tesis de empresa (prospección/instrumentos):
- **GNC / ADCS**
- **Propulsión eléctrica**
- **Instrumentos ópticos / espectroscopía**

### Material por área

#### Para GNC
- **Wie** o **Markley/Crassidis** — completo. ADCS a fondo.
- Implementar Kalman filter, UKF, B-dot, PID attitude control.
- **Farrell — Aided Navigation**.
- Proyecto: simulador completo de ADCS de un CubeSat desde detumble a pointing fino.

#### Para propulsión eléctrica
- **Goebel & Katz** — completo.
- **Jahn — Physics of Electric Propulsion**.
- Simulaciones con plasma codes simples (1D PIC).
- Visitar (si posible) algún laboratorio de electroprop — JPL, AFRL, Colorado, EPFL.

#### Para instrumentos ópticos
- **Smith — Modern Optical Engineering**.
- **Chrisp, Content et al. — Imaging spectrometer papers**.
- **Holst — CMOS/CCD Sensors and Camera Systems**.
- Entender principios de VNIR, SWIR, MWIR, TIR y técnicas de enfriamiento criogénico para detectores.

### Contexto ingeniería de sistemas
- Leer **SMAD** (Wertz) completo.
- Estudiar ECSS-E-ST-10C (system engineering) y ECSS-Q-ST-30C.

### Hitos
- Asistir a IAC como student (becas SGAC).
- Publicar un paper técnico corto (AIAA conference paper, AAS meeting, o equivalente LatAm).
- Contactar 10 profesionales senior en el área espacial LatAm, hacer 5 entrevistas.

## Año 4 — Especialización 2: hardware real e integración

**Objetivo**: Pasar del paper al soldador. Construir, no sólo analizar.

### Hardware hands-on
- Construir tu primera CubeSat subscale (1U) como proyecto personal o con grupo universitario. Componentes COTS.
  - Chasis con PC/104 rails.
  - Power board (solar + battery).
  - OBC con FreeRTOS.
  - Radio UHF (half-duplex ham band).
  - Sensores magnetómetro + giroscopio + acelerómetro.
  - Firmware: state machine, telemetry, beacon, command decode.
- NO se trata de lanzar esto — se trata de **aprender el ciclo completo** incluyendo tests térmicos caseros, vibración en shaker prestado, depuración de hw integrado.

### Electrónica espacial
- **Heiman — Underhood**, **Spaceflight Mechanisms**.
- Leer ECSS-Q-ST-60C (EEE components).
- Estudiar radiation effects: **Holmes-Siedle & Adams, "Handbook of Radiation Effects"**.

### Software de vuelo
- **NASA cFS** — clonar, compilar, correr. Entender arquitectura, event services, tables.
- Implementar un app cFS simple: contador con telemetría.
- Entender CCSDS space packet standard.

### Thermal y mechanical
- **Gilmore Thermal Handbook** — mínimo caps 1-6.
- Resolver casos: balance térmico CubeSat, heater sizing, MLI design.
- FEM simple con CalculiX/FreeCAD: primer modo natural de una plate con masas.

### Hitos
- Hardware demo funcional (CubeSat subscale).
- Contribuir a un proyecto open source aerospace (Libre Space, Orekit, poliastro, etc.).
- Continuar IAC, empezar a presentar papers propios.

## Año 5 — Consolidación: diseño de misión integrada

**Objetivo**: Pasar del componente al sistema completo. Diseñar una misión de ingeniería de alta fidelidad.

### Proyecto master
Diseño completo a nivel Fase A-B de una misión real hipotética. Elegir según interés:
- Opción A: CubeSat lunar 12U (como LunaH-Map, Lunar IceCube, BioSentinel).
- Opción B: Smallsat 200 kg Earth observation alta resolución.
- Opción C: Payload de prospección sobre otro spacecraft (riding de CLPS o Artemis secondary).

Entregables mínimos:
1. MCR y SRR documents (30-50 páginas).
2. Trade studies (mínimo 3 — comms band, propulsión, arquitectura óptica).
3. Full Δv, mass, power, link, thermal budgets.
4. Preliminary concept of operations (ConOps).
5. Risk register.
6. Cost ROM.
7. Código reproducible completo en GitHub.
8. Website / repositorio público del proyecto.

### Ingeniería de sistemas formal
- **INCOSE SE Handbook** — completo.
- **NASA SE Handbook (NASA/SP-2016-6105)** — completo.
- Considerar certificación INCOSE ASEP (Associate Systems Engineering Professional) — disponible online.

### Hitos
- Capstone presentado en IAC o conferencia mayor.
- Paper peer-reviewed submitted (AIAA, Acta Astronautica, Celestial Mech., o equivalente).
- Considerar maestría formal (ISAE, Delft, Colorado, ITA) si todavía no se tiene.

## Años 6-7 — Industria + iniciativa

**Objetivo**: Sumar experiencia industrial real y preparar el lanzamiento de la empresa.

### Trabajo industrial (en paralelo con empresa early-stage)
- Trabajar en Satellogic, INVAP, Akaer, Leanspace, o empresa espacial internacional con presencia LatAm.
- O bien contract / consulting con múltiples clientes.
- Objetivo: vivir el ciclo real de un proyecto (proposal → design → test → operations).

### Tema avanzado elegido
Profundización vertical en el área de negocio (siguiendo tesis prospección/instrumentos):
- **Estudio postdoc-level** de un tema: spectroscopy calibration, deep space communications, autonomous trajectory optimization.
- Leer papers frontera (últimos 5 años) exhaustivamente.
- Desarrollar expertise único que se convierta en moat técnico.

### Networking y ecosistema
- Asistir IAC, Small Sat, IEEE AeroConf como presentador.
- Contribuir a comunidades LatAm: organizar charla, mentorear jóvenes, colaborar con agencias.
- Construir relaciones con potenciales clientes ancla y socios (agencias, primes internacionales).

### Empresa (arranque formal)
- Incorporación formal.
- Primer equipo (2-5 personas).
- Primer contrato comercial (servicios / consulting).
- Levantar seed USD 250k-2M.

Ver `00-estrategia-latam.md` para detalle de fase 1.

## Años 8-10 — Profundización y producción

**Objetivo**: Ser experto reconocido en un área, tener producto propio.

### Dominio técnico
- Publicar 1-2 papers/año en área de especialidad.
- Impartir un seminario / curso / workshop anual.
- Mentorear graduate students.
- Considerar doctorado si se quiere path académico paralelo (no imprescindible para negocio).

### Empresa (fase 1 → fase 2)
- Primer CubeSat en órbita (año 8-10).
- Revenue 1-5 M USD.
- Series A.
- 20-40 empleados.

Ver roadmap en archivo 00.

## Años 10+

Trabajo constante:
- Mantener lectura de 1 paper/semana.
- Book/anío en área nueva (expandir footprint).
- 1 conferencia técnica/año.
- Review anual de esta biblioteca — actualizar lo que cambió.

Expertise se profundiza. El cambio viene de reconocer **cuándo profundizar vs cuándo expandir**. A los 10 años es mejor saber mucho de poco que poco de mucho.

## Nivel de aptitud objetivo por año

| Año | Auto-evaluación |
|-----|-----------------|
| 1 | Entiendo ecuaciones de Maxwell, lagrangiana, Kepler. Puedo hacer homework de MIT 16.07. |
| 2 | Puedo diseñar a mano una transferencia Hohmann, un presupuesto de Δv misión interplanetaria. Implementé simulador 2-body propio. |
| 3 | Dominio de 2 subsistemas al nivel de un engineer II. Puedo dimensionar un ADCS o un sistema de propulsión dada una misión. |
| 4 | Construí hardware propio, debuggeé flight software, realicé tests ambientales. Estoy cómodo con electrónica espacial. |
| 5 | Diseñé a nivel PDR una misión completa, con todos sus budgets. Paper peer-reviewed. |
| 7 | Experiencia industrial real. Reconocido como experto local. Empresa registrada. |
| 10 | Producto propio en órbita. Revenue Series A nivel. Experto internacional en mi área. |

## Principios de estudio

1. **Hacer problemas, no solo leer**. Un libro sin ejercicios resueltos vale la mitad.
2. **Implementar todo**. Code > paper > notas. Si no se puede simular, no se entendió.
3. **Mantener notas**. Obsidian/Zettelkasten linkeado. Re-leer notas propias trimestralmente.
4. **Conectar teoría con misiones reales**. Cada concepto → qué misión lo usó.
5. **Enseñar para aprender**. Escribir blog posts, dar charlas, mentorear. Enseñar fuerza claridad.
6. **Admitir ignorancia**. Nadie sabe todo. Es más rápido preguntar a alguien que está dos niveles arriba.
7. **No evitar lo aburrido**. Las estandarizaciones, los budgets, los tests — ahí vive 70% del trabajo real.
8. **Priorizar longevidad**. 10 horas/semana sostenidas > 80 horas intensivas agotadoras. Esto es 20 años.

## Señales de alarma

Si pasó un año y:
- No resolviste ≥300 problemas técnicos.
- No leíste ≥3 libros canónicos completos.
- No implementaste ≥5 proyectos Python/Matlab no triviales.
- No contactaste ≥20 profesionales del área.
- No asististe a ≥1 conferencia técnica.

...entonces el ritmo es insuficiente para el horizonte de 20 años. Reevaluar disponibilidad, salud, contexto. Mejor 5 años serios que 20 años diluidos.

## Un último mensaje

El camino es largo. No hay atajos — la física y la ingeniería aeroespacial son acumulativas. Pero también es extraordinariamente recompensante: en el horizonte de 20 años, habrá gente que consiga lanzar misiones propias desde LatAm. Algunos estarán en este camino porque empezaron hoy.

Las imágenes de Artemis II que colgaste de wallpaper no son sólo bonitas — son el estado del arte que tus propias misiones tendrán que superar para existir. La inspiración sirve sólo si después se traduce en 10 horas semanales consistentes. Empezá.

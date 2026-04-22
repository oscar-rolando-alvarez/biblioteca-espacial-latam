# 05 — Ingeniería de sistemas espaciales

La diferencia entre un proyecto escolar y una misión real es la disciplina de ingeniería de sistemas. Este documento resume las prácticas estándar que NO son negociables si se quiere construir hardware espacial confiable.

## 1. Ciclo de vida — modelo V

```
  Requerimientos misión ───────────────────────────────► Operaciones
       │                                                      ▲
       ▼                                                      │
  Requerimientos sistema ─────────────────────────► Validación sistema
       │                                                      ▲
       ▼                                                      │
  Diseño subsistema ──────────────────────► Verificación subsistema
       │                                                      ▲
       ▼                                                      │
  Diseño componente ──────────► Verificación componente
       │                                      ▲
       ▼                                      │
  Implementación (fabricación / código)
```

Cada nivel de descenso define qué, cada nivel de ascenso verifica contra qué. No hay atajo — saltear niveles produce hardware defectuoso que nadie sabe explicar cuando falla.

## 2. Technology Readiness Levels (TRL)

Escala NASA/DOD (1-9). Mismo concepto en ECSS.

| TRL | Estado |
|-----|--------|
| 1 | Principios básicos observados/reportados |
| 2 | Concepto de tecnología formulado |
| 3 | Prueba analítica / experimental de concepto |
| 4 | Validación de componente en laboratorio |
| 5 | Validación de componente en entorno relevante |
| 6 | Demostración de modelo de sistema/subsistema en entorno relevante |
| 7 | Demostración de prototipo en entorno operacional (vuelo) |
| 8 | Sistema completo calificado y probado |
| 9 | Sistema operacional probado en misión |

**Regla práctica**:
- Para una misión, todo componente debe estar en TRL 6+ al PDR, TRL 7+ al CDR.
- Si una misión combina componentes TRL<6, es una demostración tecnológica, y el riesgo de fracaso es alto.

## 3. Revisiones formales (reviews)

Secuencia estándar en una misión espacial. Cada review es un gate — no se pasa hasta cerrar action items.

| Sigla | Nombre | Cuándo | Qué se revisa |
|-------|--------|--------|---------------|
| MCR | Mission Concept Review | Inicio | Idea tiene sentido |
| MDR / SRR | Mission/System Requirements Review | Fase A | Requerimientos completos, consistentes |
| PDR | Preliminary Design Review | Fase B final | Diseño preliminar cumple requerimientos, riesgos identificados |
| CDR | Critical Design Review | Fase C final | Diseño listo para manufactura |
| TRR | Test Readiness Review | Pre-testing | Plan de test, instrumentación, fixtures listos |
| MRR | Manufacturing Readiness Review | Antes manufactura final | Procesos, cadena suministro |
| SAR | System Acceptance Review | Post-test | Unidad lista para integración de misión |
| FRR | Flight Readiness Review | Pre-lanzamiento | Todo listo para volar |
| MRR | Mission Readiness Review | Pre-lanzamiento | Sinónimo de FRR en algunos contextos |
| PLAR | Post-Launch Assessment | Post-lanzamiento | Salud, desempeño |

## 4. Estándares aplicables

### ECSS (European Cooperation for Space Standardization)
Tres ramas:
- **ECSS-M** (Management) — project management, risk, configuration.
- **ECSS-Q** (Product Assurance) — quality, reliability, EEE parts, materials.
- **ECSS-E** (Engineering) — requirements, design, verification.

Documentos clave:
- **ECSS-M-ST-10C**: project planning.
- **ECSS-Q-ST-30C**: dependability.
- **ECSS-Q-ST-40C**: safety.
- **ECSS-Q-ST-60C**: EEE components.
- **ECSS-E-ST-10C**: system engineering.
- **ECSS-E-ST-10-02C**: verification.
- **ECSS-E-ST-10-03C**: testing.
- **ECSS-E-ST-32C**: structural.
- **ECSS-E-ST-31C**: thermal.
- **ECSS-E-ST-20C**: electrical and electronic.
- **ECSS-E-ST-50**: communications.
- **ECSS-E-ST-60**: control engineering.
- **ECSS-E-ST-70**: ground systems & operations.

### NASA
- **NPR 7120.5**: Program/Project Management.
- **NPR 7123.1**: System Engineering Processes.
- **NASA-STD-5012**: Strength & Life Assessment for Spaceflight Hardware.
- **NASA-STD-6016**: Standard Materials and Processes Requirements for Spacecraft.
- **NASA-STD-5001**: Structural Design and Test Factors of Safety for Spaceflight.
- **NASA-STD-8739.xx**: Workmanship.

### MIL / Defense
- **MIL-STD-1540**: test requirements for launch/upper-stage/space vehicles.
- **MIL-STD-461**: EMC requirements.
- **MIL-STD-1553**: serial data bus.
- **MIL-HDBK-217**: reliability prediction.

### CubeSat-specific
- **CubeSat Design Specification (CDS)** — Cal Poly.
- **PPODS / ISIPOD** — deployer interfaces.

## 5. Mission assurance — gestión de riesgo

### Failure Mode and Effects Analysis (FMEA) / FMECA
Para cada item (función, interfaz, componente):
1. ¿Qué puede fallar? (failure mode)
2. ¿Qué pasa si falla? (failure effect)
3. ¿Por qué fallaría? (failure cause)
4. ¿Cuál es la severidad? (catastrófico, crítico, mayor, menor)
5. ¿Probabilidad?
6. ¿Detectabilidad?
7. RPN (Risk Priority Number) = severidad × probabilidad × detectabilidad.

Se atacan los RPN más altos con mitigaciones (redundancia, derating, test adicional).

### Fault Tree Analysis (FTA)
Top-down. Evento no deseado top-level → causas AND/OR. Útil para combinaciones de fallas.

### Single Point of Failure (SPOF) eliminación
Principio: ningún fallo único debe causar pérdida de misión. Técnicas:
- **Redundancia**: dual-string de aviónica, 2 receptores, 2 transmitters.
- **Cross-strapping**: habilidad de combinar bloques de distintos strings.
- **Graceful degradation**: aún con un fallo, misión parcial recuperable.

### Derating
Operar componentes por debajo de su rating nominal. Ejemplos ECSS:
- Resistores: 50-70% de potencia nominal.
- Capacitores: 50-70% de tensión nominal.
- Semiconductores: temperatura de junction < 0.75 × T_max.
- Interconexiones: corriente < 50% especificada.

### Heritage
Componentes con "flight heritage" son preferidos. El primer uso de un componente es siempre riesgo alto — por eso misiones nuevas suelen basarse en buses probados.

## 6. Configuration management

- **Baseline**: versión congelada de documentos/hardware.
- **Change control board (CCB)**: aprueba cambios, evalúa impacto.
- **Traceability**: cada requerimiento trazable a verificación. Cada pieza trazable a su materia prima y a tests aplicados.

Herramientas: DOORS (IBM), Jama, Polarion, Teamcenter. Alternativas abiertas: ReqIF + git.

## 7. Verification & Validation

### Verification
"¿Construimos el sistema correctamente?" — contra los requerimientos.
Métodos (ECSS):
- **T** = Test (preferido).
- **A** = Analysis (cuando test no factible o muy caro).
- **I** = Inspection (visual).
- **R** = Review of design (documentación).

### Validation
"¿Construimos el sistema correcto?" — contra las necesidades de la misión/cliente. Se hace al nivel más alto (misión).

### Niveles de test
Cada nivel se ejecuta antes de integrar al siguiente.
- **Component**: pruebas de subpartes (ej. resistor, chip, mecanismo).
- **Unit/Box**: caja individual (receiver, reaction wheel).
- **Subsystem**: grupo integrado (ADCS, comms) en simulación HW.
- **System (spacecraft)**: satélite completo.

### Qualification / Acceptance / Protoflight
Tres filosofías de test:
- **Qualification**: prototipos sometidos a niveles superiores a vuelo (margen) para demostrar robustez. No vuelan.
- **Acceptance**: unidad de vuelo testeada a niveles de vuelo. Vuela.
- **Protoflight**: una sola unidad, testeada a niveles intermedios (más que acceptance, menos que qualification). Vuela. Más barato, más riesgo.

Factores típicos de qualification (ECSS):
- Vibración: qual = 1.5 × acceptance, 3 minutos vs 2 minutos por eje.
- Térmico: qual = acceptance ±10°C, ciclos adicionales.
- Shock: qual = 1.4 × acceptance.

## 8. Environmental tests

### Vibration (sine, random)
Simula entornos de lanzamiento. Niveles específicos por launcher — cada proveedor publica User's Guide con envelopes de vibración.

**Typical Falcon 9 secondary payload**:
- Sine: 0.8-1.25 g (2-100 Hz), eje.
- Random: 0.02 g²/Hz flat entre 20-2000 Hz, approx 6.1 g RMS, 60s por eje.

### Shock
Liberación pirotécnica, separación. SRS (shock response spectrum) hasta 10,000 g a altas frecuencias.

### Thermal vacuum (TVAC)
- Cámara de vacío a <10⁻⁵ Pa.
- Ciclos térmicos: típicamente -40 a +80°C (bus), wider para payloads expuestos.
- Balance térmico: verificar modelo térmico coincide con medición (±3°C en puntos clave).

### EMC (compatibility)
MIL-STD-461 conducted emissions (CE), radiated emissions (RE), conducted susceptibility (CS), radiated susceptibility (RS). Típicamente 10 kHz - 40 GHz.

### Outgassing
Materiales en vacío liberan gases que pueden contaminar ópticas y sensores. ASTM E595:
- TML (Total Mass Loss) < 1%.
- CVCM (Collected Volatile Condensable Materials) < 0.1%.
Cualquier material a bordo debe ser screened contra la lista NASA Outgassing Database.

### Ionizing radiation
- TID (Total Ionizing Dose) en krad(Si). Órbita + blindaje determina dosis.
- SEE (Single Event Effects): heavy ion test, proton test. Umbrales LET y sección eficaz.

## 9. Presupuestos de misión (budgets)

Documentos vivos que se mantienen durante todo el ciclo.

### Mass budget
Targets típicos:
- Masa seca estimada + 15-30% margen según fase (early: 30%, PDR: 20%, CDR: 10%, FRR: 5%).
- System margin final ≥ 5% al lanzamiento.

### Power budget
- Producción (panel solar BOL y EOL, considerando degradación por radiación y temperatura).
- Consumo por modo (safe, nominal, science, downlink, etc.).
- Positive margin en peor caso de eclipse.
- Estado de carga de batería nunca < 30% DoD para Li-Ion durante vida útil.

### Data budget
- Generación on-board (payload + housekeeping).
- Capacidad de almacenamiento.
- Capacidad de downlink por pase.
- Margen 20-30%.

### Δv budget (ver archivo 03)
Incluir: inyección, corrección de lanzador, station keeping, collision avoidance, deorbit.

### Link budget (ver archivo 02 §4)
Margen de enlace 3 dB nominal, más para órbitas operativas sin LOS control.

### Thermal budget
Potencia disipada vs capacidad de radiador + heater. Peor-caso hot y cold separados.

### Pointing budget
Error de apuntamiento = raíz cuadrada suma cuadrática de:
- Error de determinación (sensor noise, star tracker).
- Error de control (deadband, actuator quantization).
- Error estructural (flexibilidad, thermoelastic distortion).

## 10. Workflow típico de una misión en LatAm

Escenario: startup desarrolla CubeSat 6U, primera misión.

| Fase | Duración | Entregables |
|------|----------|-------------|
| Pre-fase A (concepto) | 3-6 meses | MCR, análisis de misión, ROM cost |
| Fase A (feasibility) | 6-9 meses | SRR, requerimientos, trade studies |
| Fase B (preliminary) | 9-12 meses | PDR, diseño preliminar, analysis reports |
| Fase C (detailed design) | 6-12 meses | CDR, drawings, BOM, plan de test |
| Fase D (manufactura y test) | 9-15 meses | Unidad qualification + flight, tests env, SAR |
| Fase E (operaciones) | Vida útil | PLAR, telemetría, ciencia/operación |
| Fase F (decomisión) | Fin | Deorbit / passivation |

Total CubeSat primer misión: 3-5 años. Segunda misión siguiente familia: 1.5-2.5 años (heritage).

## 11. Costo orientativo — modelo paramétrico

### SMAD cost model (rough)
Costo total ≈ α · M^β · factor_clase.

Órdenes de magnitud reales (incluye NRE first-of-kind):
- CubeSat 3U single-mission: USD 200k-1.5M.
- CubeSat 6U advanced: USD 1-5M.
- Smallsat 100-500 kg: USD 5-40M.
- Smallsat avanzado con propulsión: USD 15-80M.
- Deep space smallsat demostrador: USD 50-200M.
- Bus clase 500-2000 kg GEO: USD 100-400M.

**Lanzamiento**:
- Rideshare LEO: USD 5k-6.5k/kg (Transporter SpaceX).
- Dedicated smallsat: USD 250k-400k/kg (Electron, Firefly).
- Lunar: Secondary en CLPS ~USD 50-100k/kg; dedicado mucho más.

## 12. Lecturas imprescindibles

1. **Wertz, Everett, Puschell (eds.) — Space Mission Engineering: The New SMAD** — biblia operativa.
2. **Larson, Kirkpatrick — Applied Space Systems Engineering** — complementario.
3. **Fortescue, Stark, Swinerd — Spacecraft Systems Engineering** — europeo, cobertura ESA.
4. **Wiley — Systems Engineering Principles and Practice** (no espacial pero riguroso).
5. **INCOSE — Systems Engineering Handbook** — marco genérico, aplicable.
6. **NASA Systems Engineering Handbook (NASA/SP-2016-6105)** — gratis online, 300+ páginas.

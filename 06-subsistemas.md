# 06 — Subsistemas de spacecraft

Un satélite se descompone en subsistemas funcionales. Este documento resume qué hace cada uno, sus métricas clave, ecuaciones de dimensionamiento, y opciones típicas.

## 1. Estructura (STR / MEC)

### Función
Mantener integridad durante lanzamiento (vibración, shock, aceleración) y operación (ciclos térmicos, micro-vibraciones, impactos MMOD).

### Cargas de lanzamiento (típico smallsat)
| Carga | Magnitud típica |
|-------|-----------------|
| Aceleración cuasi-estática axial | 5-8 g |
| Aceleración lateral | 3-5 g |
| Sine vibration | 0.8-1.25 g (2-100 Hz) |
| Random vibration | 6-15 g_RMS (20-2000 Hz) |
| Shock | 2000-6000 g (separación) |
| Acoustics | 140-145 dB OASPL |

### Frecuencias naturales mínimas (flight stability)
- Longitudinal: > 40 Hz (típico).
- Lateral: > 20 Hz.
- Verificación: análisis modal FEM + test de vibración sine sweep.

### Materiales comunes
| Material | ρ (kg/m³) | E (GPa) | σ_y (MPa) | Uso |
|----------|-----------|---------|-----------|-----|
| Al 7075-T6 | 2810 | 71 | 500 | Estructura general |
| Al 6061-T6 | 2700 | 68 | 275 | Brackets, paneles |
| Ti-6Al-4V | 4430 | 114 | 830 | Tanques, fittings críticos |
| CFRP laminado | 1550 | 135 (0°) | varies | Paneles, tubos |
| Honeycomb Al 5052 | ~50 (core) | — | — | Sandwich panels (face + core) |
| Invar 36 | 8100 | 141 | 280 | Óptica, baja expansión térmica |

### Diseño típico
- Sandwich panels Al-honeycomb Al-face sheets (0.3-0.5 mm) para estructura primaria.
- Tubos CFRP para optical benches y soportes de antenas.
- Brackets machined Al 7075 para interfaces de equipo.
- Fasteners: A286 o titanio lock-wired, siguiendo NASA-STD-5020.

## 2. Control térmico (TCS)

### Función
Mantener cada componente en su rango de operación y survival temperatures.

### Rangos típicos
| Componente | T_operation | T_survival |
|------------|-------------|------------|
| Electronics (COTS) | -20 a +50°C | -40 a +85°C |
| Batteries Li-Ion | 0 a +30°C | -20 a +50°C |
| Propellant lines | +5 a +40°C | +5 a +60°C |
| Star tracker (detector) | -30 a +30°C | -40 a +60°C |
| Solar arrays | -150 a +120°C | -170 a +150°C |

### Balance térmico estacionario (ver archivo 02 §3)
```
Q_in = Q_out
α·Φ_sun·A_sun + ε·σ·T_⊕⁴·A_⊕ + α·albedo·Φ_sun·A_⊕ + Q_internal = ε·σ·T_s⁴·A_radiator
```

### Presupuesto térmico
Para cada componente en cada modo (hot case, cold case, eclipse):
- Calor disipado (W).
- Temperatura máxima prevista.
- Heater power requerido en cold case.
- Margen: típicamente 11°C o 5°C + unidad de margen, según ECSS-E-ST-31C.

### Componentes de control
**Pasivos**:
- **MLI (Multi-Layer Insulation)**: 10-30 capas Kapton/Mylar aluminizado, separadas con netting Dacron. ε_efectivo ~0.02-0.05.
- **Thermal paints**: black paint (α=0.95, ε=0.90), white paint (α=0.20, ε=0.90).
- **OSR (Optical Solar Reflectors)**: α=0.08, ε=0.80 — para radiadores pasivos.
- **Heat pipes**: transferencia isoterma usando cambio de fase (amoníaco típico).
- **Louvers**: compuertas mecánicas que modulan área radiante según temperatura.

**Activos**:
- **Heaters** (resistive): capacidad típica 0.5-10 W por zona, controlados por thermostat o DA closed loop.
- **Pumped fluid loops**: grandes satélites (>1 kW disipación). Fluido: Coolanol, R134a.
- **PCM (Phase Change Materials)**: almacenamiento térmico transitorio.

## 3. Energía eléctrica (EPS)

### Función
Generar, almacenar, regular y distribuir potencia a todos los subsistemas.

### Arquitectura típica
```
Arreglo solar → PCU (regulator) → Distribución:
                    ↕                    ├── Subsistema A (5V, 28V, etc.)
                  Batería                ├── Subsistema B
                                         └── etc.
```

Buses comunes: **28 V** (legacy), **100 V** (moderno para alta potencia), **12 V** (CubeSats).

### Arreglo solar — dimensionamiento

Potencia BOL (beginning of life):
```
P_BOL = η_cell · A_cell · Φ_sun · cos(θ) · F_packing · (1/r_AU²)
```

Valores típicos (triple-junction GaAs, state-of-art):
- η_cell = 0.30-0.33 BOL.
- F_packing = 0.85-0.90.
- Φ_sun = 1361 W/m² a 1 AU.

Ejemplo: panel 1 m² apuntado normal a Sol, BOL, a 1 AU → ~370 W.

Degradación (EOL vs BOL):
- LEO 5 años: factor 0.90.
- GEO 15 años: factor 0.80.
- GEO 20 años: factor 0.70.
- Interplanetario Jupiter 5 años: factor 0.85 pero r=5.2 AU → flujo /27 → panel enorme.

### Tipos de celdas
| Tecnología | η BOL | Costo relativo | Uso |
|------------|-------|----------------|-----|
| Si | 14-17% | 1× | Estudiantil, baratos |
| GaAs single-junction | 18-20% | 5× | Legacy |
| GaAs triple-junction (InGaP/GaAs/Ge) | 28-30% | 10× | Estándar comercial |
| GaAs 4-junction IMM | 32-34% | 20× | High-end |
| Perovskite tandem | 25-28% | — | Investigación, no flight yet |

### Baterías
**Li-Ion** domina. Consideraciones:
- Energía específica: 100-175 Wh/kg nivel celda.
- Energía específica nivel pack (con BMS, harness, estructura): 80-140 Wh/kg.
- DoD (Depth of Discharge) máximo: 20-30% para >20,000 ciclos LEO, 50-80% para pocos ciclos GEO.
- Temperatura: 0-30°C operacional.
- **Passivation**: al fin de misión descargar completo para evitar explosión residual (requisito deorbit).

### Ejemplo dimensionamiento
Satélite LEO 100 kg, consumo nominal 80 W, eclipse = 36 min (LEO ~90 min orbit con 36 min eclipse peor caso SSO):
```
E_eclipse = 80 W × 0.6 h = 48 Wh
Capacity battery (30% DoD) = 48 / 0.3 = 160 Wh
Mass (100 Wh/kg pack) = 1.6 kg
```

Panel para recargar en 54 min de sol (asumir eficiencia 90% cargador):
```
P_panel_needed = 80 (load) + 48/(0.54·0.90) = 80 + 99 = 179 W promedio
Con cosine loss para panel fijo: P_panel_peak > 300 W → área ~1 m² de triple-junction.
```

### PCU / PDU
- **Direct Energy Transfer (DET)**: bus regulado a voltaje nominal, exceso disipado. Simple.
- **Peak Power Tracking (PPT/MPPT)**: electronics extraen el punto de máximo poder de panel. Mejor para rango de temperatura y sol.
- **Protection**: current limit, OCP, OVP, UVP. Latching current limiters (LCL) por carga.

## 4. Guidance, Navigation and Control (GNC) / ADCS

### Función
Determinar actitud y posición del spacecraft, controlar ambos a los valores deseados.

### Determinación de actitud (estimation)

**Sensores**:
| Sensor | Precisión | Masa | Potencia | Uso |
|--------|-----------|------|----------|-----|
| Sun sensor (coarse) | 1-5° | 50 g | 0.1 W | Safe mode, initial acquisition |
| Sun sensor (fine) | 0.01-0.1° | 200 g | 0.5 W | Nominal |
| Magnetómetro | 0.5-2° (depende modelo) | 100-300 g | 0.5 W | LEO |
| Earth sensor (horizon) | 0.05-0.5° | 500 g | 2-5 W | GEO histórico |
| Star tracker | 1-20 arcsec | 0.5-2 kg | 3-10 W | Alta precisión |
| Gyroscope (FOG, HRG, MEMS) | 0.001-1°/h bias | 0.5-5 kg | 5-30 W | Rate sense |
| GNSS receiver | ~1 m pos, 10 cm/s vel | 0.3-2 kg | 3-10 W | LEO-MEO |

**Algoritmos** (ver archivo 01 §5):
- TRIAD (determinación de actitud de dos vectores, no óptimo pero simple).
- QUEST (óptimo, minimiza criterio de Wahba).
- EKF / UKF para fusión multi-sensor.

### Actuadores

| Actuador | Torque típ | Momento | Uso |
|----------|------------|---------|-----|
| Magnetorquer | 0.1-30 Am² | — | LEO, desaturación RWs, low-precision |
| Reaction wheels | 10 mNm-100 mNm continuo, 30-500 mNm pico | 0.1-50 Nms | Pointing fino |
| Control Moment Gyro (CMG) | 1-10 Nm pico | 10-5000 Nms | Alta agilidad, grandes |
| Thrusters (cold gas, hidrazina) | 0.1-100 mN | — | Control + Δv |
| Tether | variable | — | Experimental |

### Modos operacionales típicos
- **Detumble**: eliminar tumbling post-separación (B-dot con magnetorquers).
- **Safe mode / Sun pointing**: apuntar paneles al Sol.
- **Acquisition**: resolver actitud con star tracker.
- **Nominal pointing**: modo operacional (payload apuntado).
- **Slew**: rotación grande entre objetivos.
- **Deorbit / end-of-life**: orientación de des-atitud para reentry.

### Presupuesto de pointing
Error total de apuntamiento = sqrt(sum of squares):
- Error de determinación (sensor noise): ~X arcsec.
- Error de control (deadband, cuantización): ~Y arcsec.
- Error estructural (flexión, térmico): ~Z arcsec.
- Alineamiento (mounting tolerance, thermal): ~W arcsec.

Total para Earth obs típica: 100-300 arcsec.
Para astronomía (JWST, Hubble): < 1 arcsec.

## 5. Propulsión (PPS) — ver archivo 04

Resumen de integración a nivel subsistema:
- Tanques: COPV (composite overwrapped pressure vessel) para gases de alta presión, metálicos para líquidos.
- Manifolds, regulators, latch valves, filters, pressure transducers, temperature sensors.
- Thrusters: 1-N, redundantes por pares (hot/cold redundancy).
- MEOP (Max Expected Operating Pressure) con factor de seguridad × 4 para presión de rotura (ISO 14623 para COPV).
- Cualificación: leak tests helio, burst, vibración, térmico, firing.

## 6. Comunicaciones (TT&C / payload data)

### División
- **TT&C (Telemetry, Tracking, Command)**: housekeeping, comandos, ranging. Low rate, high reliability.
- **Data downlink**: datos de payload. High rate.

### Bandas de frecuencia comunes
| Banda | Rango | Uso típico |
|-------|-------|-----------|
| VHF | 30-300 MHz | Amateur, smallsat TT&C legacy |
| UHF | 300 MHz-3 GHz | CubeSat TT&C |
| L | 1-2 GHz | Iridium, GPS, Globalstar |
| S | 2-4 GHz | TT&C estándar, NASA TDRSS |
| C | 4-8 GHz | Satcom legacy |
| X | 8-12 GHz | Space research downlink, SAR |
| Ku | 12-18 GHz | DTH broadcast, VSAT |
| Ka | 26-40 GHz | High-throughput, comms modernas |
| V/W | 40-75 GHz | Next-gen, rain fade severe |
| Optical (laser) | 200-300 THz | Alta tasa, atmospheric-limited |

### Link budget (ver archivo 02 §4 para fórmulas)
Presupuesto completo incluye:
- P_tx
- L_line_tx (cableado)
- G_tx (antena transmisora)
- EIRP = P_tx + G_tx - L_line
- Path loss (FSPL, atmospheric, rain, polarization)
- G_rx
- L_line_rx
- T_system (ruido: T_antenna + T_LNA + T_receiver)
- G/T de la estación terrena
- C/N₀ = EIRP + G/T - L_total + 228.6 (Boltzmann)
- Eb/N₀ = C/N₀ - 10·log(R_b)
- Margin = Eb/N₀_achieved - Eb/N₀_required

### Modulación y codificación (MODCOD)
- BPSK/QPSK: robusto, Eb/N₀ ~6 dB (BER 10⁻⁵ sin FEC).
- 8-PSK, 16-APSK: mayor tasa, mayor Eb/N₀.
- FEC: Reed-Solomon + convolucional, turbo, LDPC. Típicamente 3-5 dB de coding gain.
- CCSDS standards: TM/TC space packet, spacewire, file delivery protocol (CFDP).

### Ground segment
Estaciones terrenas: antenas 3-13 m típicas para smallsat, arrays fasos (KSAT, SSC, AWS Ground Station, Viasat RTE, Leaf Space) como servicio.

Ground segment "as a service": USD 5-30 por minuto de contacto (S/X-band), USD 200-500 por contacto Ka.

## 7. On-board computer (OBC) y flight software

### Hardware
- **Processors**: rad-hard LEON3/4 (SPARC), RAD750 (PowerPC), GR740 (quad-core LEON4), Vorago VA41620 (ARM M4). Para CubeSats: Xilinx Zynq, ARM Cortex no rad-hard.
- **Memory**: SRAM rad-hard + EDAC, MRAM (no-volátil rad-hard), NAND flash con scrubbing.

### Software
- **Real-time OS**: VxWorks, RTEMS (libre, usado en ESA), FreeRTOS, Zephyr.
- **Flight software frameworks**:
  - **NASA Core Flight System (cFS / cFE)** — open source, heritage.
  - **ESA Packet Utilisation Standard (PUS)** — estándar de telecomando/telemetría.
  - **OPS-SAT / OBSW** — implementaciones abiertas.

### Redundancia
- **Dual-string** con hot standby.
- **Watchdog timer** forzar reboot si hangs.
- **Scrubbing** de memoria para mitigar SEU.
- **Software voter** (TMR) para críticos.

## 8. Payload

Depende de la misión. Categorías comunes:
- **Earth observation**: cámara óptica (MS, HS), radar SAR, LIDAR atmosférico, radiómetros.
- **Comunicaciones**: transponders, phased arrays, ISL (inter-satellite links).
- **Navegación**: atómicos clocks, payloads de augmentation.
- **Ciencia**: espectrómetros, magnetómetros, particle detectors.
- **Deep space / prospección**: multi-spectral imagers, gamma ray spectrometer, neutron spectrometer, mass spectrometer, dust analyzer.

## 9. Arquitectura de datos on-board

Buses típicos:
- **MIL-STD-1553B**: 1 Mbps, bus legacy pero muy usado.
- **SpaceWire (ECSS-E-ST-50-12)**: serial 2-400 Mbps, punto a punto.
- **CAN bus**: bajo costo, CubeSat.
- **SpaceFibre**: 1-6.25 Gbps, nueva generación.
- **Ethernet time-triggered (TTE)**: algunos spacecraft modernos.

## 10. Integration and Test (AIT)

### Orden habitual
1. Incoming inspection + acceptance de cada caja.
2. Mechanical integration (structure → boxes → harness).
3. Electrical integration (continuity, isolation, polarity).
4. Functional test (FT): comprobar cada box responde.
5. Comprehensive performance test (CPT): escenarios operacionales.
6. Environmental campaign:
   - EMC pre-test.
   - Vibration.
   - Shock.
   - Thermal vacuum (TVAC) con ciclos + burn-in.
   - EMC formal.
7. Final CPT.
8. End-to-end test con ground segment real (ETE).
9. Pre-ship review → empaque y envío al launch site.

### Facilities LatAm
- **INPE LIT** (São José dos Campos, Brasil) — integración, shaker, cámara anecoica, TVAC.
- **CEATSA** (Bariloche, Argentina) — TVAC, EMC, vibración (sirvió SAOCOM, ARSAT).
- **Tecnológico de Monterrey** tiene infra limitada.
- Alternativa: Airbus (Toulouse), Thales Alenia (Cannes), IABG (Alemania), Intespace (Francia).

## Lecturas imprescindibles por subsistema

| Subsistema | Referencia |
|-----------|------------|
| General | SMAD (Wertz/Everett/Puschell) |
| Térmico | Gilmore, "Spacecraft Thermal Control Handbook" (2 vol) |
| Estructural | Sarafin, "Spacecraft Structures and Mechanisms" |
| ADCS | Markley & Crassidis |
| Power | Patel, "Spacecraft Power Systems" |
| Comms | Maral & Bousquet; Pratt, Bostian & Allnutt |
| Software | NASA cFS documentation; Gomes et al., "Real-Time Systems" |

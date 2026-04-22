# 02 — Física fundamental aplicada

La física que se necesita para diseño de misiones espaciales. Para cada rama: los conceptos irreducibles, las ecuaciones de trabajo, y dónde se usan.

## 1. Mecánica clásica

### Mecánica newtoniana
- Leyes de Newton.
- Conservación de momento lineal y angular — base de toda la dinámica de reentrada, separación de etapas, maniobras.
- Trabajo y energía — conservación de energía mecánica en el problema de dos cuerpos (ecuación vis-viva).
- Colisiones elásticas e inelásticas — útil para análisis de impactos de micro-meteoroides.

### Mecánica lagrangiana y hamiltoniana
- Coordenadas generalizadas, función de Lagrange L = T − V.
- Ecuaciones de Euler-Lagrange.
- Formulación hamiltoniana — indispensable para mecánica celeste avanzada y control óptimo.

**Ecuación vis-viva (energía específica en el 2-body problem)**:
```
v² = μ (2/r − 1/a)
```
Donde μ=GM del cuerpo central, r = distancia instantánea, a = semieje mayor. Útil para calcular velocidad en cualquier punto de una órbita conocida.

### Cuerpo rígido
- Tensor de inercia I.
- Ecuaciones de Euler de rotación (ver §4 de `01-matematicas.md`).
- Precesión, nutación, movimiento de torque libre — base de dinámica de spin-stabilized satellites.
- Teorema de ejes paralelos y ejes principales.

## 2. Gravitación

### Problema de dos cuerpos
- Ley de la gravitación universal.
- Conservación de energía y momento angular → órbitas cónicas (Kepler).
- Ecuación de Binet para trayectorias.

### Cuerpos N y perturbaciones
Ningún problema real es puro 2-body. Las perturbaciones relevantes:

1. **No esfericidad de la Tierra (J2, J3, J4...)**: la Tierra es un elipsoide achatado. J2 ≈ 1.0826 × 10⁻³ es el término dominante.
   - Causa regresión del nodo ascendente Ω, rotación del argumento de perigeo ω.
   - Se explota para **órbitas heliosíncronas** (SSO): Ω̇ = 360°/año se iguala al movimiento aparente del Sol ajustando inclinación ~98°.
   
   Regresión nodal J2:
   ```
   Ω̇ = −(3/2) n J2 (R_T/p)² cos(i)
   ```
   p = a(1−e²), R_T = radio terrestre, n = movimiento medio.

2. **Atracción de terceros cuerpos (Luna, Sol)**: dominante en órbitas altas (MEO/GEO, HEO).

3. **Presión de radiación solar (SRP)**: fuerza aprox. 9 μN/m² a 1 AU para superficies absorbentes. Dominante en satélites con alta área/masa (paneles, velas).

4. **Arrastre atmosférico**: crítico por debajo de ~700 km. Modelo de densidad:
   - Jacchia-Bowman (JB2008), NRLMSISE-00 — modelos operacionales.
   - Densidad varía 2-3 órdenes de magnitud con actividad solar.
   
   Fuerza de arrastre:
   ```
   F_D = −(1/2) ρ v² C_D A v̂
   ```

5. **Efectos relativistas**: relevantes para GPS, Galileo, navegación de alta precisión. Correcciones de ~38 μs/día.

### Referencia crítica
- **Vallado, "Fundamentals of Astrodynamics and Applications"** — de facto la biblia numérica de mecánica celeste aplicada. Incluye código MATLAB/C++.

## 3. Termodinámica y transferencia de calor

### Conceptos irreducibles
- Primer principio (energía), segundo principio (entropía).
- Ciclos termodinámicos: Brayton (turborreactor), Rankine (generación solar/nuclear), Otto/Diesel (no aplica), ciclos de cohetes.
- Gas ideal, gases reales, tablas de propiedades de combustibles y oxidantes.

### Transferencia de calor
- **Conducción**: Ley de Fourier `q = −k ∇T`.
- **Convección**: número de Nusselt, coeficiente h. En espacio (vacío) casi no aplica salvo en interior presurizado o dentro de sistemas fluídicos.
- **Radiación**: dominante en espacio. Stefan-Boltzmann:
  ```
  q_rad = ε σ T⁴
  ```
  σ = 5.67 × 10⁻⁸ W/(m²·K⁴), ε = emisividad.
  
  Balance térmico básico de un spacecraft en equilibrio:
  ```
  α A_abs Φ_solar + ε_ir A_ir σ T_⊕⁴ + Q_int = ε A_emit σ T_s⁴
  ```
  Φ_solar ≈ 1361 W/m² a 1 AU, varía como 1/r².
  T_⊕ ≈ 255 K (temp equivalente de Tierra en IR).
  Q_int = disipación interna.

### Ejemplo: temperatura de equilibrio de un satélite en LEO
Para un satélite esférico con α=ε=1 (cuerpo negro ideal), sin disipación interna, en sombra de Tierra:
```
T_eq_Sol  = (Φ_solar / (4σ))^(1/4) ≈ 279 K     (cuerpo negro, 1 AU)
T_eq_sombra = ∼150 K (en función del albedo terrestre y IR terrestre)
```

### Control térmico pasivo vs activo
- **Pasivo**: MLI (multi-layer insulation, mantas con ε_efectivo ~0.03), radiadores pintados (OSR), heat pipes, louvers.
- **Activo**: resistencias (heaters), loops de fluido, pumped two-phase systems (PTPS).

### Referencias
- Gilmore (ed.), "Spacecraft Thermal Control Handbook" (Aerospace Press) — **el** libro.
- Cengel, "Heat and Mass Transfer".

## 4. Electromagnetismo

### Conceptos irreducibles
- Ecuaciones de Maxwell (forma diferencial):
  ```
  ∇·E = ρ/ε₀
  ∇·B = 0
  ∇×E = −∂B/∂t
  ∇×B = μ₀J + μ₀ε₀ ∂E/∂t
  ```
- Onda plana en vacío: velocidad c = 1/√(μ₀ε₀), impedancia η₀ = 376.73 Ω.
- Polarización: lineal, circular. Comms típicos: circular (evita cross-pol fading).

### Antenas
- Directividad, ganancia, eficiencia.
- Patrones de radiación, beamwidth.
- Efectiva aperture A_ef = (λ²/4π) G.
- Ganancia de aperture típica parabólica:
  ```
  G ≈ η (π D / λ)²
  ```
  η ~0.55-0.70 (eficiencia).

### Link budget (simplificado)
```
P_rx = P_tx · G_tx · G_rx · (λ / 4πd)² · L_atm · L_pointing
```
En dB:
```
P_rx[dBW] = P_tx[dBW] + G_tx[dBi] + G_rx[dBi] − FSPL[dB] − L_atm[dB] − L_pointing[dB]
FSPL = 20 log₁₀(4πd/λ) = 32.45 + 20 log₁₀(f_MHz) + 20 log₁₀(d_km)
```

C/N₀ requerido vs logrado se compara para determinar margen de enlace (típico 3 dB).

### Efectos espaciales sobre hardware EM
- **Plasma ionosférico**: TEC (Total Electron Content) causa scintillation, retardo, rotación Faraday en banda baja. Relevante L-band y abajo.
- **Single Event Effects (SEE)**: partículas energéticas causan bit flips (SEU), latchups (SEL), burnouts (SEB). Motivo por el cual la electrónica espacial usa rad-hard o rad-tolerant parts.
- **Total Ionizing Dose (TID)**: dosis acumulada degrada semiconductores. Típico requerimiento LEO: 10-30 krad(Si) shielded. GEO o interplanetario: 100 krad o más.

### Referencias
- Balanis, "Antenna Theory: Analysis and Design".
- Maral & Bousquet, "Satellite Communications Systems".
- Jackson, "Classical Electrodynamics" (referencia dura).

## 5. Mecánica de fluidos y dinámica de gases

### Dónde aparece
- Propulsión (flujo interno en motores).
- Reentrada atmosférica (aerotermodinámica hipersónica).
- Recuperación de etapas (aerodinámica subsónica/transónica).
- Transporte en tanques (slosh, coriolis).

### Conceptos irreducibles
- Ecuaciones de Navier-Stokes.
- Número de Mach M = v/a, número de Reynolds Re = ρvL/μ.
- Flujo compresible: ondas de choque, relaciones de Rankine-Hugoniot.
- Flujo isentrópico:
  ```
  T/T₀ = (1 + ((γ−1)/2) M²)⁻¹
  p/p₀ = (T/T₀)^(γ/(γ−1))
  ρ/ρ₀ = (T/T₀)^(1/(γ−1))
  ```

### Tobera de cohete (nozzle) — ecuaciones de trabajo

**Flujo estrangulado (choked) en la garganta**:
```
ṁ = (A_t p₀ / √T₀) · √(γ/R) · (2/(γ+1))^((γ+1)/(2(γ−1)))
```

**Velocidad de salida (ideal, expansión hacia vacío)**:
```
v_e = √( (2γ/(γ−1)) · R T₀ · (1 − (p_e/p₀)^((γ−1)/γ)) )
```

**Empuje**:
```
F = ṁ · v_e + (p_e − p_∞) · A_e
```

**Impulso específico**:
```
Isp = F / (ṁ g₀)
```

### Reentrada
- Número de Knudsen, regímenes: continuo → transitorio → libre-molecular.
- Heating rate de punto de estancamiento (Sutton-Graves):
  ```
  q̇_s ≈ 1.83 × 10⁻⁴ √(ρ/R_n) v³     [W/cm²]
  ```
  R_n = radio de nariz, ρ en kg/m³, v en m/s.
- Corredor de reentrada: restringido por q̇_max (térmico) y g_max (estructural/tripulación).

### Referencias
- Anderson, "Modern Compressible Flow" + "Hypersonic and High-Temperature Gas Dynamics".
- Sutton & Biblarz, "Rocket Propulsion Elements" (ver también archivo 04).

## 6. Física de plasma

### Dónde aparece
- Propulsión eléctrica (Hall, iónica, MPD).
- Entorno espacial (plasma ionosférico, viento solar).
- Mediciones in-situ (sondas Langmuir).

### Conceptos irreducibles
- Cuasi-neutralidad, longitud de Debye, frecuencia de plasma.
  ```
  λ_D = √(ε₀ k T / (n e²))
  ω_p = √(n e² / (m ε₀))
  ```
- Movimiento en campos E y B: drift E×B, mirror magnético.
- Confinamiento magnético, ExB drift para Hall thrusters.
- Magnetohidrodinámica (MHD) ideal — para propulsión MPD y plasma solar.

### Electropropulsión — parámetros clave
- **Hall Effect Thruster (HET)**: propelente Xe (tradicional), Kr (Starlink, mejor $/kg). Isp 1500-3000 s. Empuje 50-500 mN por unidad. Eficiencia 50-60%.
- **Gridded Ion Thruster (GIT)**: Isp 3000-9000 s. Empuje 20-200 mN. Eficiencia 60-80%. Más desgaste de grid.
- **MPD (Magnetoplasmadynamic)**: alto empuje (N), requiere MW de potencia — fuera de alcance para startups salvo con nuclear power.

### Referencias
- Goebel & Katz, "Fundamentals of Electric Propulsion: Ion and Hall Thrusters" — JPL, gratis online.
- Chen, "Introduction to Plasma Physics and Controlled Fusion".

## 7. Entorno espacial

Resumen práctico de las amenazas que debe resistir un spacecraft según región.

### LEO (200-2000 km)
- Arrastre atmosférico.
- Oxígeno atómico (erosiona polímeros, Kapton).
- Escombros y micrometeoritos (MMOD) — blindaje Whipple.
- SAA (South Atlantic Anomaly) — radiación elevada.

### MEO y cinturones de Van Allen
- Radiación atrapada (electrones, protones) — hostil para electrónica.
- Órbitas como GPS (~20,000 km) están entre los dos cinturones.

### GEO (35,786 km)
- Charging electrostático por electrones calientes durante sub-tormentas → ESD descargas destructivas.
- Eventos solares (SEP) directamente sin protección magnetosférica.

### Espacio profundo
- GCR (Galactic Cosmic Rays): dosis 300-600 mSv/año tripulado.
- SEP (Solar Energetic Particles): eventos agudos que pueden matar tripulación o electrónica.
- Micro-meteoroides.

### Referencias
- Tribble, "The Space Environment".
- NASA-HDBK-4002: "Mitigating In-Space Charging Effects".

## 8. Física relativista — notas mínimas

### Dilatación temporal y GPS
Cada satélite GPS orbita a ~3.87 km/s a 20,200 km. Efectos:
- SR (velocidad): reloj corre -7.2 μs/día (más lento).
- GR (potencial gravitatorio): reloj corre +45.9 μs/día (más rápido por menor gravedad).
- Neto: +38.7 μs/día. Se corrige ajustando la frecuencia nominal del oscilador atómico.

### Referencias
- Ashby, "Relativity in the Global Positioning System" — Living Reviews in Relativity (acceso gratuito).

## Resumen del toolkit físico necesario

| Área | Nivel mínimo | Referencia libro |
|------|--------------|------------------|
| Mecánica clásica | Goldstein capítulos 1-9 | Goldstein/Poole/Safko |
| Termodinámica | Cengel completo | Cengel/Boles |
| Transferencia de calor | Incropera completo | Incropera |
| EM | Griffiths + Balanis antenas | Griffiths / Balanis |
| Fluidos | White capítulos clave | White / Anderson |
| Plasma | Chen capítulos 1-5 | Chen |
| Entorno espacial | Tribble completo | Tribble |

Este nivel se alcanza con ~18 meses de estudio dedicado siguiendo `09-plan-estudio.md`.

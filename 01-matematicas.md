# 01 — Matemáticas aplicadas al espacio

La matemática es la herramienta. No se necesita ser matemático de oficio — hay que ser fluido en las áreas que se usan todos los días en diseño de misiones y vehículos. Esta es la lista mínima y dónde aparece cada una.

## 1. Cálculo multivariable y análisis vectorial

**Dónde se usa**: Formulación de ecuaciones de movimiento, divergencia/rotor en fluidos y EM, gradientes de potencial gravitatorio.

**Conceptos clave**:
- Derivadas parciales, gradiente ∇f, divergencia ∇·**F**, rotor ∇×**F**, Laplaciano ∇²f.
- Teoremas integrales: Green, Stokes, Gauss (divergencia).
- Coordenadas curvilíneas: cilíndricas (r, θ, z), esféricas (r, θ, φ).
- Jacobiano para cambio de variables.

**Fórmulas críticas**:

Gradiente del potencial gravitatorio de un cuerpo puntual:
```
Φ(r) = -GM/r
g(r) = -∇Φ = -GM/r² r̂
```

Ecuación de continuidad (fluidos/plasma):
```
∂ρ/∂t + ∇·(ρv) = 0
```

**Referencias**:
- Marsden & Tromba, "Vector Calculus"
- Arfken, Weber, Harris, "Mathematical Methods for Physicists"

## 2. Ecuaciones diferenciales ordinarias

**Dónde se usa**: Prácticamente todo movimiento dinámico — trayectorias, control de actitud, vibraciones estructurales, transferencia de calor transitoria.

**Conceptos clave**:
- EDOs lineales y no lineales, sistemas de primer orden.
- Existencia, unicidad (Picard-Lindelöf).
- Estabilidad de Lyapunov, linealización en puntos de equilibrio.
- Transformada de Laplace para análisis de sistemas de control.

**Forma canónica de la ecuación de movimiento 2-body**:
```
r̈ = -(μ/r³) r    donde μ = GM
```
Esto es un sistema de 6 EDOs (posición y velocidad en 3D). No tiene solución analítica en forma cartesiana general pero sí se transforma en elementos orbitales donde 5 son constantes y sólo ν (anomalía verdadera) varía.

**Integración numérica**:
- Runge-Kutta 4 (RK4) — estándar para propagación orbital a corto plazo.
- RKF45, Dormand-Prince 8(7) — paso adaptativo, alta precisión.
- Bulirsch-Stoer — para problemas suaves con alta precisión.
- Gauss-Jackson, Encke — especializados para orbital sobre plazos largos (semanas-años).

**Referencias**:
- Boyce, DiPrima, "Elementary Differential Equations and Boundary Value Problems"
- Hairer, Nørsett, Wanner, "Solving Ordinary Differential Equations I & II" — biblia numérica.

## 3. Álgebra lineal

**Dónde se usa**: Transformaciones de coordenadas, cinemática de actitud, dinámica de sistemas multi-cuerpo, filtros de Kalman, análisis modal estructural, ML en operaciones.

**Conceptos clave**:
- Espacios vectoriales, base, rango, nulidad.
- Autovalores, autovectores, diagonalización.
- Formas cuadráticas, matrices definidas positivas.
- Descomposiciones: LU, QR, Cholesky, SVD.
- Cuaterniones para rotaciones (ver §4).

**Matriz de rotación 3-2-1 (Yaw-Pitch-Roll)**:
```
R_321(ψ,θ,φ) = R_x(φ) · R_y(θ) · R_z(ψ)
```
Donde cada R_i es la rotación elemental alrededor del eje i.

**Problema clásico de autovalores en análisis modal**:
```
(K - ω² M) φ = 0
```
K = matriz de rigidez, M = matriz de masa, ω = frecuencia natural, φ = modo. Esto lo usás para verificar que la frecuencia natural del spacecraft > frecuencias del launcher (típicamente >25-50 Hz).

**Referencias**:
- Strang, "Introduction to Linear Algebra" (MIT OCW 18.06)
- Trefethen & Bau, "Numerical Linear Algebra"

## 4. Cuaterniones y parametrizaciones de actitud

**Dónde se usa**: Control de actitud. Las matrices de rotación (9 números) tienen redundancia y los ángulos de Euler tienen gimbal lock. Los cuaterniones (4 números) evitan ambos problemas y son lo que se usa en flight software.

**Cuaternión unitario**:
```
q = q0 + q1 i + q2 j + q3 k     con  q0² + q1² + q2² + q3² = 1
```
También se escribe como (q_v, q0) donde q_v = (q1,q2,q3) es la parte vectorial.

**Rotación de un vector v**:
```
v' = q ⊗ v ⊗ q*
```
donde ⊗ es producto de Hamilton y q* = (−q_v, q0) es el conjugado.

**Relación cuaternión ↔ eje-ángulo (Rodrigues)**:
```
q = (cos(θ/2), ê · sin(θ/2))
```
donde ê es el eje unitario y θ el ángulo.

**Cinemática de actitud** (relación con velocidad angular ω en body frame):
```
q̇ = (1/2) Ω(ω) q
```
donde Ω(ω) es la matriz 4×4 antisimétrica construida con los componentes de ω.

**Dinámica rotacional (Euler)**:
```
I ω̇ + ω × (I ω) = τ
```
I = tensor de inercia (3×3), τ = torque externo total (perturbaciones + actuadores).

**Referencias**:
- Wie, "Space Vehicle Dynamics and Control" (2da ed)
- Markley & Crassidis, "Fundamentals of Spacecraft Attitude Determination and Control" — **el** libro de ADCS.

## 5. Probabilidad, estadística y filtros

**Dónde se usa**: Navegación (Kalman), mission assurance (Weibull en confiabilidad), planificación (Monte Carlo de Δv), procesamiento de telemetría.

**Filtro de Kalman extendido (EKF) — navegación estándar**:
Predicción:
```
x̂_k|k-1 = f(x̂_k-1|k-1, u_k-1)
P_k|k-1  = F_k-1 P_k-1|k-1 F_k-1ᵀ + Q_k-1
```
Corrección:
```
K_k = P_k|k-1 H_kᵀ (H_k P_k|k-1 H_kᵀ + R_k)⁻¹
x̂_k|k = x̂_k|k-1 + K_k (z_k − h(x̂_k|k-1))
P_k|k  = (I − K_k H_k) P_k|k-1
```
Esto lo usás para fusionar GPS + IMU + star tracker + horizon sensor.

**Unscented Kalman Filter (UKF)** — preferido cuando la no linealidad es fuerte; evita jacobianos.

**Distribución de Weibull (confiabilidad de componentes)**:
```
R(t) = exp(−(t/η)^β)
```
η = vida característica, β = parámetro de forma. β<1 infant mortality, β=1 exponencial (fallas aleatorias), β>1 wear-out.

**Simulación de Monte Carlo para presupuesto de Δv**:
Sumar contribuciones (inyección, corrección de curso, maniobras, dispersión, reserva) con incertidumbres y correr 10⁴-10⁶ muestras para obtener percentil 99 del Δv total requerido. Ese es el Δv que dimensiona el tanque, **no** el valor medio.

**Referencias**:
- Bar-Shalom, Li, Kirubarajan, "Estimation with Applications to Tracking and Navigation"
- Särkkä, "Bayesian Filtering and Smoothing"

## 6. Optimización

**Dónde se usa**: Diseño de trayectorias, asignación de recursos, control óptimo (LQR, MPC), optimización de masa/potencia a nivel sistema (MDO).

**Programación lineal y cuadrática**: scheduling de operaciones, asignación de power.

**Programación no lineal con restricciones**: diseño de trayectorias interplanetarias — minimizar Δv sujeto a ventana de lanzamiento, restricciones de flyby.

**Control óptimo (Pontryagin)**:
Hamiltoniano:
```
H = L(x,u,t) + λᵀ f(x,u,t)
```
Ecuaciones de Euler-Lagrange:
```
λ̇ = −∂H/∂x
0 = ∂H/∂u     (condición de optimalidad)
```
Esto aparece en optimización de trayectorias de bajo empuje.

**LQR (Linear Quadratic Regulator)** — control óptimo para sistemas lineales con costo cuadrático:
```
J = ∫ (xᵀQx + uᵀRu) dt
u* = −R⁻¹ Bᵀ P x       donde P resuelve la ecuación de Riccati:
AᵀP + PA − PBR⁻¹BᵀP + Q = 0
```

**Método directo vs indirecto para optimización de trayectorias**:
- **Directo** (colocación, pseudo-espectral — implementado en GPOPS-II, PSOPT) — discretizar trayectoria, resolver NLP. Más robusto, menos elegante.
- **Indirecto** — plantear condiciones necesarias de Pontryagin y shooter. Más preciso pero difícil de hacer converger.

**Referencias**:
- Nocedal & Wright, "Numerical Optimization"
- Betts, "Practical Methods for Optimal Control and Estimation Using Nonlinear Programming"

## 7. Álgebra tensorial e introducción a geometría diferencial

**Dónde se usa**: Relatividad general (correcciones GPS, navegación cerca de cuerpos masivos en décadas futuras), mecánica de medios continuos, electromagnetismo covariante.

Para fase inicial no es crítico. Se deja como tema avanzado.

**Fórmula práctica inmediata — dilatación temporal GPS**:
Los relojes en satélites GPS corren ~38.5 μs/día más rápido que en Tierra (efecto combinado SR + GR). Sin esta corrección el GPS acumularía error de 10 km/día.

**Referencias**:
- Schutz, "A First Course in General Relativity"
- Carroll, "Spacetime and Geometry"

## 8. Análisis de Fourier y procesamiento de señales

**Dónde se usa**: Comms digital (modulación, codificación), análisis de vibraciones, procesamiento de imágenes satelitales, filtrado de sensor noise.

**Transformada de Fourier**:
```
F(ω) = ∫ f(t) e^(-iωt) dt
```

**Teorema de Nyquist-Shannon**: frecuencia de muestreo ≥ 2× ancho de banda de la señal. Aliasing si no.

**Densidad espectral de potencia (PSD)** — como se caracteriza ruido de giroscopios, acelerómetros, y entornos de vibración de lanzadores. Las especificaciones son del tipo "20 g²/Hz entre 20 y 2000 Hz".

**Referencias**:
- Oppenheim & Schafer, "Discrete-Time Signal Processing"

## 9. Métodos numéricos para EDPs

**Dónde se usa**: CFD (reentrada atmosférica, propulsión, transferencia de calor), análisis estructural FEA, electromagnetismo computacional.

**Métodos principales**:
- Diferencias finitas (FDM)
- Elementos finitos (FEM) — estructural, térmico
- Volúmenes finitos (FVM) — CFD
- Métodos espectrales — alta precisión en geometrías simples

Software de industria:
- **CFD**: ANSYS Fluent, OpenFOAM (libre), SU2 (libre, aeroespacial)
- **FEM estructural**: NASTRAN, Abaqus, Code_Aster (libre)
- **Multi-físico**: ANSYS Workbench, COMSOL

**Referencias**:
- Anderson, "Computational Fluid Dynamics"
- Bathe, "Finite Element Procedures"

## 10. Teoría de grafos, combinatoria, complejidad (para software/ops)

**Dónde se usa**: Scheduling de operaciones, ruteo de tareas, diseño de redes terrestres, planificación de contactos.

Breve porque es tangencial al hardware pero importante a partir de la fase 2 cuando las operaciones se complejizan.

## Recordatorio práctico

Todo esto se puede aprender con:
1. MIT OpenCourseWare — 18.01, 18.02, 18.03, 18.06, 18.085, 18.086, 18.065.
2. 3Blue1Brown — intuición geométrica, no sustituye rigor pero acelera aprendizaje.
3. Python con NumPy/SciPy — resolver problemas numéricamente antes de atacar analíticamente.

El estudio matemático completo de esta lista toma ~2-3 años de dedicación seria part-time. No se puede saltear. Ver `09-plan-estudio.md`.

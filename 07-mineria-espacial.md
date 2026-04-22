# 07 — Minería y utilización de recursos espaciales

Este documento separa la **ciencia de los recursos** (qué hay y cómo se caracteriza) de la **economía real** (qué se puede hacer rentable en los próximos 20 años). Spoiler: en el horizonte de 20 años el negocio **no** es extracción y retorno a Tierra de metales — es información de prospección y tecnología ISRU para operaciones cislunares/marcianas.

## 1. Tipos de cuerpos objetivo

### Asteroides cercanos a la Tierra (NEOs)

**Clasificación orbital**:
- **Atiras** (totalmente dentro de órbita terrestre). Raros.
- **Atens** (a < 1 AU, q > Earth perihelio). Ejemplos: 2062 Aten, Bennu.
- **Apollos** (a > 1 AU, q < Earth aphelio). Mayoría de NEOs.
- **Amors** (a > 1 AU, q entre Earth aphelio y 1.3 AU). No cruzan órbita Tierra.

**Clasificación espectral (Tholen/Bus-DeMeo)**:
| Clase | Composición inferida | % NEOs | Albedo |
|-------|----------------------|--------|--------|
| **C** (y subclases B, G, F) | Carbonáceos, hidratos, posible agua | 10-15% | 0.03-0.09 |
| **S** (y Q, K, L) | Silicáticos, piroxeno, olivina, Fe-Ni minor | 30-40% | 0.10-0.25 |
| **X** (M, P, E) | Metálicos (M) — Fe-Ni, PGM | 10-15% | 0.03-0.50 |
| **D, T** | Primitivos, orgánicos | <5% | 0.02-0.07 |
| **V** | Diferenciados, basaltos (como Vesta) | raros | 0.30-0.55 |

**Targets de alto interés comercial**:
- **101955 Bennu** (C-type): visitado OSIRIS-REx, muestra retornada 2023. Hydrated minerals, agua estructural.
- **162173 Ryugu** (C-type): visitado Hayabusa2. Regolith con agua y orgánicos.
- **16 Psyche** (M-type, del cinturón principal): posiblemente 90% metal. Psyche mission NASA llega 2029. No NEO pero de alto interés metalúrgico.
- **99942 Apophis**: Sq-type, cercano flyby 2029 (37,000 km Tierra). Ventana excepcional de estudio.
- **469219 Kamoʻoalewa**: quasi-satélite Tierra, posible fragmento lunar. Misión Tianwen-2 (China) en curso.
- **2001 QJ142**: Δv razonable desde LEO (~5 km/s), C-type, target académico estándar de estudios.

### La Luna

**Recursos relevantes**:
- **Hielo de agua** en cráteres polares permanentemente en sombra (PSRs). Estimación: 10⁹-10¹⁰ kg en polo sur (LCROSS 2009, LRO, Chang'e, SLIM).
- **Regolith** — rico en Si, Fe, Al, Ti, Mg, O.
- **Helio-3** — atractivo teórico para fusión, pero <10 ppb en regolith. La **economía no cierra** con tecnología conocida: para recuperar 1 kg de ³He hay que procesar 150,000 toneladas de regolith. Proponen como moonshot, no como business plan.
- **KREEP** (K, REE, P) — terrenos específicos de cara cercana, interesantes para earth-rare elements.

### Marte (ISRU, no minería para retorno)
- CO₂ atmosférico (95%): convertible a O₂ (MOXIE demostrado) y metano (Sabatier + electrólisis agua).
- Hielo subsurface extendido.
- Regolith rico en Fe, Al, Si, Ti. Sulfatos y percloratos.
- Relevante para propelente de retorno (Marte → Tierra) y base permanente, **no** minería para mercado terrestre.

### Venus, Mercurio, lunas gigantes: fuera de horizonte de 20 años.

## 2. Δv desde LEO a targets — economía básica

Regla: a mayor Δv, más caro el tránsito. Los asteroides rentables son los de bajo Δv.

| Target | Δv mínimo LEO→rendezvous (km/s) |
|--------|---------------------------------|
| Luna (LLO) | 4.1 |
| Marte (MOR) | 5.6 |
| Venus (capture) | 5.3 |
| **Asteroides más accesibles** | **4.0-6.0** |
| 1999 AO10 | 4.0 |
| 2000 SG344 | 4.1 |
| 162173 Ryugu | 4.7 |
| 2008 EV5 | 4.9 |
| 101955 Bennu | 5.1 |
| 25143 Itokawa | 5.0 |
| Jupiter trojan | 7-9 |
| Ceres (cinturón principal) | 9.6 |

Para contexto: Δv retornar a Tierra con aerobraking ~0 km/s (sólo captura entrada), Δv retornar 1 km³ de masa asteroide a LEO = masivamente impráctico con propelente químico, ~manejable con propulsión eléctrica solar y misiones multi-año.

## 3. Arquitecturas de misión

### Prospección (flyby / rendezvous / sample return)
- **Flyby**: mínimo Δv, datos limitados (horas). Ej: NEAR Shoemaker (flyby Mathilde).
- **Rendezvous / orbit**: meses-años en target. Ej: Hayabusa, OSIRIS-REx, NEAR, DART.
- **Sample return**: retorno de pequeña muestra (g-kg). Ej: Hayabusa (Itokawa, 2010), Hayabusa2 (Ryugu, 2020), OSIRIS-REx (Bennu, 2023). CNSA Tianwen-2 (Kamoʻoalewa, en curso).

### Explotación in-situ (ISRU)
- **Regolith mining**: mechanical excavation, electrostatic beneficiation, magnetic separation.
- **Water extraction**:
  - Microwave heating → sublimación → condensación.
  - Vacuum heating de regolith congelado.
  - Reducción carbotérmica (regolith + CH4 → metales + CO + H2).
- **O₂ from regolith**:
  - MOXIE (Marte) — electrólisis de CO₂.
  - Molten regolith electrolysis (luna) — silicatos → O₂ + Si/metal. Demostrado en laboratorio, TRL 4-5.
  - FFC Cambridge electrolysis — similar.
- **Propellant production**:
  - Electrólisis de H₂O → H₂ + O₂ → hidrolox in-situ.
  - Sabatier: CO₂ + 4H₂ → CH₄ + 2H₂O → metalox.

### Full extraction & retorno (business clásico asteroid mining)
- **Mover el asteroide**: Asteroid Redirect Mission (NASA cancelada), gravitational tractor, masa en propelente.
- **Procesar en órbita cislunar**: lunar DRO o EML2.
- **Vender producto**: agua/propelente a clientes cislunar, metales a Tierra (sólo si competitivo con minería terrestre).

**Realidad 2026**: esto no está cerca. Nadie está a <10 años de ser rentable en esto. Las empresas que lo intentaron como core business quebraron o pivotearon:
- **Planetary Resources** (Bellevue, WA) — fundada 2010, financiada por Larry Page, Eric Schmidt, Ross Perot. Adquirida por ConsenSys 2018 y des-invertida.
- **Deep Space Industries** — fundada 2013. Adquirida por Bradford Space 2019, convertida en propulsión de agua para smallsats.
- **TransAstra** — pivoteó de extracción a propulsión eléctrica solar y servicios.
- **AstroForge** — activa, dos demos fallidas (Brokkr-1, Odin), sigue. Tesis: extraer PGM en órbita, retornar refined metal.
- **Karman+** — startup, Austin/Netherlands. Prospección.
- **Origin Space** (China) — NEO-01 demostrador 2021.

## 4. Economía real: hacer los números

### Escenario optimista de un asteroide PGM
Asteroide S o M de 100 m de diámetro, densidad 4500 kg/m³ → masa ~2.4 × 10⁹ kg.
Asumiendo 50 ppm PGM (platinum group metals), contiene ~120 toneladas PGM.
Precio Pt mercado ~USD 30M/ton → valor total **USD 3.6 B**.

Costo de misión: desarrollar + volar + procesar + retornar. Con tecnología actual:
- Desarrollo NRE: USD 2-5 B (primer-de-su-clase).
- Lanzamiento + mission ops: USD 500M-1B.
- Procesamiento y retorno: USD 1-2 B adicionales.

Total: USD 3.5-8 B. Para un solo asteroide. **Break-even marginal en el mejor caso, negativo en realista**. Y eso ignorando que si se mete 120 toneladas de Pt en el mercado, **el precio de Pt cae**.

### Escenario realista — agua / propelente cislunar
Pocas toneladas de agua extraída en Luna o NEO como propelente para operaciones cislunares:
- Costo lift agua desde Tierra a cislunar ~USD 50k/kg (decreciendo).
- Break-even ISRU: extraer agua a <USD 20k/kg operativo.
- Mercado: NASA Artemis, comerciales futuros, ISS successor.
- **Conclusión**: puede cerrar, pero requiere mercado comprador que todavía no existe.

### Escenario realista — información y payloads especializados
- Cada misión de prospección genera datos propietarios valiosos para futuros extractores.
- Vendor de instrumentos (espectrómetros, radar sounders) tiene mercado cautivo NASA/ESA.
- **Este es el negocio realista de una startup LatAm a 20 años**.

## 5. Tecnologías core para prospección

### Espectroscopía
- **VIS-NIR** (0.4-2.5 μm): composición superficial (silicatos, óxidos, hidratados).
- **MWIR** (3-5 μm): features de hidroxyl/water ice.
- **TIR** (8-14 μm): silicatos específicos, temperatura.
- **Gamma-ray / neutron**: elementos profundos, contenido de agua (H sensitive).

### Radar
- **Radar sounder (SHARAD/MARSIS heritage)**: subsurface structure.
- **Bi-static radar**: spacecraft + cubesat receiver → imaging sub-surface detallada.

### Otros
- **LIDAR**: topography precisa.
- **Magnetómetro**: diferenciación metalica vs silicátea.
- **Mass spectrometer** (TGA + MS): volátiles en muestra.
- **Raman / LIBS**: compositional microscale.
- **In-situ penetrator** + TGA: prospección subsuperficial.

## 6. ISRU química y procesos

### Reducción carbotérmica
```
SiO₂ + 2C → Si + 2CO    (1700°C)
2FeO + C → 2Fe + CO      (900°C)
3Al₂O₃ + 3C → 2Al + 3CO  (alta T, requiere electrólisis)
```

### Sabatier (Mars / cis-lunar con hidrógeno importado)
```
CO₂ + 4H₂ → CH₄ + 2H₂O    (300°C, Ni catalyst)
```

### Electrólisis
```
2H₂O → 2H₂ + O₂
2CO₂ → 2CO + O₂
```

### Water from carbonaceous regolith
Temperatura baja (100-300°C) en vacío extrae H₂O, CO₂, SO₂. Residuo mineral procesable después.

### Pirólisis solar directa
Concentración solar para alcanzar temperatura de reducción sin importar combustible. Sólo luz solar.

### Referencias
- Sanders et al., "ISRU Capability Roadmap" — NASA reports.
- Sonter, M.J. — trabajos seminales asteroid mining economics.
- "Asteroids: Prospective Energy and Material Resources" (Springer, Badescu ed.) — compendium.

## 7. Marco legal actualizado (2026)

### Outer Space Treaty (1967)
**Art. II**: "Outer space, including the Moon and other celestial bodies, is not subject to national appropriation by claim of sovereignty, by means of use or occupation, or by any other means."
- Interpretación: prohíbe apropiación **por estados**, no entidades privadas.
- Permite actividades, no propiedad del cuerpo.

### Ley USA — Commercial Space Launch Competitiveness Act (2015)
§ 51303: "A United States citizen engaged in commercial recovery of an space resource under this chapter shall be entitled to any asteroid resource or space resource obtained, including to possess, own, transport, use, and sell the asteroid resource or space resource obtained in accordance with applicable law, including the international obligations of the United States."

**Efecto**: empresa USA puede extraer y vender. Basis legal para startups asteroid mining domiciliadas USA.

### Luxembourg Space Resources Act (2017)
Similar al US Act. Primer país en ofrecer marco específico. Razón por la que muchas empresas de asteroid mining tienen subsidiary Luxembourg:
- iSpace Luxembourg
- SES Luxembourg
- Planetary Resources Luxembourg (cerrada)

### UAE Space Resources Act (2019)
Tercer marco. UAE activo en espacio (Mars Hope, Rashid rover).

### Artemis Accords (2020-)
Firmados por ~40 países incluyendo Brasil (2021), Colombia (2022), México (2024), Ecuador (2024), Argentina (2024), Perú (2025), Chile (2025), Uruguay (2025).
- Reconocimiento de "safety zones" alrededor de operaciones.
- Transparencia, coordinación.
- Compatible con OST.

### Lección para startup LatAm
- Incorporar en Delaware + subsidiary Luxembourg para legal clarity.
- Operar fisicamente en LatAm aprovechando costos.
- Firmar con agencias LatAm (AEB, AEM, CONAE) como proveedor de capacidad técnica.
- Position como proveedor de **información y tecnología**, no como claimant de recursos — evita debates legales largos.

## 8. Roadmap tecnológico a 20 años — qué puede hacer una startup LatAm

| Años | Actividad | Entregable |
|------|-----------|-----------|
| 0-5 | Estudios paramétricos, diseño conceptual, simulación. Participar en consorcios (ESA, NASA CLPS, JAXA HERACLES). | Papers, co-I en misiones, sub-contratos. |
| 5-10 | Hardware TRL 4-5: instrumento de prospección, proc. regolith lab-scale. | Breadboard integrado, resultados publicables. |
| 10-14 | TRL 6-7: tech demo en vuelo (CubeSat lunar o rideshare a órbita cislunar). | Hardware operacional en vuelo. |
| 14-18 | Primer payload propio en misión de terceros (CLPS, ESA Argonaut, JAXA). | Revenue de operación real. |
| 18-22 | Misión propia prime-contract con consorcio. NEO prospección. | Datos comerciales, IP. |

**Extracción real y retorno**: post-2045 para cualquiera, incluso con todo el capital del mundo. No cerrar el business plan en eso.

## 9. Nicho estratégico LatAm — hipótesis viable

**"Instrumental y procesamiento de datos de prospección remota para cuerpos menores, operando con talento LatAm y dominicilio legal optimizado."**

Ventajas competitivas sostenibles:
1. Costo de talento (científicos + ingenieros) 30-50% vs US/EU.
2. Zona horaria (6-8 horas UT típicamente) — solape con estaciones NASA Goldstone/Madrid/Canberra y ESA.
3. Latitud ecuatorial para operaciones que requieren contacto bajo horizon.
4. Acceso regulatorio Artemis Accords + flexibilidad legal para operar en mercados diversos.
5. Talento científico en áreas adyacentes (astronomía, geología, oceanografía — en Chile particularmente fuerte).

Desventajas a trabajar:
1. Ausencia de heritage propio — se compensa con partnerships iniciales.
2. Cadena de suministro limitada — se compensa importando hasta tener volumen.
3. Capital disponible — se compensa con grants + VC internacional.

## 10. Precedentes y lecturas

### Empresas relevantes
- **AstroForge** (USA) — asteroide PGM retrieval. 2 demos, tercera en camino.
- **TransAstra** (USA) — propulsión agua + prospección.
- **Karman+** (Netherlands/USA) — prospección.
- **Origin Space** (China) — demos.
- **ispace** (Japón/Luxembourg) — rovers lunares, HAKUTO.
- **Honeybee Robotics** (USA, ahora Blue Origin) — drill systems.
- **Dereum Labs** (México) — regolith simulant, ISRU studies.
- **OffWorld** (USA) — robots de minería.

### Libros imprescindibles
1. **Badescu (ed.), "Asteroids: Prospective Energy and Material Resources"** (Springer, 2013) — compendium técnico.
2. **Gertsch, Martin, "Mining Engineering: Space Applications"** — cross-over minería terrestre → espacio.
3. **Sanchez & McInnes** — papers sobre deflection y resource economics.
4. **Erickson, "Space Patrol"** / **Robb**, literatura gris sobre asteroid mining.

### Papers seminales
- Sonter, M.J., "The technical and economic feasibility of mining the near-earth asteroids" (1997).
- Sanchez, J.-P., & McInnes, C.R., "Assessment on the feasibility of future shepherding of asteroid resources" (Acta Astronautica, 2011).
- Ross, S.D., "Near-Earth asteroid mining" (Caltech, 2001).
- Elvis, M., "Let's mine asteroids — for science and profit" (Nature, 2012).

### Conferencias a seguir
- **Space Resources Roundtable** (anual, Colorado School of Mines).
- **IEEE Aerospace Conference** (Big Sky, Montana).
- **IAC** — International Astronautical Congress.
- **LPSC** — Lunar and Planetary Science Conference.
- **ASCEND** (AIAA).

### Research institutions clave
- **Colorado School of Mines** — programa de space resources, maestría específica.
- **University of Central Florida** — regolith simulant labs.
- **DLR / ESA** — planetary resources research programs.
- **JAXA ISAS** — Hayabusa heritage.

## Resumen ejecutivo

1. La física del asteroid mining es factible. La economía **no cierra** con tecnología actual + horizonte 20 años para "retornar metales a Tierra".
2. **El negocio viable** a 20 años es: tecnología de prospección (instrumentos, algorithms, simuladores), ISRU lunar para propelente local, y servicios operacionales para clientes (NASA, ESA, CNSA, startups).
3. Una startup LatAm puede posicionarse como **jugador nicho de alta competencia técnica con costo base ventajoso**, vendiendo principalmente a agencias internacionales y primes.
4. Roadmap: instrumentos → CubeSat demo lunar → payload en misión de terceros → prime de misión NEO.
5. Legal: domiciliar en USA + Luxembourg para extractables, ops en LatAm para desarrollo.
6. La extracción real de metales y retorno a Tierra queda fuera del horizonte 20 años para todos.

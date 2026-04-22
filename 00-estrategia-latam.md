# 00 — Estrategia LatAm: Roadmap a 20 años

## 1. La realidad LatAm 2026 — ventajas y restricciones

### Ventajas estructurales reales

**Geografía ecuatorial.** Una órbita ecuatorial requiere menos Δv desde latitudes bajas porque la velocidad tangencial terrestre en el ecuador es ~465 m/s vs ~408 m/s en Cabo Cañaveral (28.5°N). El ahorro efectivo para GEO es ~15-20% de propelente útil. Puertos explotables:
- **Alcântara, Brasil (CLA)** — 2.3°S, operativo como sitio de lanzamiento suborbital; acuerdos TSA con USA desde 2019 permiten hardware ITAR.
- **Centre Spatial Guyanais, Kourou** — 5.2°N, operado por CNES/ESA/Arianespace. Acceso vía partnerships con empresas francesas.
- **Ecuador** — proyecto histórico en Pacayacu; nunca operacional.
- **Perú (CONIDA)** — sitio de sondeo en Punta Lobos.

**Costo de talento.** Un ingeniero aeroespacial senior en Brasil/Argentina cuesta USD 35-70k/año vs USD 150-250k en USA. Esto permite equipos más grandes por el mismo capital, pero compite con salary arbitrage de empresas que contratan remoto desde USA.

**Universidades fuertes en áreas específicas.**
- USP, ITA (Instituto Tecnológico de Aeronáutica), Unicamp — Brasil
- Instituto Balseiro, UBA, UNLP, UNC — Argentina
- UNAM, IPN, Tec de Monterrey — México
- Universidad de los Andes, EAFIT, UIS — Colombia
- Universidad de Chile, UC, USACH — Chile

**Agencias espaciales existentes.**
- **AEB** (Agência Espacial Brasileira) — desde 1994
- **CONAE** (Argentina) — opera SAOCOM, SAC-D
- **AEM** (México) — desde 2010, poco funding propio
- **ASCo** (Colombia) — creada 2024
- **CONIDA** (Perú), **ASE** (Ecuador), **ABAE** (Venezuela) — variable funcionalidad

### Restricciones reales

1. **Capital de riesgo limitado para hardware.** VCs LatAm no están cómodos con deep tech de 5-10 años de runway. La mayor parte del capital aeroespacial tendrá que venir de USA/Europa o de grants gubernamentales.
2. **ITAR / EAR.** Cualquier componente dual-use (giroscopios, ciertos sensores, algoritmos de reentrada, propulsión de alto rendimiento) tiene restricciones de exportación desde USA. Brasil tiene TSA parcial, otros países no. Esto limita supply chain.
3. **Volatilidad macroeconómica.** Devaluación, inflación, controles de capital (Argentina). Un proyecto a 10 años necesita estructuración legal sofisticada (probablemente holding en Delaware o Luxemburgo).
4. **Fuga de cerebros.** Los mejores ingenieros terminan en SpaceX, Blue Origin, Rocket Lab, Planet, ESA. La startup debe ofrecer misión + equity + calidad de vida para retener.
5. **Infraestructura de test limitada.** Cámaras térmicas al vacío grandes, vibración de niveles espaciales, EMC — mayormente en Brasil (INPE LIT) y algunos laboratorios en Argentina (CEATSA). Todo lo demás es outsourcing internacional.

## 2. Roadmap 20 años — 5 fases de 4 años

### Fase 1 (Años 0-4): Fundación y caja

**Objetivo**: Construir equipo, generar revenue, acumular credibilidad técnica.

- **Producto primario**: Servicios de datos satelitales (Earth observation analytics), consultoría a agro/minería/petróleo, integración de ground stations comerciales.
- **Revenue target**: USD 500k ARR año 2, USD 3M ARR año 4.
- **Equipo**: 5-15 personas. Founders + 2-3 senior engineers + comercial + ops.
- **Capital**: Bootstrap + angels + seed <USD 2M. Programas: Start-Up Chile, Ignicion (Argentina), SP Ventures, BNDES Garagem.
- **Hitos técnicos**: Primera CubeSat 3U financiada por cliente (puede ser government contract o corporate R&D), lanzada como secondary payload en Falcon 9 / Electron / PSLV.
- **KPI aprender-por-hacer**: ADCS funcional en órbita, link comms establecido, power positive por órbita.

### Fase 2 (Años 4-8): Producto propio

**Objetivo**: Dejar de vender horas, vender unidades. Primer producto hardware recurrente.

- **Producto primario**: Bus CubeSat 6U-12U para servicios de nicho (IoT desde espacio, monitoreo metano, vigilancia marítima pesquera — nicho que Satellogic no cubre).
- **Revenue target**: USD 10-25M ARR.
- **Equipo**: 30-80 personas. Team dedicado de estructuras, aviónica, thermal, AIT (assembly-integration-test), mission ops, software de vuelo.
- **Capital**: Series A USD 15-40M. Inversores: SpaceFund, Seraphim, Y Combinator, Kaszek, Endeavor. También considerar FINEP/BNDES en Brasil.
- **Hitos técnicos**: 5-10 satélites propios operando constelación. Automatización de AIT. Flight heritage de aviónica propia.
- **Infraestructura**: Cleanroom ISO 8 propio, shaker table, thermal vacuum chamber propia.

### Fase 3 (Años 8-12): Launcher pequeño o bus grande

**Objetivo**: Moat defendible. Dos caminos — elegir uno según el talento y capital disponibles.

**Camino A — Lanzador dedicado pequeño**:
- Vehículo tipo Electron (200-300 kg a LEO) aprovechando Alcântara.
- Partnerships con AEB para infraestructura de rango de seguridad, tracking, propulsion ground test.
- Quemar USD 150-300M en desarrollo. Primer vuelo comercial año 10-12.

**Camino B — Bus mediano**:
- Bus 100-500 kg para órbitas específicas (constelaciones de comms regionales, Earth obs de alta resolución).
- Cliente ancla: contratos gubernamentales LatAm (Brasil, México, Colombia, Chile) o comerciales.
- Menos capital pero margen menor y competencia global fuerte (Astranis, Loft Orbital, Terran Orbital).

- **Revenue target**: USD 50-150M ARR.
- **Capital**: Series B-C USD 80-250M.
- **Hitos**: Si A, primer lanzamiento comercial. Si B, primeros satélites geoestacionarios propios.

### Fase 4 (Años 12-16): Deep space técnico

**Objetivo**: Demostrar tecnología para exploración. Payloads a Luna / NEO.

- **Producto primario**: Payloads de prospección para misiones de terceros. Espectrómetros multi-banda, magnetómetros, neutron spectrometer, LIDAR. Vender a NASA/ESA/JAXA/CNSA como contratistas, también a empresas mineras espaciales (AstroForge, TransAstra, Karman+).
- Misión propia de demostración: cubesat lunar (tipo CAPSTONE/Lunar IceCube, ~25 kg) en órbita halo NRHO o polar. Lanzada como secondary en una misión Artemis / CLPS.
- **Revenue target**: USD 200-500M ARR.
- **Hitos**: Primer hardware propio más allá de GEO. Contratos NASA/ESA como prime subcontractor.

### Fase 5 (Años 16-20+): Misión de prospección propia

**Objetivo**: Primera misión full-stack propia a un NEO.

- **Perfil de misión típico**: Spacecraft de 250-500 kg, Δv total ~5 km/s (LEO → NEO flyby/rendezvous), duración 2-4 años, propulsión eléctrica solar (Hall thruster xenón o criptón), payload espectral VIS-NIR-MWIR + radar bi-estático.
- **Target**: Un asteroide clase C con presencia de volátiles (agua) como 101955 Bennu, 162173 Ryugu, o uno similar fácilmente accesible (Δv < 6 km/s).
- **Financiamiento**: USD 400M-1B, mezcla de capital privado + gobiernos (AEB, AEM, CONAE) + partner prime internacional (Lockheed, Airbus, Northrop).
- **Modelo**: No se extrae — se vende información. Datos de composición, mapeo superficial, caracterización de regolito. A clientes: agencias, mineras espaciales, investigación académica.

**La extracción real queda para fase siguiente fuera del horizonte de 20 años.** Eso requiere precedente técnico (primer asteroide captured sample return), infraestructura cislunar de procesamiento, y mercado comprador establecido.

## 3. Modelo de negocio por fase — economía unitaria

| Fase | Producto | Unidad | Precio unitario | COGS | Margen bruto | Clientes típicos |
|------|----------|--------|-----------------|------|--------------|------------------|
| 1 | Servicios datos | Licencia anual | USD 20-200k | Infra + ops | 60-75% | Agro, minera, fintech |
| 2 | CubeSat | Satélite | USD 1-5M | USD 300-1500k | 50-70% | Gobiernos, telcos |
| 3a | Launcher | Vuelo | USD 7-15M | USD 4-9M | 35-45% | Gov + comerciales smallsat |
| 3b | Bus mediano | Satélite | USD 15-50M | USD 8-30M | 40-55% | Agencias, operadores comms |
| 4 | Payload deep-space | Instrumento | USD 10-80M | USD 4-40M | 50-60% | NASA/ESA/JAXA, mineras esp. |
| 5 | Misión NEO | Mission-as-service | USD 200M-1B | USD 150-700M | 25-40% | Consortium gov + privados |

## 4. Financiamiento — mapa de capital realista

### Seed (USD 250k-2M)
- **Fondos LatAm deep tech**: Kaszek Ventures, Monashees, Valor Capital, SP Ventures, Alaya, Platanus
- **Aceleradores**: Start-Up Chile (USD 80k equity-free), Ignicion Argentina, Parallel18 PR, 500 Startups LatAm
- **Grants gubernamentales**: FINEP Brasil, CORFO Chile, MINCyT Argentina (ANR), CONACyT México

### Series A-B (USD 15-60M)
- **Verticales espaciales**: SpaceFund, Seraphim Space, Starbridge, Promus Ventures, E2MC
- **VCs LatAm cross-border**: Kaszek, Qualcomm Ventures, General Atlantic (ya hicieron Satellogic)
- **Corporate VCs**: Airbus Ventures, Boeing HorizonX, Lockheed Martin Ventures

### Series C+ y crecimiento (USD 80M+)
- **Growth / deep tech**: SoftBank (hizo OneWeb), BlackRock, Fidelity, Wellington
- **Vía SPAC / IPO**: Satellogic precedente (2022, NASDAQ) — posible pero cost of capital elevado
- **Gobiernos**: BNDES, BID, IDB Lab, financiamiento bilateral (USTDA, AFD francés)

### Grants sin dilución
- **SBIR equivalentes**: FINEP Tecnova, CORFO I+D, MINCyT PICT/PIDDEF
- **ESA NPI via partnerships académicos** (requiere institución europea asociada)
- **Horizon Europe** — cluster 4/6 permiten associated countries LatAm con partner europeo lead

## 5. Marco regulatorio

### Tratados internacionales aplicables

- **Outer Space Treaty (1967)** — Art. II: ningún Estado puede reclamar soberanía sobre cuerpos celestes. NO prohíbe actividad comercial, pero crea ambigüedad sobre property rights de recursos extraídos.
- **Moon Treaty (1979)** — ratificado por muy pocos países, irrelevante en la práctica. Ningún país espacial mayor lo firmó.
- **Liability Convention (1972)** — el Estado de registro es responsable por daños causados por objetos espaciales. Importante para seguros.
- **Registration Convention (1976)** — obligación de registrar objetos ante UNOOSA.
- **Artemis Accords (2020-)** — Brasil firmó 2021, Colombia 2022, México 2024, Ecuador 2024, Argentina 2024, Perú 2025, Chile 2025, Uruguay 2025. Permite reconocimiento de "safety zones" alrededor de operaciones de recursos. **Esto es importante**: es el marco en el que una startup LatAm puede operar en recursos lunares/NEO con cobertura legal.

### Regulación nacional — resumen por país

- **Brasil**: AEB autoriza lanzamientos; Decreto 9.279/2018 + regulación de Alcântara. Más maduro regulatoriamente.
- **Argentina**: CONAE autoriza; Ley 23.877 sobre innovación científica. Telecomunicaciones bajo ENACOM.
- **México**: AEM coordina; necesita permisos SCT para comms.
- **Colombia**: ASCo recién creada (2024), marco en desarrollo.
- **Chile**: Política Nacional del Espacio 2023; no hay ley espacial específica aún.
- **Luxemburgo** — relevante porque su **Space Resources Law (2017)** reconoce propiedad privada de recursos extraídos. Many asteroid mining startups incorporate there. Considerar holding en Luxemburgo para cuando se llegue a fase 5.
- **USA** — **Commercial Space Launch Competitiveness Act (2015)** reconoce propiedad de recursos. Delaware para holding + Luxembourg para subsidiary de recursos es estructura común.

### Spectrum / ITU
Las frecuencias de comunicación satelital se coordinan vía ITU (Ginebra). Cada satélite debe tener filing ITU a través de una administración nacional. Brasil y Argentina tienen administradores activos (ANATEL, ENACOM). Esto es un activo: filings prioritarios para bandas Ka, Ku, X.

## 6. Precedentes LatAm — casos de estudio

### Satellogic (Argentina/USA)
- Fundada 2010 (Emiliano Kargieman + Gerardo Richarte + Lino Echeverría).
- Earth observation de alta resolución, constelación ~30 satélites.
- Hub técnico en Argentina, corporate en USA. Fabricación en Uruguay y Argentina.
- IPO NASDAQ 2022 vía SPAC CF Acquisition Corp V, valuación inicial USD 850M (después cayó ~90% en bear market).
- **Lección**: es posible. La capitalización bursátil post-IPO muestra que la categoría es dura en public markets, mejor mantenerse privado si es posible.

### INVAP (Argentina, estatal)
- Empresa estatal de Río Negro desde 1976.
- Satélites SAC, SAOCOM (radar L-band), ARSAT-1/2.
- **Lección**: la infraestructura técnica existe y es accesible via partnerships/hiring.

### Akaer (Brasil)
- Engenharia aeronáutica desde 1992. Aeroestructuras, radomes, soporte a Embraer y a programa CBERS.
- **Lección**: hay cadena de suministro aeroespacial en São José dos Campos que se puede aprovechar.

### Dereum Labs (México)
- Fundada 2022, enfoque ISRU lunar, regolith simulant y extractive processes.
- Pequeña, R&D stage, signed MoUs con AEM.
- **Lección**: hay espacio para jugadores nicho específicos con tesis clara.

### Otros a seguir
- **Leanspace** (Chile/Francia) — plataforma software para operaciones satelitales.
- **Perseus Space Technologies** (Argentina) — in-space mobility.
- **FR Inteligencia** (Brasil) — ground stations.
- **Mercurio Space** (Brasil) — componentes.

## 7. Primeros movimientos concretos (próximos 90 días)

Si vas en serio con esto, estos son movimientos que podés empezar ya mismo:

1. **Unirse a SGAC (Space Generation Advisory Council)** LatAm — acceso a red global de <35 años en espacio, becas IAC.
2. **Aplicar a IAC 2026** (International Astronautical Congress) con paper o estudiante scholarship.
3. **Identificar 3 mentores**: uno en Satellogic/INVAP, uno en NASA/ESA, uno ex-SpaceX/BlueOrigin de origen LatAm.
4. **Comenzar con la secuencia de `09-plan-estudio.md`** — esto es no-negociable, no se puede saltar.
5. **Crear un tracker de ecosistema**: spreadsheet con todas las empresas espaciales LatAm, su funding, stage, tech focus. Actualizarlo trimestralmente.
6. **Seguir newsletters clave**: Payload, SpaceNews, European Spaceflight, The Orbital Index, SpaceQ (Canadá), Space in Africa (para paralelos estratégicos).

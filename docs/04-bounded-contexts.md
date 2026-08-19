# Contextos acotados AS-IS

## 1. Cómo se modeló el AS-IS y por qué

Hoy Hogar de los Alpes se despliega como **un único monolito construido desde 2016**: una base de código, un esquema de base de datos, un ciclo de QA y despliegues de tres a cuatro horas. Desde el punto de vista técnico existe, por tanto, un solo artefacto.

Este mapa documenta las **islas lógicas de modelo** que ya existen dentro del monolito. Cada una tiene un dueño de facto en el organigrama y un lenguaje propio, pero **ninguna tiene una frontera técnica que la proteja**.

Los límites y los nombres de los contextos se expresan con el mismo **vocabulario de capacidad** que la sección de Dominios y Subdominios, de modo que ambas secciones puedan leerse en conjunto. La correspondencia **no es de uno a uno y no tiene por qué serlo**: los subdominios describen el espacio del problema y los contextos acotados el espacio de la solución. La tabla puente de la sección 5 documenta qué contexto realiza cada subdominio, incluidos los casos en los que el monolito no respeta la frontera.

Los límites se derivaron cruzando tres fuentes de evidencia:

| Fuente | Qué aporta |
|---|---|
| **Los subdominios acordados por el equipo** | La descomposición de capacidades de negocio de la sección anterior, que este mapa realiza |
| **Los procesos del enunciado** (Marketplace, Siniestros y pólizas, Verificación de proveedores) | Las capacidades operativas reales y los puntos donde el trabajo cambia de manos |
| **El organigrama y los sistemas externos** | El dueño de facto de cada capacidad y las fronteras que HdA no controla |

Es importante subrayar una decisión de lectura: **este mapa está deliberadamente lleno de anti-patrones**. La malla de Shared Kernel, el Conformist frente a más de treinta partners y la ausencia total de capas anticorrupción no son propuestas de diseño; son el diagnóstico. El TO-BE existe precisamente para eliminarlos.

### 1.1 Dos contextos que se retiraron del mapa

Versiones anteriores de este mapa incluían **Gestión de Pólizas y Coberturas** y **Evaluación y Aprobación de Siniestros**. Ambos se retiraron porque el enunciado atribuye esas capacidades a la aseguradora, no a HdA:

> «la aseguradora hace la **evaluación previa** y **aprueba** la atención»
>
> «el partner **crea el trabajo** mediante las integraciones del sistema»
>
> «HdA se encarga del ciclo de vida completo **del trabajo**»


---

## 2. Contextos acotados identificados

### 2.1 Dominio Servicios para el hogar (11 contextos)

| # | Contexto | Descripción del contexto | Equipo dueño |
|---|---|---|---|
| 1 | **Captura y Diagnóstico de Trabajos** | Capta la necesidad del hogar por la web y la aplicación móvil, la diagnostica mediante el asistente conversacional y la estructura como un Trabajo con categoría, urgencia, ubicación y evidencia inicial. | Asistente IA |
| 2 | **Riesgo y Fraude** | Detecta fraude y evalúa el riesgo de trabajos, proveedores y pagos, y alimenta la priorización y la automatización de otros procesos con modelos analíticos. | Datos e IA |
| 3 | **Orquestación de Trabajos** | Gestiona el ciclo de vida del Trabajo desde su creación hasta su cierre, incluyendo sub-trabajos, actividades, dependencias, paralelismo y novedades. | Workflows |
| 4 | **Cotizaciones** | Gestiona la solicitud, recepción, evaluación y selección de cotizaciones asociadas a un Trabajo, incluyendo solicitudes de información adicional y visitas al predio. | Cotizaciones |
| 5 | **Matching de Proveedores** | Determina los proveedores candidatos y resuelve la asignación considerando categoría, zona, disponibilidad, elegibilidad y las redes permitidas por el partner. | Publicación y Búsqueda |
| 6 | **Gestión de Ejecución** | Coordina la ejecución y el seguimiento de los trabajos apoyándose en los cerca de 100 agentes de gestión, incluyendo actividades, novedades y cumplimiento de las condiciones acordadas. | Gestión de agentes |
| 7 | **Red de Proveedores** | Administra la red de profesionales y empresas, sus servicios declarados, cobertura geográfica, disponibilidad y reputación. | Registro |
| 8 | **Confianza de Proveedores** | Verifica y acredita a proveedores y técnicos frente a los requisitos propios de HdA y determina para qué servicios y zonas quedan habilitados. | Acreditación |
| 9 | **Evidencia, Calidad y Garantías** | Gestiona la aceptación del trabajo, las reclamaciones de calidad, las garantías, las disputas y las compensaciones, y consolida la reputación del proveedor. | Calidad y disputas |
| 10 | **Procesamiento de Pagos** | Gestiona el cobro, la retención, la liberación, la devolución y la conciliación de los pagos del canal Marketplace, y las liquidaciones a los proveedores. | Pagos |
| 11 | **Plataforma** | Provee identidad, control de acceso, notificaciones y las clases base compartidas por todo el monolito, de las que dependen los demás módulos. | Plataforma |

### 2.2 Dominio Atención de Solicitudes de Partner B2B2C (5 contextos)

| # | Contexto | Descripción del contexto | Equipo dueño |
|---|---|---|---|
| 12 | **Entrada de Solicitudes de Partner** | Recibe las solicitudes ya aprobadas que los partners B2B2C crean por integración, tanto de siniestros como de instalaciones, las registra y mantiene el estado sincronizado con el sistema del partner. | Integraciones B2B2C |
| 13 | **Reglas y Orquestación de Partner** | Concentra las condiciones de todos los partners B2B2C —SLA, redes permitidas, montos máximos, pasos de aprobación, compliance y auditoría— y orquesta la atención de la solicitud aprobada hasta convertirla en un Trabajo. | Reglas de Partner |
| 14 | **Elegibilidad para Red de Partner** | Determina qué proveedores están homologados por cada partner y pueden participar en la atención de sus solicitudes. | Reglas de Partner |
| 15 | **Evidencia y Auditoría** | Gestiona la recopilación y consolidación de las evidencias que exige cada partner para soportar la ejecución, la auditoría y el cierre. | Gestión de agentes |
| 16 | **Facturación a Partners** | Consolida las evidencias, formaliza el cierre del Trabajo y genera la información necesaria para facturar al partner según el acuerdo comercial. | Finanzas y Tesorería |

### 2.3 Sistemas externos (5)

No son propiedad de HdA. Hoy sus modelos entran al dominio sin traducción.

| Sistema | Descripción | Cómo se integra hoy |
|---|---|---|
| **Sistemas de Partner** | Sistemas propios de las más de 30 aseguradoras, bancos y comercios que originan trabajos de siniestros e instalaciones. Cada partner define reglas, pasos, formatos y requisitos de compliance distintos. | REST, SOAP y archivos planos según el partner |
| **Sistema de Antecedentes Judiciales** | Sistema de la Policía Nacional consultado para verificar los antecedentes judiciales de cada persona que visitará el predio de un cliente. | Portal web consultado manualmente por un agente de verificación |
| **Registro Mercantil** | Registro mercantil de la Cámara de Comercio consultado para comprobar la existencia y el estado legal de los proveedores que son empresas. | Portal web consultado manualmente; el certificado se adjunta como archivo al expediente |
| **Entidades Certificadoras** | Entidades certificadoras y consejos profesionales que validan la vigencia de matrículas, títulos y certificaciones técnicas de los proveedores. | Solicitud manual con respuesta de 24 a 48 horas |
| **Pasarela de Pagos** | Pasarela de pagos externa que ejecuta el cobro, la retención, la liberación y la devolución del dinero del canal Marketplace. | SDK invocado de forma síncrona desde el módulo de pagos |

### 2.4 Diagrama del Context Map AS-IS

![Context Map AS-IS](context-map-as-is_ContextMap.png)

*Figura 1. Context Map AS-IS: 16 contextos internos, 5 sistemas externos y 34 relaciones. Generado a partir de `context-map-as-is.cml`.*

**Orquestación de Trabajos** es el punto donde converge prácticamente todo el acoplamiento: participa en 8 de las 34 relaciones y es el contexto que ningún equipo puede modificar sin coordinar con los demás.

---

## 3. Relaciones y tipos de integración

Se identificaron **34 relaciones** entre los 16 contextos internos y los 5 sistemas externos. La columna *mecanismo real* es deliberadamente concreta: en el AS-IS no existen protocolos de integración entre contextos, existen llamadas en el mismo proceso, tablas compartidas y, en tres casos, personas copiando datos a mano.

| Patrón | Cantidad | Qué significa en el AS-IS |
|---|---|---|
| Shared Kernel | 20 | Mismo modelo, misma base de datos, misma transacción |
| Customer / Supplier | 8 | Lectura directa de la base operativa o herencia de clases base, sin contrato |
| Conformist | 6 | Sistemas de terceros adoptados sin capa anticorrupción |

### 3.1 Shared Kernel (20 relaciones)

Dos o más contextos comparten y modifican el mismo modelo dentro de la misma base de datos y la misma transacción. Ningún equipo puede cambiarlo sin coordinarse con los demás.

| Contextos | Mecanismo real de integración |
|---|---|
| Riesgo y Fraude ↔ Captura y Diagnóstico de Trabajos | El asistente conversacional construye la solicitud y persiste la especificación del trabajo dentro del mismo proceso y la misma transacción |
| Captura y Diagnóstico de Trabajos ↔ Orquestación de Trabajos | La solicitud del hogar instancia directamente las tablas trabajo y sub_trabajo del esquema compartido |
| Orquestación de Trabajos ↔ Cotizaciones | Llamadas in-process y llave foránea sub_trabajo_id en el mismo esquema; un cambio de alcance reinicia la cotización en la misma transacción |
| Orquestación de Trabajos ↔ Matching de Proveedores | La publicación y el proveedor asignado son columnas de estado del propio sub-trabajo |
| Orquestación de Trabajos ↔ Gestión de Ejecución | El seguimiento de la ejecución escribe sobre las mismas filas del trabajo que gobierna el motor de flujo |
| Orquestación de Trabajos ↔ Procesamiento de Pagos | La retención y la liberación de fondos se ejecutan en la misma transacción de la transición de estado del trabajo |
| Orquestación de Trabajos ↔ Reglas y Orquestación de Partner | Las reglas de más de 30 partners están embebidas como condicionales dentro del motor de flujo del monolito |
| Gestión de Ejecución ↔ Cotizaciones | Una novedad dispara la recotización invocando directamente el servicio de cotizaciones dentro del monolito |
| Gestión de Ejecución ↔ Evidencia, Calidad y Garantías | Disputas y garantías son tablas hijas del trabajo con borrado en cascada; el cierre y la aceptación ocurren en la misma transacción |
| Gestión de Ejecución ↔ Evidencia y Auditoría | Las evidencias se adjuntan al trabajo desde la misma consola operativa y comparten el servidor de archivos de la aplicación |
| Matching de Proveedores ↔ Red de Proveedores | El matching resuelve la oferta con un JOIN SQL directo sobre proveedor, servicio_declarado, cobertura y disponibilidad |
| Matching de Proveedores ↔ Confianza de Proveedores | El filtro de elegibilidad consulta en línea el estado de acreditación; la regla de confianza vive dentro de la consulta de búsqueda |
| Matching de Proveedores ↔ Reglas y Orquestación de Partner | La red de proveedores permitida por el partner se evalúa dentro de la misma consulta que ordena los candidatos |
| Red de Proveedores ↔ Confianza de Proveedores | El estado de verificación es una columna de las tablas proveedor y técnico; el expediente y el perfil comercial son el mismo registro |
| Evidencia, Calidad y Garantías ↔ Red de Proveedores | La reputación se materializa como campo calculado sobre la tabla proveedor mediante un trigger |
| Entrada de Solicitudes de Partner ↔ Reglas y Orquestación de Partner | La orquestación lee y escribe el mismo registro de siniestro que mantiene el módulo de recepción |
| Reglas y Orquestación de Partner ↔ Elegibilidad para Red de Partner | La red permitida y las homologaciones vigentes se leen de la misma tabla de acuerdo comercial del partner |
| Elegibilidad para Red de Partner ↔ Confianza de Proveedores | La homologación del partner se persiste como columna adicional del expediente de acreditación de HdA |
| Evidencia y Auditoría ↔ Facturación a Partners | El cierre valida la completitud de la evidencia recorriendo las tablas hijas del trabajo dentro de la misma transacción |
| Facturación a Partners ↔ Orquestación de Trabajos | La generación de ítems facturables recorre el histórico de trabajo y sub_trabajo con consultas directas sobre el esquema operativo |

### 3.2 Customer / Supplier (8 relaciones)

El contexto aguas abajo depende del modelo de otro sin poder negociar un contrato: consulta la base de datos operativa directamente, o hereda las clases base de la plataforma, y cualquier migración de esquema lo rompe.

| Upstream → Downstream | Mecanismo real de integración |
|---|---|
| Gestión de Ejecución → Riesgo y Fraude | Consultas de solo lectura sobre la base de datos operativa para priorización y automatización; no existe canal de eventos |
| Procesamiento de Pagos → Riesgo y Fraude | Extracción periódica desde el esquema de pagos para detección de fraude, con exportes a hoja de cálculo |
| Evidencia, Calidad y Garantías → Riesgo y Fraude | Lectura directa de disputas y calificaciones para alimentar modelos analíticos |
| Facturación a Partners → Procesamiento de Pagos | La liquidación consulta los ítems facturables generados por el cierre mediante acceso directo a sus tablas |
| Plataforma → Orquestación de Trabajos | Clases base, identidad y notificaciones de las que hereda el motor de flujo; no hay contrato, se hereda directamente de las clases del paquete común |
| Plataforma → Red de Proveedores | El proveedor extiende la cuenta genérica de plataforma y comparte con ella la tabla de identidad |
| Plataforma → Entrada de Solicitudes de Partner | Las credenciales de los más de 30 partners son cuentas técnicas del mismo esquema de identidad |
| Plataforma → Gestión de Ejecución | Los roles y permisos de los cerca de 100 agentes están definidos en el modelo de acceso genérico |

### 3.3 Conformist frente a sistemas externos (6 relaciones)

HdA no controla ninguno de estos modelos y los adopta tal cual, sin capa anticorrupción.

| Upstream → Downstream | Mecanismo real de integración |
|---|---|
| Sistemas de Partner → Entrada de Solicitudes de Partner | Un adaptador distinto por cada uno de los más de 30 partners, en REST, SOAP y archivos planos; el modelo externo entra sin traducción al dominio |
| Sistemas de Partner → Reglas y Orquestación de Partner | Las condiciones comerciales y de compliance de cada partner se replican tal cual en la configuración del monolito |
| Sistema de Antecedentes Judiciales → Confianza de Proveedores | Consulta manual: un agente ingresa al portal de la Policía Nacional y transcribe el resultado al expediente |
| Registro Mercantil → Confianza de Proveedores | Consulta manual del registro mercantil y del estado legal en Cámara de Comercio; el certificado se adjunta como archivo |
| Entidades Certificadoras → Confianza de Proveedores | Validación de títulos y matrículas con respuesta de 24 a 48 horas que bloquea el avance del expediente |
| Pasarela de Pagos → Procesamiento de Pagos | SDK invocado de forma síncrona dentro de la transacción de negocio; los códigos de estado de la pasarela se persisten en el modelo de dominio |

---

## 4. Relación entre equipos

Los equipos provienen del organigrama del enunciado. En ContextMapper se modelan como `BoundedContext` de tipo `TEAM` dentro de un `ContextMap` de tipo `ORGANIZATIONAL`, que por restricción de la gramática vive en un archivo aparte.

| Equipo | Área | Contexto o contextos de los que es dueño |
|---|---|---|
| **Asistente IA** | CTO | Captura y Diagnóstico de Trabajos |
| **Datos e IA** | CTO | Riesgo y Fraude |
| **Publicación y Búsqueda** | CTO | Matching de Proveedores |
| **Registro** | CTO | Red de Proveedores |
| **Acreditación** | CTO | Confianza de Proveedores |
| **Workflows** | CTO | Orquestación de Trabajos |
| **Cotizaciones** | CTO | Cotizaciones |
| **Integraciones B2B2C** | CTO | Entrada de Solicitudes de Partner |
| **Reglas de Partner** | CTO | Reglas y Orquestación de Partner · Elegibilidad para Red de Partner |
| **Plataforma** | CTO | Plataforma |
| **Gestión de agentes** | COO | Gestión de Ejecución · Evidencia y Auditoría |
| **Calidad y disputas** | COO | Evidencia, Calidad y Garantías |
| **Pagos** | CFO | Procesamiento de Pagos |
| **Finanzas y Tesorería** | CFO | Facturación a Partners |
| **Riesgo y cumplimiento** | CFO | Revisión reactiva sobre la base operativa; no es dueño de ningún contexto |
| **Wallet y préstamos** | CFO | Dominio TO-BE de Servicios financieros para proveedores |

![Vista organizacional AS-IS](team-map-as-is_ContextMap.png)

*Figura 2. Vista organizacional AS-IS: 16 equipos y 23 relaciones, 13 de ellas Partnership. Generada a partir de `team-map-as-is.cml`.*

**Hallazgo principal: el Partnership del AS-IS es forzado.** De las 23 relaciones entre equipos, 13 son Partnership, pero ninguna es una alianza elegida: son dependencias impuestas por el código compartido. Ningún equipo puede liberar sin coordinar con los demás, y Workflows participa en siete de ellas. Esto explica de forma directa los despliegues de 3-4 horas, las semanas de QA y el hecho de que los equipos se bloqueen entre sí. También anticipa el mayor riesgo del plan de crecimiento: **duplicar el equipo de ingeniería de 50 a 100 personas sobre esta estructura multiplica el costo de coordinación, no la capacidad de entrega.**

**Hallazgo secundario: el equipo Plataforma no tenía contexto.** Aparecía en el mapa organizacional con cuatro relaciones aguas arriba —identidad, acceso y notificaciones de las que depende todo el monolito— pero no existía ningún contexto acotado que le correspondiera. El hueco se hizo visible al contrastar el mapa con los subdominios genéricos acordados, y se corrigió añadiendo el contexto **Plataforma**.

---

## 5. Trazabilidad: del subdominio al contexto y a la evidencia

Cada contexto acotado realiza uno o más de los subdominios acordados por el equipo y se sustenta en evidencia explícita del enunciado. Ningún contexto fue inventado. **Cuando un subdominio no tiene contexto propio en el AS-IS es porque el monolito no respeta esa frontera, y eso mismo constituye un hallazgo.**

### 5.1 Tabla puente: subdominio → contexto

Recorre los 17 subdominios acordados y señala qué contexto los realiza. Es el puente entre el espacio del problema y el espacio de la solución.

| Dominio | Subdominio acordado | Tipo | Contexto que lo realiza | Observación |
|---|---|---|---|---|
| Servicios para el hogar | **Captura y diagnóstico de trabajos** | Núcleo | Captura y Diagnóstico de Trabajos |  |
| Servicios para el hogar | **Orquestación de trabajos** | Núcleo | Orquestación de Trabajos · Gestión de Ejecución | Dos contextos realizan este subdominio: el motor de flujo y la operación con agentes |
| Servicios para el hogar | **Confianza de proveedores** | Núcleo | Confianza de Proveedores |  |
| Servicios para el hogar | **Matching de proveedores** | Núcleo | Matching de Proveedores |  |
| Servicios para el hogar | **Red de proveedores** | Soporte | Red de Proveedores |  |
| Servicios para el hogar | **Cotizaciones** | Soporte | Cotizaciones |  |
| Servicios para el hogar | **Evidencia, calidad y garantías** | Soporte | Evidencia, Calidad y Garantías |  |
| Servicios para el hogar | **Reputación** | Soporte | **— sin contexto propio —** | La reputación es un campo calculado por un disparador sobre la tabla `proveedor`: el monolito no respeta esta frontera. En el TO-BE sí es un contexto |
| Servicios para el hogar | **Riesgo y fraude** | Soporte | Riesgo y Fraude |  |
| Servicios para el hogar | **Procesamiento de pagos** | Genérico | Procesamiento de Pagos |  |
| Servicios para el hogar | **Identidad y acceso** | Genérico | Plataforma | Un solo contexto realiza los dos subdominios genéricos |
| Servicios para el hogar | **Notificaciones** | Genérico | Plataforma |  |
| Atención de Solicitudes de Partner B2B2C | **Entrada de solicitudes de partner** | Núcleo | Entrada de Solicitudes de Partner |  |
| Atención de Solicitudes de Partner B2B2C | **Reglas y orquestación de partner** | Núcleo | Reglas y Orquestación de Partner | Fusiona las tres piezas que en el AS-IS compartían la tabla `acuerdo_partner` |
| Atención de Solicitudes de Partner B2B2C | **Elegibilidad para red de partner** | Núcleo | Elegibilidad para Red de Partner |  |
| Atención de Solicitudes de Partner B2B2C | **Evidencia y auditoría** | Soporte | Evidencia y Auditoría |  |
| Atención de Solicitudes de Partner B2B2C | **Facturación a partners** | Soporte | Facturación a Partners |  |

### 5.2 Evidencia por contexto

| Contexto | Subdominio que realiza | Tipo | Evidencia en el enunciado |
|---|---|---|---|
| **Captura y Diagnóstico de Trabajos** | Captura y diagnóstico de trabajos | Núcleo | Slide Clientes · Marketplace B2C (asistente conversacional que diagnostica problema, categoría y urgencia) · Flujo Marketplace, paso 1 |
| **Riesgo y Fraude** | Riesgo y fraude | Soporte | Slide Estrategia y visión · IA en todas las etapas del negocio · Detección de fraude y priorización sobre la base operativa |
| **Orquestación de Trabajos** | Orquestación de trabajos | Núcleo | Slide Servicios (trabajo, sub-trabajos, orden, paralelismo y bloqueos) · Slide Trabajos complejos y novedades |
| **Cotizaciones** | Cotizaciones | Soporte | Flujo Marketplace, paso 3 · Slide Servicios (el proveedor puede requerir información adicional o visita al predio) |
| **Matching de Proveedores** | Matching de proveedores | Núcleo | Flujo Marketplace, paso 2 (publica a proveedores acreditados que coinciden en categoría, zona y disponibilidad) |
| **Gestión de Ejecución** | Orquestación de trabajos | Núcleo | Flujo Marketplace, paso 4 · Slide Contexto (~100 agentes de gestión) · Slide Trabajos complejos y novedades |
| **Red de Proveedores** | Red de proveedores · Reputación | Soporte | Slide Servicios (persona natural o empresa; declara servicios, ciudad y zonas) · Estadísticas: +45.000 proveedores |
| **Confianza de Proveedores** | Confianza de proveedores | Núcleo | Slide Verificación de proveedores (5 pasos, antecedentes, títulos y certificados) · Slide Clientes · Proveedores de Servicios |
| **Evidencia, Calidad y Garantías** | Evidencia, calidad y garantías · Reputación | Soporte | Flujo Marketplace, paso 5 (reseña) · Slide Trabajos complejos (disputa de calidad, garantías) |
| **Procesamiento de Pagos** | Procesamiento de pagos | Genérico | Flujo Marketplace, paso 5 (el pago se procesa en la plataforma y queda retenido hasta finalizar el trabajo) |
| **Plataforma** | Identidad y acceso · Notificaciones | Genérico | Organigrama: equipo Plataforma bajo el CTO, responsable de identidad, acceso y notificaciones para todo el monolito |
| **Entrada de Solicitudes de Partner** | Entrada de solicitudes de partner | Núcleo | Flujo Siniestros y pólizas, paso 2 (el partner crea el trabajo mediante integraciones) · Estadísticas: +30 partners y +25 millones de requests diarios |
| **Reglas y Orquestación de Partner** | Reglas y orquestación de partner | Núcleo | Flujo Siniestros, paso 3 (red permitida, SLA, montos máximos, pasos de aprobación y auditoría) · Slide Clientes («cada partner es un universo») |
| **Elegibilidad para Red de Partner** | Elegibilidad para red de partner | Núcleo | Slide Clientes · Partners B2B2C (el partner puede exigir proveedores específicos ya homologados por la aseguradora) |
| **Evidencia y Auditoría** | Evidencia y auditoría | Soporte | Flujo Siniestros, pasos 4 y 5 (recolección de evidencias; HdA consolida evidencias) |
| **Facturación a Partners** | Facturación a partners | Soporte | Flujo Siniestros, paso 5 (cierra el trabajo y factura al partner según el acuerdo comercial) |

### 5.3 Evidencia de los sistemas externos

| Sistema externo | Evidencia en el enunciado |
|---|---|
| **Sistemas de Partner** | Slide Clientes · Aseguradoras, Bancos y Comercios · Estadísticas: +30 partners activos |
| **Sistema de Antecedentes Judiciales** | Slide Verificación de proveedores (Policía Nacional · antecedentes) |
| **Registro Mercantil** | Slide Verificación de proveedores (Cámara de Comercio · RUES) |
| **Entidades Certificadoras** | Slide Verificación de proveedores (CONTE y entidades certificadoras, respuesta 24-48 h) |
| **Pasarela de Pagos** | Flujo Marketplace, paso 5 (el pago se procesa en la plataforma) |

---

## 6. Anti-patrones detectados y puente hacia el TO-BE

Esta lista es el insumo directo del diseño TO-BE: cada anti-patrón tiene una contrapartida explícita y trazable.

| # | Anti-patrón AS-IS | Evidencia | Qué debe resolver el TO-BE |
|---|---|---|---|
| 1 | Big Ball of Mud: Shared Kernel en malla. 20 de las 34 relaciones comparten modelo, base de datos y transacción. | Despliegues de 3-4 horas, semanas de QA y equipos bloqueados entre sí | Ownership único por contexto y contratos explícitos; ningún Shared Kernel entre contextos TO-BE |
| 2 | La solicitud del partner y el Trabajo son el mismo objeto. La orquestación instancia el Trabajo directamente y le arrastra el identificador externo del partner, sin un concepto propio de Solicitud de Partner que sirva de frontera. | Relación Reglas y Orquestación de Partner ↔ Orquestación de Trabajos en Shared Kernel | Contextos separados con un evento de integración y un identificador de correlación propio |
| 3 | Conformist frente a más de 30 partners sin capa anticorrupción. El modelo externo entra crudo al núcleo. | «Cada partner es un universo»; un adaptador por partner en REST, SOAP y archivos planos | ACL en el borde y un Published Language propio que los partners consuman |
| 4 | Integración por consulta manual humana. Policía, Cámara de Comercio y entidades certificadoras se consultan a mano. | Slide de verificación de proveedores; respuestas de 24-48 h que bloquean el expediente | Integración asíncrona con reintentos y verificación asistida por IA, sin sacrificar la seguridad |
| 5 | Reglas de partner duplicadas en tres piezas. El módulo general, el de siniestros y la orquestación comparten la tabla de acuerdos y se despliegan juntos. | Las tres piezas se consolidan en Reglas y Orquestación de Partner; en el AS-IS estaban unidas por Shared Kernel | Un solo contexto propietario del acuerdo, publicando su lenguaje a los consumidores |
| 6 | La acreditación propia de HdA y la homologación que exige el partner viven en el mismo expediente. | Relación Elegibilidad para Red de Partner ↔ Confianza de Proveedores en Shared Kernel | Separar la confianza propia de HdA de la autorización que concede cada partner |
| 7 | Analítica sobre la base de datos operativa. Riesgo y Fraude y la liquidación consultan el OLTP y exportan a hoja de cálculo. | Cuatro de las 8 relaciones Customer/Supplier del mapa | Modelos de lectura propios del consumidor, alimentados por eventos |
| 8 | Consistencia fuerte en procesos largos. El cierre del trabajo y la liberación del pago comparten transacción. | Relación Orquestación de Trabajos ↔ Procesamiento de Pagos en Shared Kernel | Consistencia eventual, idempotencia y compensación explícita |
| 9 | El proceso depende de intervención humana no modelada. Cerca de 100 agentes destraban el flujo con acceso directo a las tablas. | Contexto Gestión de Ejecución y sus 6 relaciones | Orquestación explícita de novedades y compensaciones; el agente pasa a ser un actor del modelo |
| 10 | Escalabilidad acoplada. La atención de solicitudes de partner puede multiplicarse 4x en 48 horas por un evento climático, pero comparte despliegue con todo lo demás. | Estadísticas de picos; +25 millones de requests diarios | Contratos asíncronos y escalamiento localizado por contexto |
| 11 | Partnership forzado entre equipos. 13 relaciones de coordinación obligatoria, 7 de ellas con el equipo Workflows. | Vista organizacional AS-IS | Un dueño por contexto y contratos versionados que permitan liberar de forma independiente |
| 12 | Capacidades de negocio sin frontera técnica. Reputación es un campo calculado por un disparador sobre la tabla `proveedor`, e Identidad y Notificaciones son un paquete del que hereda todo el monolito. | Tabla puente de la sección 5: tres subdominios sin contexto propio en el AS-IS | Contexto propio y contrato versionado para cada capacidad |

---
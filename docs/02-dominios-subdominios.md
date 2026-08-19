# DOMINIOS Y SUBDOMINIOS

En Domain-Driven Design (DDD), un dominio representa una actividad de negocio, mientras que sus subdominios delimitan capacidades con objetivos, reglas y lenguaje propios. Esta descomposición permite concentrar el diseño en las capacidades que diferencian a Hogar de los Alpes (HdA) y separar aquellas que pueden resolverse mediante componentes de soporte o soluciones estandarizadas.

Para clasificar los subdominios se consideran dos criterios: diferenciación para el negocio y complejidad de sus reglas. Un subdominio se clasifica como **Núcleo** cuando constituye una ventaja competitiva y requiere conocimiento especializado; como **Soporte** cuando es necesario para operar, pero no representa por sí mismo la propuesta de valor principal; y como **Genérico** cuando corresponde a una capacidad estandarizada que puede apoyarse en productos o proveedores especializados.

La identificación se realiza a partir del enunciado del proyecto, el análisis del funcionamiento actual, los escenarios de EventStorming y los modelos incluidos en el repositorio. Como resultado se reconocen cuatro dominios: dos existentes en el AS-IS y dos líneas de negocio previstas en el TO-BE.

| Dominio | Estado | Justificación de la separación |
|---|---|---|
| Servicios para el hogar | AS-IS | Reúne la experiencia B2C de trabajos puntuales: estructuración de la necesidad, búsqueda de oferta, contratación, ejecución y garantía. |
| Atención de siniestros B2B2C | AS-IS | Concentra aproximadamente el 70 % del volumen actual y presenta lenguaje, redes, SLA, límites y reglas diferentes para cada partner. |
| Servicios recurrentes para el hogar | TO-BE | Introduce planes, horarios y continuidad de atención, una dinámica distinta de la contratación de trabajos puntuales. |
| Servicios financieros para proveedores | TO-BE | Convierte el historial operacional verificado en una propuesta de inclusión financiera para proveedores. |

## Dominio 1: Servicios para el hogar - AS-IS

**Vision statement:** conectar hogares con proveedores confiables y coordinar trabajos puntuales para el hogar, desde la estructuración de la necesidad hasta la terminación y la garantía.

Este dominio representa la operación B2C actual. Se inicia cuando una persona expresa una necesidad del hogar y continúa con su diagnóstico, publicación, cotización, asignación, ejecución, pago y seguimiento posterior. El **Trabajo** es la unidad central del flujo y puede descomponerse en subtrabajos y actividades con dependencias, ejecución paralela y novedades.

La operación B2C se mantiene separada de la atención B2B2C porque en el primer caso el hogar selecciona y contrata directamente, mientras que en el segundo la solicitud proviene de un partner y está condicionada por acuerdos, redes y controles externos.

### Subdominios de Servicios para el hogar

| Subdominio | Descripción | Diferenciación | Complejidad | Clasificación |
|---|---|---:|---:|---|
| Captura y diagnóstico de trabajos | Convierte la necesidad expresada por el hogar en un Trabajo estructurado con categoría, urgencia, ubicación y evidencia. | Alta | Alta | Núcleo |
| Orquestación de trabajos | Gestiona el ciclo de vida de trabajos simples y complejos, incluidas dependencias, paralelismo, rediagnóstico, novedades y compensaciones. | Alta | Alta | Núcleo |
| Confianza de proveedores | Verifica personas y empresas y concede acreditaciones por servicio y territorio para proteger la promesa de seguridad de HdA. | Alta | Alta | Núcleo |
| Matching de proveedores | Encuentra y prioriza proveedores elegibles según servicio, ubicación, disponibilidad, acreditación y reputación. | Alta | Alta | Núcleo |
| Red de proveedores | Mantiene perfiles, servicios declarados, cobertura, disponibilidad y técnicos vinculados a empresas. | Media | Media | Soporte |
| Cotizaciones | Gestiona propuestas, visitas, solicitudes de información, selección y cambios de alcance de trabajos y subtrabajos. | Media | Media | Soporte |
| Evidencia, calidad y garantías | Reúne evidencias de ejecución y administra revisiones de calidad, disputas, garantías y seguimiento posventa. | Media | Alta | Soporte |
| Reputación | Consolida calificaciones, cumplimiento y resultados de garantías para apoyar decisiones posteriores. | Media | Media | Soporte |
| Riesgo y fraude | Detecta patrones sospechosos en trabajos, proveedores y evidencias y apoya decisiones auditables. | Media | Alta | Soporte |
| Procesamiento de pagos | Autoriza, retiene, libera, reembolsa y concilia dinero mediante proveedores especializados. | Baja | Media | Genérico |
| Identidad y acceso | Autentica usuarios y sistemas y autoriza el acceso a las capacidades de la plataforma. | Baja | Media | Genérico |
| Notificaciones | Entrega comunicaciones transaccionales mediante canales estandarizados. | Baja | Baja | Genérico |

## Dominio 2: Atención de siniestros B2B2C - AS-IS

**Vision statement:** coordinar solicitudes previamente aprobadas por partners como trabajos auditables, aplicando redes, SLA, límites y reglas particulares sin asumir la propiedad de la póliza ni de la decisión de cobertura.

Este dominio representa la capacidad de HdA para recibir solicitudes B2B2C y gestionar su atención como trabajos sujetos a las condiciones de cada partner. La aseguradora, el banco o el comercio realiza la evaluación previa y autoriza la atención; después, el partner crea o comunica el caso a HdA.

Por esta razón, la póliza, la cobertura y la aprobación inicial se modelan como decisiones externas. HdA no administra estos conceptos: conserva sus referencias, traduce las restricciones recibidas y coordina la prestación del servicio. La frontera independiente se justifica por el volumen actual, el lenguaje especializado y la variabilidad de redes, SLA, límites, evidencias y procesos de facturación entre partners.

### Subdominios de Atención de siniestros B2B2C

| Subdominio | Descripción | Diferenciación | Complejidad | Clasificación |
|---|---|---:|---:|---|
| Entrada de solicitudes de partner | Traduce una solicitud aprobada en un caso de servicio y conserva sus identificadores, restricciones y decisiones externas. | Alta | Alta | Núcleo |
| Reglas y orquestación de partner | Aplica redes permitidas, SLA, límites, controles, pasos de aprobación y requisitos de cumplimiento durante la atención. | Alta | Alta | Núcleo |
| Elegibilidad para red de partner | Determina qué proveedores verificados están habilitados para el caso según la red y la homologación exigidas por el partner. | Alta | Alta | Núcleo |
| Evidencia y auditoría | Consolida la evidencia y la trazabilidad exigidas por el acuerdo para auditar y cerrar el caso. | Media | Alta | Soporte |
| Facturación a partners | Convierte trabajos terminados y evidencia aceptada en ítems facturables según el acuerdo comercial. | Media | Media | Soporte |

## Dominio 3: Servicios recurrentes para el hogar - TO-BE

**Vision statement:** conectar hogares con servicios recurrentes confiables mediante planes, horarios y continuidad de atención.

Este dominio TO-BE extiende la propuesta de valor desde trabajos puntuales hacia relaciones continuas con el cliente. Incluye servicios como limpieza, jardinería y asistencia doméstica, contratados mediante planes cuya ejecución se repite en el tiempo.

La recurrencia exige administrar la vigencia del plan, la programación periódica, la continuidad del proveedor y las novedades de cada ciclo. Se modela como un dominio independiente porque su dinámica de negocio es distinta de la contratación puntual y debe evolucionar sin frenar al resto de la plataforma.

### Subdominios de Servicios recurrentes para el hogar

| Subdominio | Descripción | Diferenciación | Complejidad | Clasificación |
|---|---|---:|---:|---|
| Planeación de servicio recurrente | Programa ciclos de servicio y preserva la continuidad de proveedor, horario y condiciones del plan. | Alta | Alta | Núcleo |
| Gestión de suscripciones | Administra el alta, los cambios, las pausas, la renovación y la cancelación de planes recurrentes. | Media | Media | Soporte |
| Cobro recurrente | Cobra y concilia periódicamente las tarifas del plan mediante capacidades estándar de billing. | Baja | Media | Genérico |

## Dominio 4: Servicios financieros para proveedores - TO-BE

**Vision statement:** mejorar la inclusión financiera del proveedor convirtiendo su historial de trabajo verificado en servicios de crédito y acceso a infraestructura financiera.

Este dominio TO-BE aprovecha información operacional autorizada para ofrecer productos financieros a proveedores que pueden tener acceso limitado al sistema financiero tradicional. Los trabajos terminados, el cumplimiento, la reputación y el comportamiento de pago aportan hechos verificables para construir un perfil de riesgo.

El dominio financiero consume esos hechos sin apropiarse de la operación de servicios. También se mantiene separado del procesamiento de pagos actual: los pagos B2C permiten liquidar un Trabajo, mientras que este dominio crea una nueva propuesta de valor para el proveedor.

### Subdominios de Servicios financieros para proveedores

| Subdominio | Descripción | Diferenciación | Complejidad | Clasificación |
|---|---|---:|---:|---|
| Scoring de proveedores | Estima el riesgo crediticio a partir del historial de trabajos, cumplimiento, reputación y comportamiento financiero autorizado. | Alta | Alta | Núcleo |
| Microcrédito para proveedores | Ofrece y administra productos de financiación adaptados a profesionales independientes de servicios para el hogar. | Alta | Alta | Núcleo |
| Wallet | Proporciona saldo almacenado y movimientos de dinero mediante infraestructura financiera regulada y especializada. | Baja | Alta | Genérico |


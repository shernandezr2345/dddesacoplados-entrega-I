# LENGUAJE UBICUO

El lenguaje ubicuo de Hogar de los Alpes (HdA) reúne los términos utilizados por negocio y tecnología para describir la solicitud, estructuración, asignación, ejecución y cierre de servicios. Las definiciones se aplican de manera consistente en el análisis de dominios, el EventStorming y los diagramas de arquitectura.

El lenguaje no implica que todos los dominios compartan un único modelo. Un mismo término puede adquirir matices diferentes según el contexto; cuando esto ocurre, se explicita la traducción y se evita reutilizar estructuras de datos como si fueran conceptos universales.

El ciclo de vida del **Trabajo** se adopta como flujo representativo del EventStorming. La narración comienza en dos entradas -la necesidad de un hogar en Marketplace B2C y la solicitud previamente aprobada de un partner B2B2C- y converge en la planificación, publicación, cotización, asignación, ejecución, gestión de novedades y cierre. Después del cierre, cada entrada produce consecuencias diferentes: pago y calificación en Marketplace, o consolidación de evidencias y facturación al partner en B2B2C.

## Glosario canónico

| Término | Definición canónica |
|---|---|
| Necesidad del hogar | Situación expresada por una persona y que todavía no ha sido estructurada como un Trabajo. Puede incluir texto, imágenes, ubicación y nivel de urgencia. |
| Solicitud B2B2C | Petición enviada por un partner para atender un servicio bajo un acuerdo comercial. Conserva identificadores y restricciones externas. |
| Trabajo | Unidad operacional mediante la cual HdA coordina un servicio. Contiene origen, categoría, urgencia, ubicación, alcance, participantes, evidencias y estado de ejecución. |
| Trabajo B2C | Trabajo originado por una necesidad del hogar y contratado directamente por el cliente. |
| Caso de partner | Representación interna de una solicitud B2B2C aprobada externamente. Vincula el identificador del partner, las restricciones aplicables y el Trabajo utilizado para prestar el servicio. |
| Siniestro | Hecho reportado y evaluado por una aseguradora. No es sinónimo de Trabajo ni es administrado por HdA; puede originar una solicitud B2B2C después de la decisión de cobertura del partner. |
| Subtrabajo | Parte cotizable o asignable de un Trabajo complejo. Tiene alcance, estado y dependencias propios y puede ejecutarse de forma secuencial o paralela. |
| Actividad | Paso operativo dentro de un Trabajo o Subtrabajo. No se asigna ni se cotiza de manera independiente, salvo que se transforme explícitamente en un Subtrabajo. |
| Categoría de servicio | Clasificación de la necesidad que determina capacidades, reglas y proveedores candidatos. Puede cambiar como resultado de un rediagnóstico. |
| Cliente del hogar | Persona que solicita, contrata y acepta un servicio B2C para un predio. |
| Partner B2B2C | Aseguradora, banco, comercio u organización que origina solicitudes y define condiciones mediante un acuerdo con HdA. |
| Proveedor | Persona o empresa que ofrece y ejecuta servicios para el hogar dentro de la red de HdA. |
| Técnico | Persona vinculada a una empresa proveedora y habilitada individualmente para ejecutar determinados servicios. |
| Agente de gestión | Colaborador de HdA que acompaña, coordina o interviene en la ejecución y las novedades de un Trabajo. |
| Verificación | Comprobación de identidad, documentos o datos de una persona o empresa. Produce un resultado verificable, pero no concede por sí sola autorización para prestar un servicio. |
| Acreditación | Autorización otorgada por HdA para que un proveedor preste determinados servicios en territorios definidos, después de satisfacer requisitos internos. |
| Homologación | Autorización adicional exigida por un partner para que un proveedor participe en su red o atienda determinados casos. |
| Elegibilidad | Decisión calculada para un Trabajo o caso específico. Considera servicio, territorio, disponibilidad, verificación, acreditación, homologación, red y demás restricciones vigentes. |
| Reputación | Resultado acumulado de calificaciones, cumplimiento, calidad y garantías de un proveedor. Se utiliza como señal para decisiones posteriores. |
| Calificación | Valoración emitida después de un servicio B2C y utilizada como una de las señales que actualizan la Reputación del proveedor. |
| Cotización | Propuesta versionada que establece alcance, precio, vigencia y condiciones para ejecutar un Trabajo o Subtrabajo. |
| Selección de Cotización | Decisión del cliente de Marketplace mediante la cual elige una propuesta. No equivale a la aprobación que puede exigir un partner B2B2C. |
| Aprobación del partner | Decisión externa mediante la cual un partner acepta una atención, una Cotización o una excepción según sus límites y reglas. HdA conserva el resultado, pero no es propietaria de la decisión. |
| Asignación | Decisión que vincula un proveedor elegible con un Trabajo o Subtrabajo. Puede invalidarse por cambios de alcance, disponibilidad o reglas aplicables. |
| Evidencia | Registro o referencia inmutable que demuestra una condición, avance, novedad o resultado del servicio. El archivo puede residir en almacenamiento externo, pero su identidad y trazabilidad pertenecen al flujo del Trabajo. |
| Novedad | Situación ocurrida durante la atención que puede alterar alcance, categoría, costo, agenda, proveedor, evidencia o aprobación. |
| Rediagnóstico | Reevaluación de la necesidad después de descubrir información nueva. Puede invalidar planificación, cotización, asignación o aprobaciones existentes. |
| Garantía | Compromiso posterior al cierre mediante el cual se revisa y, cuando corresponde, se corrige un problema atribuible al servicio ejecutado. |
| Disputa | Desacuerdo formal sobre alcance, calidad, evidencia, cobro o cumplimiento que requiere una decisión y trazabilidad. |
| Cierre de Trabajo | Confirmación de que la ejecución y las validaciones requeridas terminaron. Sus efectos posteriores dependen del origen B2C o B2B2C. |
| Pago retenido | Fondos autorizados para un Trabajo B2C que permanecen en custodia hasta que se satisfaga la condición de liberación. |
| Cargo facturable | Registro generado para un Trabajo B2B2C cerrado cuya evidencia satisface el acuerdo comercial. Constituye una entrada para facturación, no una factura. |
| Facturación al partner | Consolidación de cargos facturables y emisión de la información comercial requerida por el acuerdo B2B2C. |
| Regla de partner | Condición particular de una relación B2B2C, como red permitida, SLA, límite, evidencia, aprobación o requisito de auditoría. |
| SLA | Compromiso de nivel de servicio acordado con un partner y aplicado a hitos medibles del Caso de partner o del Trabajo. |
| Plan recurrente | Acuerdo que define un servicio periódico, su frecuencia, condiciones y continuidad esperada. |
| Suscripción | Vinculación vigente de un cliente con un Plan recurrente. Puede activarse, modificarse, pausarse, renovarse o cancelarse. |
| Ciclo de servicio | Ocurrencia programada de un servicio dentro de una Suscripción. Puede generar un Trabajo para su ejecución. |
| Scoring de proveedor | Evaluación de riesgo construida con información operacional verificada y datos cuyo uso ha sido autorizado. |
| Microcrédito | Producto de financiación ofrecido a un proveedor de acuerdo con una decisión de riesgo y unas condiciones de pago. |
| Wallet | Capacidad de saldo y movimiento de dinero ofrecida mediante infraestructura financiera regulada. No reemplaza el procesamiento de pagos de los Trabajos. |

## Diferencias que deben preservarse

### Verificación, acreditación, homologación y elegibilidad

Estos términos representan decisiones diferentes y no deben utilizarse como sinónimos:

1. **Verificación:** confirma identidad, documentos o información.
2. **Acreditación:** HdA autoriza servicios y territorios para un proveedor verificado.
3. **Homologación:** un partner autoriza al proveedor para participar en su red.
4. **Elegibilidad:** se determina si el proveedor puede atender un Trabajo concreto en las condiciones actuales.

Por tanto, un proveedor puede estar verificado y acreditado, pero no ser elegible debido a ubicación, disponibilidad, categoría o restricciones del caso. También puede ser elegible para B2C y no estar homologado para un partner determinado.

### Trabajo, caso de partner y siniestro

El **Siniestro** pertenece al lenguaje de la aseguradora. El **Caso de partner** conserva la referencia y las condiciones que recibe HdA. El **Trabajo** coordina la prestación efectiva del servicio. La aprobación de cobertura ocurre fuera de HdA y no debe representarse mediante eventos como `SiniestroAprobadoPorHdA`.

```text
Siniestro evaluado por la aseguradora
    → Solicitud B2B2C aprobada
    → Caso de partner registrado en HdA
    → Trabajo creado y orquestado por HdA
```

### Trabajo, Subtrabajo y Actividad

Un **Trabajo** representa el resultado completo que debe entregarse. Un **Subtrabajo** es una unidad del Trabajo que puede requerir cotización, proveedor o dependencias propias. Una **Actividad** es un paso de ejecución y no debe convertirse automáticamente en una unidad contractual.

## Traducciones entre dominios

| Concepto | Servicios para el hogar | Atención B2B2C | Proveedores | Servicios recurrentes | Servicios financieros |
|---|---|---|---|---|---|
| Trabajo | Servicio solicitado y contratado por el hogar. | Prestación asociada a un Caso de partner. | Oportunidad ejecutable para un proveedor elegible. | Ejecución de un Ciclo de servicio. | Fuente de hechos operacionales verificados. |
| Cliente | Cliente del hogar. | Partner contratante; el habitante puede ser beneficiario sin ser el contratante. | No es el concepto principal. | Titular de la Suscripción. | Proveedor titular del producto financiero. |
| Aprobación | Selección de cotización y aceptación de condiciones por el cliente. | Decisión externa del partner sobre cobertura, límites o excepciones. | Acreditación o aceptación de una oportunidad. | Activación o modificación del plan. | Decisión de riesgo o crédito. |
| Cierre | Aceptación, liberación del pago y habilitación de reseña o garantía. | Evidencia aceptada, sincronización con el partner y habilitación de facturación. | Actualización de cumplimiento y reputación. | Terminación de un ciclo, no de la Suscripción completa. | Incorporación de hechos autorizados al historial de riesgo. |
| Proveedor | Oferente acreditado y elegible para el Trabajo. | Miembro verificado y homologado para la red aplicable. | Persona, empresa o Técnico con capacidades y cobertura. | Proveedor cuya continuidad puede formar parte del plan. | Cliente financiero y sujeto de evaluación de riesgo. |

Cuando un concepto cruza una frontera de dominio, se comparte mediante un contrato explícito y se traduce al modelo receptor. No se comparte la entidad interna completa ni se supone que los estados tienen el mismo significado.

## Vocabulario del ciclo de vida del Trabajo

| Etapa | Marketplace B2C | B2B2C | Lenguaje común de HdA |
|---|---|---|---|
| Entrada | La necesidad del hogar se describe, diagnostica y estructura. | El partner envía una solicitud previamente aprobada con identificadores y restricciones. | `Trabajo de Marketplace creado` o `Trabajo de partner creado`. |
| Planeación | HdA determina el flujo requerido para resolver la necesidad. | HdA determina el flujo y aplica las condiciones del Caso de partner. | `Flujo de Trabajo definido`, `Subtrabajos creados`, `Dependencias registradas`. |
| Elegibilidad | Se exige acreditación para servicio y territorio. | Se exige además homologación o pertenencia a la red del partner. | `Proveedores elegibles encontrados` o `Proveedores elegibles no encontrados`. |
| Publicación y cotización | El cliente compara y selecciona una Cotización. | El partner aprueba la Cotización cuando sus reglas o límites lo requieren. | `Trabajo publicado`, `Cotización presentada`, `Cotización seleccionada` o `Cotización aprobada por partner`. |
| Asignación y pago inicial | El cliente autoriza el pago y los fondos permanecen retenidos. | La asignación sigue las condiciones y la red aplicables al Caso de partner. | `Proveedor asignado`, `Trabajo agendado`; en B2C, `Fondos retenidos`. |
| Ejecución | El proveedor ejecuta el servicio y registra avances y evidencias. | Se ejecuta el mismo Trabajo y se conserva la trazabilidad exigida por el acuerdo. | `Trabajo iniciado`, `Avance reportado`, `Evidencia registrada`. |
| Novedades | Un cambio puede exigir rediagnóstico, recotización, reasignación o compensación. | Además, la Novedad y sus decisiones se sincronizan con el partner. | `Novedad reportada`, `Trabajo rediagnosticado`, `Recotización solicitada`, `Nuevo proveedor asignado`. |
| Cierre | La aceptación libera el pago retenido y habilita la Calificación o una Garantía. | La aceptación de la evidencia habilita el cargo facturable y la Facturación al partner. | `Trabajo cerrado`; luego `Pago liberado` y `Proveedor calificado`, o `Cargo facturable creado`. |

## Convenciones para EventStorming y diagramas

| Elemento | Convención | Ejemplos correctos |
|---|---|---|
| Actor | Nombre singular del rol que toma la decisión. | `Cliente del hogar`, `Partner B2B2C`, `Proveedor`, `Agente de gestión`. |
| Comando | Verbo en infinitivo seguido del objeto de negocio. Expresa intención y puede ser rechazado. | `Estructurar Trabajo`, `Publicar Subtrabajo`, `Seleccionar Cotización`, `Solicitar aprobación de Cotización`. |
| Evento de dominio | Hecho en pasado que ya ocurrió y no se modifica. | `Trabajo Estructurado`, `Cotización Seleccionada`, `Cotización Aprobada por Partner`, `Proveedor Asignado`. |
| Política | Regla expresada como reacción: cuando ocurre un hecho, se intenta un comando. | “Cuando el Trabajo queda listo para asignación, determinar proveedores elegibles”. |
| Modelo de lectura | Nombre de la información necesaria para decidir, sin verbos de acción. | `Proveedores elegibles`, `Estado del Trabajo`, `Cotizaciones vigentes`. |
| Agregado | Frontera de consistencia que protege reglas de negocio y procesa comandos. | `Trabajo`, `Cotización`, `Caso de partner`, `Suscripción`. |
| Sistema externo | Nombre del sistema o autoridad fuera de la propiedad de HdA. | `Sistema del partner`, `Pasarela de pagos`, `Autoridad de verificación`. |
| Hot spot | Pregunta o regla pendiente de validación, no una decisión confirmada. | “¿Quién acepta la evidencia final en cada acuerdo B2B2C?”. |

## Criterios de consistencia

- Se utiliza **Trabajo** para la unidad operacional de HdA y **Siniestro** únicamente para el concepto externo de la aseguradora.
- Se especifica **Cliente del hogar**, **Partner** o **Proveedor** en lugar de utilizar “cliente” sin contexto.
- Los comandos no se redactan como hechos y los eventos no se redactan en presente o futuro.
- Los eventos describen resultados de negocio, no llamadas técnicas como `APIInvocada` o `RegistroInsertado`.
- La aprobación externa de cobertura no se atribuye a HdA.
- Un cambio de categoría, alcance, costo o proveedor se representa como una Novedad y puede producir rediagnóstico, recotización o reasignación.
- El cierre B2C y el cierre B2B2C comparten la terminación operacional, pero producen efectos posteriores diferentes.
- El scoring financiero consume únicamente hechos verificados y datos autorizados; no modifica el Trabajo original.
- Los términos en inglés se conservan solo cuando corresponden al lenguaje aceptado del proyecto, como `partner`, `wallet`, `scoring`, `EventStorming`, `AS-IS` y `TO-BE`.

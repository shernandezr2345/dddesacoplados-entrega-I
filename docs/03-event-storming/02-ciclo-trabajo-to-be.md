# EventStorming Big Picture TO-BE

## Propósito y alcance

El Big Picture TO-BE conserva el **Trabajo** como hilo narrativo, pero explicita un lenguaje más preciso, las decisiones de negocio y las diferencias entre Marketplace B2C y B2B2C. La vista presenta tres recorridos relacionados:

1. Habilitación de la oferta de proveedores.
2. Entradas Marketplace B2C y B2B2C.
3. Ciclo común del Trabajo y consecuencias posteriores por canal.

El tablero describe comportamiento de negocio esperado. No define una correspondencia uno a uno entre elementos del EventStorming, *bounded contexts* y microservicios.

## Tablero

![EventStorming Big Picture TO-BE: ciclo de vida objetivo del Trabajo](eventstorming-to-be.png)

**Fuente:** [Hogar de los Alpes — EventStorming Big Picture TO-BE](https://miro.com/app/board/uXjVHx35FNE=/?share_link_id=417901581664)

## Lectura del flujo

### Habilitación de proveedores

La oferta se prepara en un flujo paralelo al ciclo del Trabajo. Un proveedor se verifica y HdA puede acreditarlo para determinados servicios y territorios. Cuando un partner exige una red propia, el proveedor requiere además homologación. La **Elegibilidad** se calcula después para cada Trabajo concreto considerando categoría, zona, disponibilidad, acreditación y, cuando aplique, homologación y reglas del partner.

Esta secuencia preserva cuatro decisiones distintas:

1. **Verificación:** confirma identidad, documentos o credenciales.
2. **Acreditación:** HdA autoriza servicios y territorios.
3. **Homologación:** el partner habilita al proveedor dentro de su red.
4. **Elegibilidad:** determina si puede atender un Trabajo específico.

### Entrada Marketplace B2C

El cliente del hogar presenta una necesidad. HdA la diagnostica y crea el Trabajo de Marketplace. La planificación define subtrabajos, actividades, orden, paralelismo y bloqueos antes de buscar oferta elegible.

### Entradas B2B2C

La aseguradora evalúa y aprueba externamente la atención antes de enviar la solicitud. HdA registra un **Caso de partner**, traduce los identificadores y restricciones recibidos y crea el Trabajo utilizado para prestar el servicio.

El tablero también representa solicitudes de bancos o comercios para instalaciones. Aunque el origen externo cambia, ambas variantes convergen en un Caso de partner y en un Trabajo de HdA. Las reglas del acuerdo determinan red, SLA, límites, aprobaciones y evidencias.

### Ciclo común del Trabajo

Después de la entrada, el flujo común comprende:

1. Definir el flujo del Trabajo.
2. Determinar proveedores elegibles y publicar el Trabajo.
3. Recibir la Cotización y la información adicional o visita necesaria.
4. Seleccionar la Cotización en Marketplace o solicitar aprobación al partner en B2B2C.
5. Asignar al proveedor elegible y agendar el Trabajo.
6. Autorizar y retener fondos en Marketplace antes de iniciar.
7. Ejecutar el Trabajo y registrar avances y evidencias.
8. Reportar y gestionar novedades mediante rediagnóstico, recotización, reasignación o sincronización con el partner.
9. Validar evidencias y cerrar el Trabajo.

### Consecuencias posteriores al cierre

- **Marketplace B2C:** cuando el Trabajo cumple la condición de aceptación, se liberan los fondos retenidos y se habilita la calificación del proveedor.
- **B2B2C:** HdA valida y consolida la evidencia exigida. El cierre genera un **Cargo facturable**, que posteriormente se incorpora a la facturación del partner según el acuerdo comercial.

## Decisiones semánticas reflejadas

- El **Siniestro** pertenece al lenguaje de la aseguradora; HdA registra un **Caso de partner** y coordina un **Trabajo**.
- La aprobación inicial de cobertura pertenece al partner y no se representa como una decisión tomada por HdA.
- La selección de Cotización del cliente de Marketplace se distingue de la aprobación que puede exigir un partner.
- El pago retenido aplica al recorrido Marketplace y se libera después de la aceptación; no se confunde con la facturación B2B2C.
- Una Novedad puede invalidar planificación, Cotización, Asignación, agenda o aprobaciones y activar una decisión compensatoria.
- El Cargo facturable es una entrada para facturación y no equivale todavía a una factura.
- Los servicios recurrentes y financieros se reconocen como dominios diferentes y no se incorporan artificialmente al ciclo del Trabajo puntual.

## Relación con el resto de la entrega

El [lenguaje ubicuo](00-lenguaje-ubicuo.md) define los términos utilizados en el tablero y la sección de [dominios y subdominios](../02-dominios-subdominios.md) explica las capacidades de negocio descubiertas. Los límites de los *bounded contexts* se analizan posteriormente; no se deducen de manera automática a partir de cada comando o evento.

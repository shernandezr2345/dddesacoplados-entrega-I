# CONTEXTO Y ALCANCE

## Contexto del proyecto

Hogar de los Alpes (HdA) es una compañía colombiana fundada en Bogotá en 2015 cuyo propósito es conectar hogares que necesitan resolver problemas con proveedores confiables de servicios como plomería, electricidad, carpintería y pintura. Opera en Bogotá, Medellín, Cali, Cartagena y Barranquilla mediante dos canales principales:

- **Marketplace B2C:** una persona describe una necesidad, recibe apoyo para diagnosticarla y contrata directamente el servicio.
- **B2B2C:** aseguradoras, bancos y comercios envían solicitudes de atención mediante integraciones y aplican condiciones particulares de red, SLA, límites, aprobaciones, evidencias y auditoría.

El canal B2B2C origina aproximadamente el 70 % de los trabajos y el Marketplace, el 30 %. La operación actual supera los 12.000 trabajos diarios, cuenta con más de 45.000 proveedores registrados y se integra con más de 30 partners. La estrategia de expansión hacia México, Brasil y Argentina proyecta alrededor de 36.000 trabajos diarios y más de 100.000 proveedores.

## Problema que motiva la transformación

La operación está soportada por un monolito construido desde 2016. Según el enunciado, los equipos comparten la fuente de código y los ciclos de QA y despliegue, lo cual genera despliegues de tres a cuatro horas, semanas de validación y bloqueos entre equipos. La expansión regional, los picos de demanda y la incorporación de servicios recurrentes y productos financieros aumentarán estas tensiones.

El enunciado no incluye el código, el esquema de datos ni los contratos internos del monolito. Por ello, los modelos AS-IS de la entrega son una **reconstrucción lógica** basada en los procesos, el organigrama y las integraciones descritas; no pretenden documentar módulos físicos que hayan sido comprobados en el sistema real.

## Objetivo del proyecto y de la Entrega 1

El objetivo general del proyecto es diseñar e implementar una arquitectura que soporte la migración del monolito hacia un sistema reactivo distribuido basado en eventos. La Entrega 1 no ejecuta esa migración: establece las bases estratégicas de dominio necesarias para decidir límites semánticos, responsabilidades y relaciones.

La entrega comprende:

1. Identificación y clasificación de dominios y subdominios.
2. Definición de sus *vision statements*.
3. Construcción del lenguaje ubicuo.
4. EventStorming Big Picture AS-IS y TO-BE.
5. Identificación de *bounded contexts* AS-IS y TO-BE.
6. Relaciones entre contextos y mecanismos de desacoplamiento.
7. Relación entre los contextos y los equipos responsables.

No forman parte de esta entrega la selección detallada de infraestructura, brokers o bases de datos; el diseño completo de agregados; la implementación de pruebas de concepto; ni la definición de microservicios uno a uno.

## Decisión de alcance del EventStorming

El análisis adopta el **ciclo de vida del Trabajo** como flujo representativo y muestra sus entradas Marketplace B2C y B2B2C.

La narración comienza de dos maneras:

- En Marketplace B2C, el cliente del hogar describe una necesidad que HdA diagnostica y estructura.
- En B2B2C, un partner envía una solicitud previamente aprobada con identificadores y restricciones externas. La aseguradora conserva la propiedad de la póliza, la cobertura y la aprobación inicial; HdA coordina la prestación del servicio.

Ambas entradas convergen en la planificación, publicación, cotización, asignación, ejecución, gestión de novedades y cierre del Trabajo. Después del cierre, cada canal produce consecuencias diferentes: liberación del pago y calificación en Marketplace, o consolidación de evidencias y facturación al partner en B2B2C.

Esta decisión permite analizar un flujo transversal a las capacidades principales sin reducir la historia al Marketplace ni atribuir a HdA decisiones que pertenecen a los sistemas externos de los partners.

## Criterio de trazabilidad

Para mantener una narrativa verificable, la documentación distingue entre:

- **Hechos:** información explícita del enunciado del proyecto.
- **Interpretaciones AS-IS:** reconstrucciones del equipo sobre la operación actual.
- **Decisiones TO-BE:** propuestas de diseño que deben validarse con expertos de dominio.
- **Hot spots:** preguntas o reglas todavía no confirmadas.

La audiencia principal de esta documentación está compuesta por el equipo de ingeniería, arquitectos, expertos de dominio y responsables de las capacidades de negocio involucradas en la transformación.

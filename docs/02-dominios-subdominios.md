# DOMINIOS Y SUBDOMINIOS

El análisis de dominios y subdominios de Hogar de los Alpes (HdA) parte de sus capacidades reales de negocio. La compañía conecta hogares y organizaciones que requieren trabajos con proveedores de servicios profesionales, operando tanto mediante un marketplace B2C como mediante integraciones B2B2C con aseguradoras, bancos y comercios.

Actualmente, HdA gestiona más de 12.000 trabajos diarios, cuenta con aproximadamente 45.000 proveedores registrados y más de 30 partners B2B2C. La expansión hacia México, Brasil y Argentina proyecta alrededor de 36.000 trabajos diarios y más de 100.000 proveedores registrados.

El principal reto consiste en identificar las capacidades de negocio que deben evolucionar de manera independiente. Por esta razón, la identificación de dominios y subdominios utiliza como insumos los procesos del negocio, los actores, la estructura organizacional y la estrategia futura de HdA.

## Dominio 1: Servicios para el hogar — AS-IS

### Vision Statement

> Conectar las necesidades de hogares, aseguradoras, bancos y comercios con proveedores de servicios confiables, gestionando el ciclo de vida de los trabajos desde su creación hasta su ejecución y cierre.

Este dominio representa la actividad principal de HdA. Su unidad de negocio fundamental es el **Trabajo**, entendido como una actividad específica que un tercero necesita resolver.

Un trabajo puede ser sencillo o estar compuesto por múltiples sub-trabajos, categorías, proveedores, cotizaciones y tiempos de ejecución.

La gestión de trabajos es común a los dos principales modelos de negocio:

* **Marketplace B2C:** los hogares solicitan directamente los servicios.
* **B2B2C:** aseguradoras, bancos y comercios crean trabajos mediante integraciones.

### Subdominios — Servicios para el hogar

| Subdominio                        | Descripción                                                                                                                                             | Diferenciación | Complejidad | Clasificación |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------: | ----------: | ------------- |
| **Gestión de Trabajos**           | Gestiona el ciclo de vida del Trabajo desde su creación hasta su ejecución y cierre, incluyendo sub-trabajos, actividades, dependencias y novedades.    |           Alta |        Alta | **Núcleo**    |
| **Gestión de Proveedores**        | Administra la red de profesionales y empresas, sus servicios, cobertura, disponibilidad y reputación.                                                   |           Alta |        Alta | **Núcleo**    |
| **Acreditación y Elegibilidad**   | Gestiona la verificación, acreditación y homologación de proveedores y determina para qué trabajos pueden ser elegibles.                                |           Alta |        Alta | **Núcleo**    |
| **Marketplace**                   | Conecta la demanda de los hogares con la oferta de proveedores mediante la solicitud y contratación de trabajos.                                        |           Alta |        Alta | **Núcleo**    |
| **Cotizaciones**                  | Gestiona la solicitud, recepción, evaluación y selección de cotizaciones asociadas a un Trabajo.                                                        |           Alta |        Alta | **Núcleo**    |
| **Asignación**                    | Determina los proveedores candidatos y la asignación de trabajos considerando categoría, zona, disponibilidad, acreditación y reglas aplicables.        |           Alta |        Alta | **Núcleo**    |
| **Reglas de Partner / B2B2C**     | Gestiona las particularidades de aseguradoras, bancos y comercios: SLA, aprobaciones, montos, proveedores homologados, compliance y flujos específicos. |           Alta |        Alta | **Núcleo**    |
| **Gestión de Ejecución**          | Coordina la ejecución y seguimiento de los trabajos, incluyendo actividades, proveedores involucrados y cumplimiento de las condiciones acordadas.      |           Alta |        Alta | **Núcleo**    |
| **Calidad, Garantías y Disputas** | Gestiona problemas de calidad, reclamaciones, garantías, disputas y compensaciones derivados de los trabajos ejecutados.                                |          Media |       Media | **Soporte**   |
| **Pagos y Liquidaciones**         | Gestiona los pagos asociados a los trabajos, liquidaciones y procesos de facturación con participantes y partners.                                      |     Baja/Media |       Media | **Soporte**   |
| **Datos e IA**                    | Proporciona capacidades de datos e inteligencia artificial para diagnóstico, fraude, priorización, automatización y soporte a otros procesos.           |          Media |        Alta | **Soporte**   |

La información de estos subdominios corresponde a la definición presentada en el documento de la Entrega I.

---

## Dominio 2: Gestión de Siniestros y Pólizas — AS-IS

### Vision Statement

> Gestionar el ciclo de atención de siniestros y pólizas provenientes de aseguradoras, coordinando su evaluación, aprobación y transformación en trabajos que puedan ser atendidos por la red de proveedores de Hogar de los Alpes.

Este dominio representa la capacidad de HdA para gestionar los procesos asociados a siniestros provenientes principalmente de aseguradoras, desde la recepción y evaluación del caso hasta su aprobación y posterior atención mediante un Trabajo.

A diferencia del flujo de Marketplace, donde el hogar solicita directamente un servicio, en este modelo el proceso puede comenzar con un siniestro reportado por el asegurado ante su aseguradora. La aseguradora evalúa el caso y, cuando corresponde, aprueba la atención y solicita a HdA la gestión del servicio.

Este flujo forma parte del modelo **B2B2C**.

### Subdominios — Gestión de Siniestros y Pólizas

| Subdominio                                 | Descripción                                                                                                                                                 | Diferenciación | Complejidad | Clasificación |
| ------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------: | ----------: | ------------- |
| **Gestión de Siniestros**                  | Gestiona el ciclo de vida del siniestro desde su recepción y evaluación hasta su aprobación y derivación a la atención correspondiente.                     |           Alta |        Alta | **Núcleo**    |
| **Gestión de Pólizas y Coberturas**        | Determina las condiciones de cobertura aplicables al siniestro y las restricciones que deben considerarse antes de autorizar su atención.                   |           Alta |        Alta | **Núcleo**    |
| **Evaluación y Aprobación de Siniestros**  | Gestiona la evaluación previa realizada por la aseguradora y las decisiones de aprobación necesarias para iniciar la atención del caso.                     |           Alta |        Alta | **Núcleo**    |
| **Orquestación de Atención del Siniestro** | Coordina la transformación del siniestro aprobado en un Trabajo y su posterior atención, aplicando las condiciones particulares del partner.                |           Alta |        Alta | **Núcleo**    |
| **Reglas de Partner para Siniestros**      | Aplica las reglas específicas de cada aseguradora, incluyendo proveedores permitidos, SLA, montos máximos, aprobaciones y requisitos de auditoría.          |           Alta |        Alta | **Núcleo**    |
| **Gestión de Proveedores Homologados**     | Determina qué proveedores pueden participar en la atención de determinados siniestros según las condiciones y homologaciones exigidas por cada aseguradora. |           Alta |        Alta | **Núcleo**    |
| **Gestión de Evidencias**                  | Gestiona la recopilación y consolidación de evidencias requeridas durante la atención del siniestro para soportar la ejecución, auditoría y cierre.         |     Media/Alta |  Media/Alta | **Soporte**   |
| **Cierre y Facturación de Siniestros**     | Consolida las evidencias, formaliza el cierre del Trabajo y genera la información necesaria para facturar a la aseguradora según el acuerdo comercial.      |          Media |       Media | **Soporte**   |

---

## Dominio 3: Servicios recurrentes del hogar — TO-BE

### Vision Statement

> Proporcionar servicios recurrentes para el hogar mediante modelos de suscripción que permitan contratar, programar y gestionar servicios periódicos de forma confiable y flexible.

Este dominio representa una nueva línea de negocio estratégica para HdA. A diferencia del modelo actual de trabajos puntuales, los servicios recurrentes buscan establecer una relación continua con el cliente mediante la contratación de servicios bajo un modelo de suscripción.

La estrategia contempla servicios como:

* Empleadas domésticas
* Limpieza
* Jardinería

Estos servicios requieren gestionar una relación recurrente con el cliente, donde la contratación no se limita a un único Trabajo, sino que implica la programación y ejecución periódica del servicio.

Por esta razón, este dominio se plantea como **TO-BE**, ya que corresponde a una capacidad que HdA busca incorporar como parte de su evolución y expansión del negocio.

### Subdominios — Servicios recurrentes del hogar

| Subdominio                          | Descripción                                                                                               | Diferenciación | Complejidad | Clasificación |
| ----------------------------------- | --------------------------------------------------------------------------------------------------------- | -------------: | ----------: | ------------- |
| **Suscripciones**                   | Gestiona la contratación, configuración, renovación y cancelación de servicios recurrentes para el hogar. |           Alta |        Alta | **Núcleo**    |
| **Planificación recurrente**        | Coordina la programación de las actividades y servicios periódicos contratados mediante una suscripción.  |           Alta |        Alta | **Núcleo**    |
| **Gestión de servicios periódicos** | Gestiona la ejecución repetitiva de servicios como limpieza, jardinería o asistencia doméstica.           |           Alta |        Alta | **Núcleo**    |

---

## Dominio 4: Servicios financieros para proveedores — TO-BE

### Vision Statement

> Proporcionar servicios financieros a los proveedores de Hogar de los Alpes mediante wallets, pagos y mecanismos de scoring que permitan facilitar el acceso a micropréstamos utilizando su historial operacional.

Este dominio representa una nueva línea de negocio estratégica orientada a los proveedores de servicios.

HdA busca aprovechar la información generada durante la operación de los trabajos para ofrecer productos financieros a profesionales que actualmente pueden no contar con acceso suficiente al sistema financiero tradicional.

La estrategia contempla capacidades como:

* Wallets para proveedores
* Servicios de pago
* Scoring financiero
* Micropréstamos

Una característica importante de este dominio es que el historial de trabajos del proveedor puede convertirse en una fuente de información para evaluar su comportamiento y capacidad crediticia.

Por esta razón, los servicios financieros para proveedores se consideran un dominio **TO-BE** independiente del procesamiento de pagos del negocio actual.

Aunque ambos manejan transacciones financieras, tienen objetivos de negocio diferentes:

* Los **pagos actuales** permiten completar y liquidar los trabajos.
* Los **servicios financieros TO-BE** buscan crear una nueva propuesta de valor financiera para los proveedores.

### Subdominios — Servicios financieros para proveedores

| Subdominio                        | Descripción                                                                                                                     | Diferenciación | Complejidad | Clasificación |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | -------------: | ----------: | ------------- |
| **Wallet de Proveedores**         | Permite gestionar fondos y operaciones financieras asociadas a los proveedores de servicios.                                    |           Alta |        Alta | **Núcleo**    |
| **Servicios financieros y pagos** | Gestiona servicios financieros dirigidos a los proveedores, aprovechando la relación existente con la plataforma.               |           Alta |        Alta | **Núcleo**    |
| **Scoring y Micropréstamos**      | Utiliza el historial operacional de los proveedores para construir mecanismos de scoring y facilitar el acceso a microcréditos. |           Alta |        Alta | **Núcleo**    |

---

## Resumen de dominios

|  # | Dominio                                    | Estado | Enfoque                                                                         |
| -: | ------------------------------------------ | ------ | ------------------------------------------------------------------------------- |
|  1 | **Servicios para el hogar**                | AS-IS  | Operación principal de trabajos B2C y B2B2C                                     |
|  2 | **Gestión de Siniestros y Pólizas**        | AS-IS  | Gestión de siniestros provenientes principalmente de aseguradoras               |
|  3 | **Servicios recurrentes del hogar**        | TO-BE  | Nuevos servicios bajo modelos de suscripción                                    |
|  4 | **Servicios financieros para proveedores** | TO-BE  | Nuevos servicios financieros basados en el historial operacional de proveedores |


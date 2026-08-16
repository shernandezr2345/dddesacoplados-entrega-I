# CONTEXTO Y ALCANCE 
 
Hogar de los Alpes (HdA) es una compañía colombiana fundada en Bogotá en 2015 cuyo propósito es conectar hogares que necesitan resolver problemas con profesionales de confianza para servicios como plomería, electricidad, carpintería y pintura. Actualmente opera en Bogotá, Medellín, Cali, Cartagena y Barranquilla, y cuenta con un modelo de negocio que combina un marketplace B2C con operaciones B2B2C provenientes principalmente de aseguradoras, bancos y comercios. 

La organización enfrenta un proceso de transformación debido a su crecimiento, la adquisición por parte de Seguros de los Alpes y la estrategia de expansión hacia México, Brasil y Argentina. Esta expansión implica nuevos países, monedas, regulaciones, zonas horarias y partners, además de un crecimiento proyectado hasta aproximadamente 36.000 trabajos diarios y más de 100.000 proveedores registrados. 

Desde el punto de vista tecnológico, la operación actual se encuentra soportada sobre un monolito construido desde 2016. El crecimiento ha incrementado la dificultad para desarrollar nuevas capacidades: existen despliegues de 3 a 4 horas, semanas de QA y bloqueos entre equipos debido a que comparten una misma base de código. La compañía cuenta actualmente con aproximadamente 50 personas en ingeniería y espera duplicar este equipo durante los próximos 18 meses. 



# Preguntas para entendimiento:

## ¿Qué es Hogar de los Alpes?

**Hogar de los Alpes (HdA)** es una compañía colombiana fundada en Bogotá en 2015 cuyo propósito es conectar hogares que necesitan resolver problemas con profesionales de confianza, entre ellos plomeros, electricistas, carpinteros y pintores.

Actualmente opera en cinco ciudades colombianas:

* Bogotá
* Medellín
* Cali
* Cartagena
* Barranquilla

---

## ¿Cómo genera negocio actualmente Hogar de los Alpes?

El caso presenta dos grandes fuentes de trabajos:

### B2C — Marketplace

Personas que utilizan la aplicación o página web para solicitar un trabajo para su hogar. Un asistente conversacional ayuda a diagnosticar el problema y crear el trabajo con información como:

* Categoría
* Urgencia
* Ubicación
* Evidencia

### B2B2C

Aseguradoras, bancos y comercios crean trabajos mediante integraciones con HdA.

En este modelo, el propietario del inmueble no necesariamente es usuario de HdA, porque la relación comercial puede ser con la aseguradora, banco o comercio. Cada partner tiene sus propias reglas, pasos y requisitos de compliance.

> **70 % de los trabajos provienen de B2B2C y 30 % del marketplace.**

---

## ¿Cuál es el propósito del negocio?

El propósito de HdA es conectar hogares que necesitan resolver un problema con profesionales de confianza, garantizando que los proveedores estén verificados y calificados.

En el marketplace B2C, el cliente busca principalmente:

* Confianza en el proveedor
* Precios justos
* Seguridad
* Garantía sobre el trabajo realizado

---

## ¿Cuál es la magnitud actual de la operación?

| Indicador                                             |               Magnitud |
| ----------------------------------------------------- | ---------------------: |
| Trabajos completados                                  |        +12.000 diarios |
| Proveedores registrados                               |                +45.000 |
| Proveedores con acreditación completa para siniestros |                  6.500 |
| Partners B2B2C                                        |                    +30 |
| Requests diarios                                      |           +25 millones |
| Cobertura                                             | 5 ciudades colombianas |
| Participación B2B2C                                   |                   70 % |
| Participación Marketplace                             |                   30 % |

El problema es que el modelo actual debe soportar una operación con alto volumen, múltiples actores, múltiples reglas y comportamiento variable.

---

## ¿Cuál es el principal problema tecnológico actual?

La operación completa corre actualmente sobre un **monolito construido desde 2016**.

El crecimiento ha generado dificultades para desarrollar nuevas capacidades:

* Despliegues de 3–4 horas
* Semanas de QA
* Equipos bloqueados entre sí
* Dificultad para evolucionar capacidades de manera independiente

Además, la organización ya tiene equipos alrededor de capacidades como:

* Proveedores de Servicio
* Marketplace
* Siniestros
* Gestión de Trabajos

La estructura organizacional y los procesos del negocio ya muestran posibles fronteras de responsabilidad que deben ser analizadas.

---

## ¿Por qué es necesario transformar la arquitectura?

La transformación es necesaria porque HdA debe acompañar una expansión importante del negocio.

La estrategia contempla expansión hacia:

* México
* Brasil
* Argentina

Además, se planea entrar en nuevos modelos de negocio como:

* Servicios recurrentes bajo suscripción
* Empleadas domésticas
* Limpieza
* Otros servicios para el hogar

Por lo tanto, la arquitectura debe permitir que estas nuevas capacidades evolucionen sin frenar al resto de la plataforma.

---

## ¿Cuál es el objetivo arquitectónico del proyecto?

El objetivo explícito del proyecto es diseñar e implementar una arquitectura que soporte la migración del sistema monolítico hacia un **sistema reactivo distribuido basado en eventos**, capaz de acompañar la expansión regional y los nuevos modelos de negocio.

El objetivo está relacionado con la evolución del dominio y de la arquitectura, utilizando eventos y límites de responsabilidad que permitan una evolución independiente.

---

## ¿Qué se busca lograr específicamente en la Entrega I?

La Entrega I establece las bases de la arquitectura de dominio.

Se busca documentar:

1. Dominios
2. Subdominios
3. Vision Statements
4. Lenguaje ubicuo
5. Flujos del lenguaje ubicuo
6. Contextos acotados
7. Relaciones entre contextos
8. Mecanismos de desacoplamiento
9. Relación entre equipos

Todo esto debe analizarse tanto para el **AS-IS** como para el **TO-BE**.

---

## ¿Cuál es el alcance funcional de nuestro análisis?

El análisis de esta entrega comprende las principales capacidades de negocio de Hogar de los Alpes involucradas en:

* Generación de trabajos
* Gestión de trabajos
* Ejecución de trabajos
* Relación con proveedores
* Relación con clientes
* Relación con partners B2B2C
* Capacidades que soportan estas operaciones

Para el análisis detallado del lenguaje ubicuo y EventStorming se seleccionará un flujo representativo del negocio, mientras que el análisis de dominios, subdominios y contextos acotados considerará la organización como un todo, tal como exige la guía de la entrega.

---

## ¿Qué flujo utilizaremos como foco del EventStorming?

Para el análisis detallado del lenguaje ubicuo y EventStorming se propone utilizar como flujo principal:

> **Siniestros y Pólizas B2B2C**

Este flujo resulta representativo debido a la importancia que tiene el modelo B2B2C dentro de la operación de Hogar de los Alpes, que actualmente representa aproximadamente el **70 % de los trabajos**.

---

## ¿Qué cubre el AS-IS?

El **AS-IS** representa cómo funciona actualmente el negocio y cómo se encuentran organizadas sus responsabilidades antes de la transformación arquitectónica.

El análisis AS-IS permitirá identificar:

* Actores actuales
* Eventos del negocio
* Comandos
* Procesos
* Sistemas existentes
* Sistemas externos
* Reglas de negocio
* Dependencias entre capacidades
* Responsabilidades actuales
* Lenguaje utilizado por los participantes

---

## ¿Qué representa el TO-BE?

El **TO-BE** representa la propuesta de organización futura del dominio y de sus contextos, considerando la migración desde el monolito hacia una arquitectura distribuida basada en eventos.

El análisis TO-BE permitirá establecer:

* Nuevos límites de responsabilidad
* Contextos acotados
* Relaciones entre contextos
* Mecanismos de desacoplamiento
* Eventos de integración
* Responsabilidades de los equipos
* Evolución independiente de las capacidades

---

## ¿Qué queda fuera del alcance de esta entrega?

En esta entrega no se pretende definir todavía la implementación detallada de la arquitectura distribuida, tecnologías específicas de infraestructura, configuración de brokers, bases de datos, despliegues, observabilidad ni los POC técnicos.

El foco está en establecer el **modelo de dominio y sus límites**, mediante:

* Dominios
* Subdominios
* Lenguaje ubicuo
* EventStorming
* Contextos acotados
* Relaciones entre contextos

Esto se realizará para los escenarios **AS-IS y TO-BE**.

---

## ¿Quién es la audiencia de esta documentación?

La audiencia principal es:

* Equipo de ingeniería
* Arquitectos de software
* Expertos de dominio
* Equipos responsables de las capacidades de negocio
* Stakeholders involucrados en la transformación arquitectónica

La documentación busca servir como referencia común para comprender el dominio, establecer un lenguaje ubicuo compartido y definir los límites de responsabilidad que orientarán la evolución arquitectónica de Hogar de los Alpes.

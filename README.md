# Entrega 1 - Diseño y arquitectura de dominio

Proyecto del equipo **DDDesacoplados** para el curso **Diseño y construcción de soluciones no monolíticas**. El caso de estudio es **Hogar de los Alpes (HdA)** y esta entrega documenta su análisis estratégico de dominio mediante Domain-Driven Design (DDD).

## Integrantes

- Nicolás Samuel Páez Tarazona
- Nicolás Giovanny Caicedo Ramírez
- Carlos Andrés Portillo Bucheli
- Steven Hernández Ríos

## Documento principal

El documento consolidado de la entrega está en:

- [`Entrega 1 - DDDesacoplados - Integrado con contextos realineados.pdf`](Entrega%201%20-%20DDDesacoplados%20-%20Integrado%20con%20contextos%20realineados.pdf)

Este PDF contiene la narrativa completa, las tablas, el lenguaje ubicuo, los EventStorming AS-IS y TO-BE, los contextos acotados, los Context Maps y las conclusiones.

## Estructura del proyecto

```text
.
├── README.md
├── Entrega 1 - DDDesacoplados - Integrado con contextos realineados.pdf
├── docs/
│   ├── 01-contexto-alcance.md
│   ├── 02-dominios-subdominios.md
│   ├── 03-event-storming/
│   │   ├── 00-lenguaje-ubicuo.md
│   │   ├── 01-servicios-para-el-hogar-as-is.md
│   │   ├── 02-ciclo-trabajo-to-be.md
│   │   ├── eventstorming-as-is.png
│   │   └── eventstorming-to-be.png
│   ├── 04-bounded-contexts.md
│   ├── 05-context-map.md
│   ├── context-map-as-is_ContextMap.png
│   ├── context-map-to-be_ContextMap.png
│   ├── team-map-as-is_ContextMap.png
│   └── team-map-to-be_ContextMap.png
└── models/
    ├── 01-domain-model.cml
    ├── 02-context-map-as-is.cml
    ├── 021-team-map-as-is.cml
    ├── 03-context-map-to-be.cml
    └── 031-team-map-to-be.cml
```

## Dónde encontrar cada elemento de evaluación

| Elemento | Documento explicativo | Artefacto verificable |
|---|---|---|
| Contexto, problema y alcance | [`docs/01-contexto-alcance.md`](docs/01-contexto-alcance.md) | PDF, sección **Contexto y alcance** |
| Dominios y subdominios | [`docs/02-dominios-subdominios.md`](docs/02-dominios-subdominios.md) | [`models/01-domain-model.cml`](models/01-domain-model.cml) |
| Lenguaje ubicuo | [`docs/03-event-storming/00-lenguaje-ubicuo.md`](docs/03-event-storming/00-lenguaje-ubicuo.md) | PDF, páginas **10 a 14**. Allí se encuentran el glosario, las traducciones entre dominios y las convenciones visuales |
| EventStorming Big Picture AS-IS | [`docs/03-event-storming/01-servicios-para-el-hogar-as-is.md`](docs/03-event-storming/01-servicios-para-el-hogar-as-is.md) | [`docs/03-event-storming/eventstorming-as-is.png`](docs/03-event-storming/eventstorming-as-is.png) |
| EventStorming Big Picture TO-BE | [`docs/03-event-storming/02-ciclo-trabajo-to-be.md`](docs/03-event-storming/02-ciclo-trabajo-to-be.md) | [`docs/03-event-storming/eventstorming-to-be.png`](docs/03-event-storming/eventstorming-to-be.png) |
| Contextos acotados AS-IS, relaciones, equipos y anti-patrones | [`docs/04-bounded-contexts.md`](docs/04-bounded-contexts.md) | [`models/02-context-map-as-is.cml`](models/02-context-map-as-is.cml), [`models/021-team-map-as-is.cml`](models/021-team-map-as-is.cml) y sus PNG en `docs/` |
| Contextos acotados TO-BE, mecanismos de integración y trazabilidad | [`docs/05-context-map.md`](docs/05-context-map.md) | [`models/03-context-map-to-be.cml`](models/03-context-map-to-be.cml), [`models/031-team-map-to-be.cml`](models/031-team-map-to-be.cml) y sus PNG en `docs/` |
| Entrega integral | PDF ubicado en la raíz | Contiene la narrativa y todos los diagramas en un único archivo |

## Alcance del EventStorming

Los dos tableros utilizan el **ciclo de vida del Trabajo** como flujo representativo y muestran sus dos entradas: **Marketplace B2C** y **B2B2C**. El AS-IS reconstruye el comportamiento actual del monolito; el TO-BE hace explícitas las decisiones, políticas y fronteras semánticas propuestas.

## Requisitos para revisar la entrega

No es necesario instalar dependencias para leer la entrega: el PDF y todos los diagramas ya generados están incluidos.

Para validar o regenerar los modelos CML se necesita:

- [Context Mapper CLI](https://contextmapper.org/docs/context-mapper-cli/), disponible mediante el comando `cm`.
- Una instalación de Java compatible con la versión de Context Mapper utilizada.

El proyecto no fue desarrollado en Gitpod; por esta razón no requiere un archivo `.gitpod.yml`.

## Validación de los modelos

Desde la raíz del proyecto:

```bash
cm validate -i models/01-domain-model.cml
cm validate -i models/02-context-map-as-is.cml
cm validate -i models/021-team-map-as-is.cml
cm validate -i models/03-context-map-to-be.cml
cm validate -i models/031-team-map-to-be.cml
```

## Regeneración de los Context Maps

```bash
mkdir -p generated

cm generate -i models/02-context-map-as-is.cml -g context-map -o generated
cm generate -i models/021-team-map-as-is.cml -g context-map -o generated
cm generate -i models/03-context-map-to-be.cml -g context-map -o generated
cm generate -i models/031-team-map-to-be.cml -g context-map -o generated
```

Los PNG versionados en `docs/` permiten revisar los diagramas aunque el evaluador no tenga Context Mapper instalado.
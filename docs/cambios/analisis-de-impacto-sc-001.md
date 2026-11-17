# Análisis de impacto · SC-001: Detectar clientes sin actividad reciente

## Resumen
- **Solicitud:** SC-001, de Miriam Gómez (dupla de revisión), 12 de noviembre de 2026.
- **Qué pide:** una lista "Sin actividad" con los clientes de venta en curso que llevan mucho tiempo sin actividad registrada, con un plazo que define la agencia.
- **Tipo de mantenimiento:** perfectivo.
- **Prioridad sugerida:** media.
- **Fecha del análisis:** 16 de noviembre de 2026.

Se entiende por actividad cualquier registro con fecha en el historial del cliente: cotización, prueba de manejo, seguimiento tras la prueba o cambio de etapa. La última actividad se obtiene de esas fechas, así que no hace falta un historial nuevo.

## Módulos afectados (ADR-001)

| Módulo | Qué cambia | Impacto |
|---|---|---|
| Seguimiento y reportes | Arma la lista "Sin actividad" y guarda el plazo definido por la agencia | Alto: es donde crece |
| Clientes y ventas | Expone, por su interfaz, la fecha de última actividad de las ventas en curso de un vendedor | Medio |
| Usuarios y accesos | Permiso para que solo el gerente cambie el plazo. La lista usa la regla existente de que el vendedor solo ve sus clientes | Bajo |
| Catálogo de autos | Sin cambios | Ninguno |

La lista se arma pidiendo la información a clientes y ventas por su interfaz, no leyendo sus tablas, para respetar la regla del ADR-001.

## Documentos y diagramas afectados

| Pieza | Cambio |
|---|---|
| Especificación de requisitos | Dos requisitos nuevos: RF-022 (lista de clientes sin actividad) y RF-023 (configuración del plazo de inactividad). Se ajusta RF-008, que hoy no explica cómo un cliente llega a estar inactivo |
| Casos de uso (drawio y texto) | Dos casos nuevos: CU-15 (consultar clientes sin actividad, vendedor) y CU-16 (configurar el plazo de inactividad, gerente) |
| C4 contexto | Sin cambios: no hay actores ni sistemas nuevos |
| C4 contenedores | Sin cambios: misma aplicación y misma base de datos |
| C4 componentes | Una flecha nueva, de usuarios y accesos a seguimiento y reportes. La flecha de seguimiento a clientes y ventas ya existe y solo cambia su etiqueta |
| Diagrama de clases | Nueva clase para la regla de inactividad (plazo en días); operación para consultar la última actividad de una venta; operaciones del vendedor (ver la lista) y del gerente (definir el plazo) |
| Diagrama de secuencia | Una secuencia nueva para CU-15. La de CU-04 no cambia |
| Diagrama de estados | Sin cambios: la inactividad es del cliente (`activo`), no una etapa de la venta |
| Base de datos | Un lugar para guardar el plazo. La última actividad se calcula con las fechas que ya existen |

## Estimación de esfuerzo

| Pieza | Horas |
|---|---|
| Requisitos y casos de uso | 2 |
| Diagramas | 3 |
| Clientes y ventas: exponer la última actividad | 2 |
| Seguimiento y reportes: regla y lista | 6 |
| Plazo configurable y permiso del gerente | 3 |
| Pantalla "Sin actividad" | 4 |
| Pruebas de los cuatro criterios de aceptación | 3 |
| **Total** | **23 (unos 3 días de trabajo)** |


## Riesgos y decisiones abiertas
- **¿La lista marca al cliente como inactivo?** SC-001 solo pide mostrarlo. Si el sistema lo marcara solo, cambiaría `Cliente.activo` y habría que revisar RF-008.
- **Plazo inicial.** La agencia define cuánto es "mucho", pero falta un valor con el que arranque el sistema.
- **Rendimiento.** La consulta recorre las ventas en curso del vendedor. Debe probarse con el límite de 500 clientes por vendedor de RNF-REN-001.
- **Frontera entre módulos.** Revisar en el pull request que seguimiento y reportes no lea tablas de clientes y ventas.

## Decisión
Se acepta, después de los requisitos imprescindibles. Atiende el dolor central del vendedor (perder el seguimiento puede significar perder la venta), cae en módulos con fronteras claras y cierra el hueco de cómo se llega a inactivo. Su prioridad es media y el sistema ya es usable sin esto.

# Especificación de requisitos

#### **Sistema:** AutoTrack
#### **Autor:** Ana Camila López Sánchez
#### **Fecha de la última actualización:** 


## 1. Propósito y alcance

**Propósito del documento:** Este documento describe con detalle los requisitos funcionales y no funcionales del sistema AutoTrack, a partir de lo definido en la Visión del producto y de la información recabada en la entrevista con el vendedor. Va dirigido al equipo de desarrollo, al gerente de la agencia y a los vendedores que participarán como usuarios del sistema, para que todos compartan un mismo entendimiento de qué construirá el sistema y qué queda fuera de él.

**Alcance del sistema:** 
<li>Registrar clientes y su información de contacto, necesidades respecto a los vehículos, hobbies y aficiones.</li>
<li>Registrar la información tanto de los vendedores como del gerente.</li>
<li>Registrar los automóviles disponibles en la agencia y en la planta o centro de distribución, así como el automóvil de interés de cada cliente.</li>
<li>Actualizar el estado de cada venta (interesado, cotización, prueba de manejo, apartado, canal de venta —financiamiento o de contado—, cierre de la venta, entrega del vehículo, etc.).</li>
<li>Generar reportes de venta y seguimiento.</li>
<li>Guardar las ventas concretadas para que el vendedor y el gerente puedan consultarlas posteriormente.</li>


**Fuera del alcance:** 

<li>No procesará pagos ni generará contratos de compra ni contratos de financiamiento.</li>
<li>No enviará mensajes automáticos por WhatsApp, SMS o correo electrónico.</li>
<li>No permitirá realizar la compra del automóvil directamente desde el sistema.</li>

## 2. Usuarios y su contexto

| Usuario | Qué hace hoy sin el sistema | Qué espera del sistema |
|---|---|---|
| **Vendedor** | Atiende a varios clientes a la vez (según la temporada), y guarda la información de cada uno en conversaciones de WhatsApp, llamadas, notas sueltas o una hoja de Excel medianamente organizada. Depende de su memoria para recordar en qué etapa va cada cliente. | Tener en un solo lugar los datos de contacto, el auto de interés y el avance de cada cliente, para no perder el hilo del proceso ni dejar de dar seguimiento en el momento correcto. |
| **Gerente** | Pide actualizaciones directamente a cada vendedor para saber cómo van las ventas. | Consultar el estado de todas las ventas y el avance de cada vendedor sin depender de que se lo reporten manualmente, para tomar decisiones con información actualizada. |
| **Cliente** | Se comunica con el vendedor por WhatsApp o llamadas para preguntar por autos, recibir información y dar seguimiento a su proceso de compra. | Consultar el catálogo de autos disponibles, seleccionar los que le interesan y revisar en qué parte de su proceso de compra se encuentra, sin recibir mensajes innecesarios. |

**Conflictos identificados entre usuarios:** 
1. Vendedor vs. Cliente: el vendedor quiere contactar al cliente con frecuencia para aumentar las probabilidades de concretar la venta, mientras que el cliente prefiere recibir solo información relevante y no ser contactado constantemente. El sistema debe apoyar el seguimiento del vendedor sin forzar un contacto excesivo hacia el cliente.
2. Vendedor vs. Gerente: el vendedor necesita rapidez para registrar y avanzar a sus clientes sin que capturar datos le quite tiempo de venta, mientras que el gerente necesita que la información esté completa y actualizada para poder supervisar el proceso. El sistema debe definir un mínimo de información obligatoria que no vuelva pesado el registro para el vendedor pero sí sea suficiente para el gerente.

## 3. Requisitos funcionales

**3.1 Resumen**
| ID | Nombre | Prioridad | Origen |
|---|---|---|---|
| RF-001 | Registro de cliente | Imprescindible | Entrevista con el vendedor, preguntas 2 y 3 |
| RF-002 | Registro del automóvil de interés | Imprescindible | Entrevista con el vendedor, pregunta 3 |
| RF-003 | Generación de cotización | Imprescindible | Entrevista con el vendedor, pregunta 4 |
| RF-004 | Programación de prueba de manejo | Imprescindible | Entrevista con el vendedor, pregunta 5 |
| RF-005 | Registro de seguimiento tras la prueba de manejo | Imprescindible | Entrevista con el vendedor, pregunta 6 |
| RF-006 | Avance de etapa de la venta | Imprescindible | Entrevista con el vendedor, pregunta 7; Visión del producto, regla de negocio 2 |
| RF-007 | Cambio de automóvil de interés | Importante | Entrevista con el vendedor, pregunta 12 |
| RF-008 | Reactivación de cliente inactivo | Importante | Entrevista con el vendedor, pregunta 11 |
| RF-009 | Cierre de la venta | Imprescindible | Visión del producto, secciones 2 y 3 |
| RF-010 | Consulta de estado por el gerente | Importante | Entrevista con el vendedor, contexto general; Visión del producto, sección 2 |
| RF-011 | Reporte de ventas por etapa | Importante | Visión del producto, sección 3 (alcance) |
| RF-012 | Consulta de catálogo por el cliente | Deseable | Visión del producto, secciones 2 y 3 |
| RF-014 | Entrega del vehículo | Imprescindible | Visión del producto, sección 2; regla de negocio 3 |
| RF-015 | Consulta de ventas concretadas | Importante | Visión del producto, secciones 2 y 3 |
| RF-016 | Reporte de ventas por vendedor | Importante | Visión del producto, sección 3 (alcance) |
| RF-017 | Reporte de seguimiento a clientes | Importante | Visión del producto, sección 3 (alcance) |
| RF-018 | Retroceso de etapa de la venta | Importante | Entrevista con el vendedor, pregunta 11 |
| RF-019 | Venta perdida | Importante | Entrevista con el vendedor, pregunta 11; diagrama de estados |
| RF-020 | Consulta del estado de compra por el cliente | Deseable | Visión del producto, secciones 2 y 3 |
| RF-021 | Selección de automóviles de interés por el cliente | Deseable | Visión del producto, secciones 2 y 3 |                                  |


**RF-001 · Registro de cliente**
| Campo | Contenido |
|---|---|
| Descripción | El sistema permite al vendedor registrar los datos de contacto de un cliente y asociarlo como su responsable de seguimiento. |
| Origen | Entrevista con el vendedor, preguntas 2 y 3, 15 de septiembre. |
| Prioridad | Imprescindible |
| Criterio de aceptación | Al guardar un cliente con sus datos de contacto, este aparece en la lista de clientes del vendedor que lo registró. Si falta el dato de contacto, el sistema no guarda y señala cuál falta. |
| Relacionado con | RF-002, RNF-SEG-001 |
 
**RF-002 · Registro del automóvil de interés**
| Campo | Contenido |
|---|---|
| Descripción | El sistema permite registrar qué automóvil (modelo) le interesa a cada cliente, y consultarlo en cualquier momento del proceso. |
| Origen | Entrevista con el vendedor, pregunta 3, 15 de septiembre. |
| Prioridad | Imprescindible |
| Criterio de aceptación | Al guardar el automóvil de interés de un cliente, este queda visible en la ficha del cliente junto con sus demás datos. |
| Relacionado con | RF-001, RF-007 |
 
**RF-003 · Generación de cotización**
| Campo | Contenido |
|---|---|
| Descripción | El sistema permite al vendedor generar una cotización para el automóvil de interés de un cliente, antes de que se concrete la venta. |
| Origen | Entrevista con el vendedor, pregunta 4, 15 de septiembre. |
| Prioridad | Imprescindible |
| Criterio de aceptación | Al generar una cotización, esta queda asociada al cliente y visible en su historial, con la fecha en que se generó. |
| Relacionado con | RF-006 |
 
**RF-004 · Programación de prueba de manejo**
| Campo | Contenido |
|---|---|
| Descripción | El sistema permite al vendedor programar una prueba de manejo con un cliente para el automóvil de su interés. |
| Origen | Entrevista con el vendedor, pregunta 5, 15 de septiembre. |
| Prioridad | Imprescindible |
| Criterio de aceptación | Al programar una prueba de manejo con fecha, esta aparece en el historial del cliente. Si no se indica fecha, el sistema no guarda y señala el error. |
| Relacionado con | RF-005, RF-006 |
 
**RF-005 · Registro de seguimiento tras la prueba de manejo**
| Campo | Contenido |
|---|---|
| Descripción | El sistema permite al vendedor registrar la opinión o comentarios del cliente después de realizada la prueba de manejo. |
| Origen | Entrevista con el vendedor, pregunta 6, 15 de septiembre. |
| Prioridad | Imprescindible |
| Criterio de aceptación | Al guardar un seguimiento asociado a una prueba de manejo ya registrada, este queda visible en el historial del cliente con la fecha en que se realizó. |
| Relacionado con | RF-004, RF-007 |
 
**RF-006 · Avance de etapa de la venta**
| Campo | Contenido |
|---|---|
| Descripción | El sistema permite al vendedor avanzar la venta de un cliente a la siguiente etapa, en el orden establecido: interesado, cotización, prueba de manejo, negociación y apartado. El cierre (vendida) y la entrega (completada) se registran con RF-009 y RF-014. |
| Origen | Entrevista con el vendedor, pregunta 7, 15 de septiembre; Visión del producto, regla de negocio 2. |
| Prioridad | Imprescindible |
| Criterio de aceptación | Al avanzar la etapa de un cliente, el sistema solo permite pasar a la siguiente etapa del orden establecido, no permite saltar etapas, y el cambio queda reflejado con fecha en el historial del cliente. |
| Relacionado con | RF-003, RF-004, RF-008, RF-009, RF-018 |
 
**RF-007 · Cambio de automóvil de interés**
| Campo | Contenido |
|---|---|
| Descripción | El sistema permite modificar el automóvil de interés de un cliente que cambió de opinión, sin necesidad de crear un nuevo proceso de venta. |
| Origen | Entrevista con el vendedor, pregunta 12, 15 de septiembre. |
| Prioridad | Importante |
| Criterio de aceptación | Al cambiar el automóvil de interés de un cliente existente, el proceso de venta conserva su historial previo y solo se actualiza el dato del modelo. |
| Relacionado con | RF-002 |
 
**RF-008 · Reactivación de cliente inactivo**
| Campo | Contenido |
|---|---|
| Descripción | El sistema permite retomar el seguimiento de un cliente que dejó de responder y después vuelve a contactar, permitiendo repetir o ajustar los pasos necesarios del proceso. |
| Origen | Entrevista con el vendedor, pregunta 11, 15 de septiembre. |
| Prioridad | Importante |
| Criterio de aceptación | Al marcar a un cliente inactivo como "reactivado", el sistema conserva su historial anterior y permite continuar o repetir etapas del proceso sin perder la información previa. |
| Relacionado con | RF-006, RF-018 |
 
**RF-009 · Cierre de la venta**
| Campo | Contenido |
|---|---|
| Descripción | El sistema permite al vendedor marcar una venta como vendida cuando el canal de venta (financiamiento o de contado) ya está definido. |
| Origen | Visión del producto, sección 3 (alcance: canal de venta y cierre de la venta) y sección 2. |
| Prioridad | Imprescindible |
| Criterio de aceptación | Al marcar como vendida una venta en etapa apartado con el canal definido, la etapa cambia a vendida y queda en el historial con fecha. Si falta el canal, el sistema no cierra la venta y señala el dato faltante. |
| Relacionado con | RF-006, RF-014 |
 
**RF-010 · Consulta de estado por el gerente**
| Campo | Contenido |
|---|---|
| Descripción | El sistema permite al gerente consultar todas las ventas, la etapa del proceso de cada cliente y el avance de cada vendedor, sin depender de que se lo reporten manualmente. |
| Origen | Entrevista con el vendedor, contexto general; Visión del producto, sección 2. |
| Prioridad | Importante |
| Criterio de aceptación | Al ingresar al sistema, el gerente puede ver la lista de ventas en curso de todos los vendedores con su etapa actual, sin necesidad de solicitarla directamente a cada uno. |
| Relacionado con | RF-006 |
 
**RF-011 · Reporte de ventas por etapa**
| Campo | Contenido |
|---|---|
| Descripción | El sistema permite al gerente generar un reporte con la cantidad de ventas que hay en cada etapa durante un periodo. |
| Origen | Visión del producto, sección 3 (alcance). |
| Prioridad | Importante |
| Criterio de aceptación | Al indicar un periodo, el sistema muestra cuántas ventas hay en cada etapa. |
| Relacionado con | RF-006, RF-010, RF-016 |
 
**RF-012 · Consulta de catálogo por el cliente**
| Campo | Contenido |
|---|---|
| Descripción | El sistema permite al cliente consultar el catálogo de autos disponibles de la marca. |
| Origen | Visión del producto, sección 3 (alcance); sección 2 ("¿Quién puede hacer qué?"). |
| Prioridad | Deseable |
| Criterio de aceptación | Al ingresar al sistema, el cliente puede ver la lista de autos disponibles. |
| Relacionado con | RF-002, RF-021 |
 
**RF-014 · Entrega del vehículo**
| Campo | Contenido |
|---|---|
| Descripción | El sistema permite al vendedor registrar la entrega del vehículo de una venta en etapa vendida. |
| Origen | Visión del producto, sección 2 ("¿Qué pasa cuando se concreta una venta?"); regla de negocio 3. |
| Prioridad | Imprescindible |
| Criterio de aceptación | Al registrar la entrega, la venta pasa a completada con la fecha de entrega y deja de aparecer en la lista de pendientes del vendedor. Si el vehículo aún no está disponible, el sistema no permite registrar la entrega. |
| Relacionado con | RF-009, RF-015 |
 
**RF-015 · Consulta de ventas concretadas**
| Campo | Contenido |
|---|---|
| Descripción | El sistema permite al vendedor y al gerente consultar las ventas completadas y su historial. |
| Origen | Visión del producto, sección 2 ("Se guarda el historial") y sección 3 (alcance). |
| Prioridad | Importante |
| Criterio de aceptación | Al consultar el historial de ventas concretadas, el vendedor ve las ventas completadas que atendió y el gerente ve las de todos los vendedores, cada una con su historial de etapas. |
| Relacionado con | RF-014, RNF-SEG-001 |
 
**RF-016 · Reporte de ventas por vendedor**
| Campo | Contenido |
|---|---|
| Descripción | El sistema permite al gerente generar un reporte con la cantidad de ventas de cada vendedor durante un periodo. |
| Origen | Visión del producto, sección 3 (alcance). |
| Prioridad | Importante |
| Criterio de aceptación | Al indicar un periodo, el sistema muestra cuántas ventas tiene cada vendedor. |
| Relacionado con | RF-010, RF-011 |
 
**RF-017 · Reporte de seguimiento a clientes**
| Campo | Contenido |
|---|---|
| Descripción | El sistema permite al gerente generar un reporte del seguimiento que cada vendedor dio a sus clientes durante un periodo. |
| Origen | Visión del producto, sección 3 (alcance). |
| Prioridad | Importante |
| Criterio de aceptación | Al indicar un periodo, el sistema muestra, por vendedor, cuántas cotizaciones generó, cuántas pruebas de manejo realizó y cuántas opiniones de clientes registró tras la prueba. |
| Relacionado con | RF-003, RF-004, RF-005 |
 
**RF-018 · Retroceso de etapa de la venta**
| Campo | Contenido |
|---|---|
| Descripción | El sistema permite al vendedor regresar una venta a la etapa anterior indicando un motivo, cuando hay que repetir pasos con el cliente. |
| Origen | Entrevista con el vendedor, pregunta 11, 15 de septiembre; separado de RF-006 el 16 de noviembre. |
| Prioridad | Importante |
| Criterio de aceptación | Al retroceder la etapa, el sistema pide un motivo breve. Sin motivo, no cambia la etapa y lo señala. Con motivo, la venta regresa a la etapa anterior y el motivo queda en el historial con fecha. |
| Relacionado con | RF-006, RF-008 |
 
**RF-019 · Venta perdida**
| Campo | Contenido |
|---|---|
| Descripción | El sistema permite al vendedor marcar como perdida una venta en la que el cliente desiste, conservando su historial. |
| Origen | Entrevista con el vendedor, pregunta 11, 15 de septiembre; diagrama de estados (transición "cliente desiste"). |
| Prioridad | Importante |
| Criterio de aceptación | Al marcar una venta como perdida, la etapa cambia a perdida con fecha, la venta deja de aparecer en la lista de pendientes y su historial se conserva. |
| Relacionado con | RF-006, RF-008 |
 
**RF-020 · Consulta del estado de compra por el cliente**
| Campo | Contenido |
|---|---|
| Descripción | El sistema permite al cliente revisar en qué etapa se encuentra su proceso de compra. |
| Origen | Visión del producto, sección 2 ("¿Quién puede hacer qué?") y sección 3 (alcance). |
| Prioridad | Deseable |
| Criterio de aceptación | Al ingresar al sistema, el cliente con una venta iniciada ve la etapa actual de su venta. Si aún no tiene proceso, el sistema le indica que contacte a un vendedor. |
| Relacionado con | RF-006, RNF-SEG-001 |
 
**RF-021 · Selección de automóviles de interés por el cliente**
| Campo | Contenido |
|---|---|
| Descripción | El sistema permite al cliente marcar uno o más autos del catálogo como de su interés. |
| Origen | Visión del producto, sección 3 (alcance); sección 2 ("¿Quién puede hacer qué?"). |
| Prioridad | Deseable |
| Criterio de aceptación | Al marcar uno o más autos, estos quedan reflejados en la ficha del cliente. |
| Relacionado con | RF-002, RF-012 |

## 4. Requisitos no funcionales

**4.1 Resumen**
| ID          | Atributo       | Nombre                                     | Prioridad      | Origen                                                                                         |
| ----------- | -------------- | ------------------------------------------ | -------------- | ---------------------------------------------------------------------------------------------- |
| RNF-REN-001 | Rendimiento    | Tiempo de consulta de la ficha del cliente | Importante     | Derivado del tipo de sistema y de la entrevista (dolor: dificultad para encontrar información) |
| RNF-SEG-001 | Seguridad      | Acceso restringido por tipo de usuario     | Imprescindible | Visión del producto, sección 4 (atributos de calidad)                                          |
| RNF-USA-001 | Usabilidad     | Registro rápido de datos del cliente       | Imprescindible | Entrevista con el vendedor, pregunta 9; Visión del producto, sección 4                         |
| RNF-DIS-001 | Disponibilidad | Acceso al sistema en horario de trabajo    | Importante     | Visión del producto, sección 4 (atributos de calidad)                                          |

#### 4.2 Fichas

**RNF-REN-001 · Tiempo de consulta de la ficha del cliente**

| Campo               | Contenido                                                                                                                                                                                 |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Atributo de calidad | Rendimiento                                                                                                                                                                               |
| Descripción         | La ficha de un cliente, con sus datos de contacto, automóvil de interés e historial de etapas, se despliega en menos de tres segundos.                                                    |
| Métrica             | Tiempo entre la solicitud y el despliegue completo de la ficha, medido con hasta 500 clientes registrados por vendedor.                                                                   |
| Origen              | Derivado del tipo de sistema (sistema de información de consulta frecuente) y del dolor reportado en la entrevista sobre encontrar información de un cliente rápidamente.                 |
| Prioridad           | Importante                                                                                                                                                                                |
| Por qué importa     | El vendedor suele consultar la ficha mientras habla con el cliente (en persona, por teléfono o por WhatsApp). Si tarda, pierde fluidez en la conversación y puede dar una mala impresión. |
| Afecta a            | RF-001, RF-002, RF-006                                                                                                                                                                    |

**RNF-SEG-001 · Acceso restringido por tipo de usuario**

| Campo               | Contenido                                                                                                                                                                                                                                                                      |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Atributo de calidad | Seguridad                                                                                                                                                                                                                                                                      |
| Descripción         | El sistema restringe las acciones y la información visible según el tipo de usuario: el vendedor solo puede ver y modificar la información de sus propios clientes, el gerente puede ver y modificar la de todos, y el cliente solo puede ver su propio proceso y el catálogo. |
| Métrica             | Porcentaje de intentos de acceso no autorizado bloqueados correctamente, medido sobre pruebas de acceso cruzado entre usuarios (debe ser 100%).                                                                                                                                |
| Origen              | Visión del producto, sección 4 (atributo "Seguridad") y sección 2 ("¿Quién puede hacer qué?").                                                                                                                                                                                 |
| Prioridad           | Imprescindible                                                                                                                                                                                                                                                                 |
| Por qué importa     | Los datos de contacto y el proceso de compra de un cliente son información sensible. Si un vendedor pudiera ver o modificar clientes de otro vendedor, o un cliente viera el proceso de otro, se perdería la confianza en el sistema y podría haber consecuencias legales.     |
| Afecta a            | RF-001, RF-006, RF-010                                                                                                                                                                                                                                                         |

**RNF-USA-001 · Registro rápido de datos del cliente**

| Campo               | Contenido                                                                                                                                                                                                                                                 |
| ------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Atributo de calidad | Usabilidad                                                                                                                                                                                                                                                |
| Descripción         | El vendedor puede registrar un cliente nuevo con sus datos básicos y automóvil de interés en pocos pasos, sin necesidad de capacitación extensa.                                                                                                          |
| Métrica             | Tiempo promedio para completar el registro de un cliente nuevo (objetivo: menos de un minuto) y número de pasos/clics requeridos.                                                                                                                         |
| Origen              | Entrevista con el vendedor, pregunta 9 (información que a veces no se registra correctamente en Excel por falta de orden); Visión del producto, sección 4 (atributo "Usabilidad").                                                                        |
| Prioridad           | Imprescindible                                                                                                                                                                                                                                            |
| Por qué importa     | El vendedor atiende a varios clientes a la vez y su prioridad es vender, no capturar datos. Si el registro es lento o confuso, es probable que deje de usar el sistema y vuelva a WhatsApp o notas sueltas, repitiendo el problema que se busca resolver. |
| Afecta a            | RF-001, RF-002                                                                                                                                                                                                                                            |

**RNF-DIS-001 · Acceso al sistema en horario de trabajo**

| Campo               | Contenido                                                                                                                                                                                                                                           |
| ------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Atributo de calidad | Disponibilidad                                                                                                                                                                                                                                      |
| Descripción         | El sistema está disponible para consulta y registro durante el horario laboral de la agencia, incluyendo fines de semana si la agencia opera esos días.                                                                                             |
| Métrica             | Porcentaje de tiempo activo (uptime) durante el horario laboral definido (objetivo: 99%).                                                                                                                                                           |
| Origen              | Visión del producto, sección 4 (atributo "Disponibilidad").                                                                                                                                                                                         |
| Prioridad           | Importante                                                                                                                                                                                                                                          |
| Por qué importa     | Si el sistema no está disponible mientras el vendedor atiende a un cliente, puede perder la oportunidad de registrar información importante o dar seguimiento a tiempo, lo que, de acuerdo con la entrevista, ya es una causa de pérdida de ventas. |
| Afecta a            | RF-001, RF-006, RF-008                                                                                                                                                                                                                              |


## 5. Casos de uso

### CU-01 · Registrar un cliente nuevo
 
| Campo | Información |
|---|---|
| **Actor principal** | Vendedor |
| **Objetivo** | Guardar en el sistema los datos de contacto de un cliente nuevo y quedar como su vendedor responsable. |
| **Precondición** | El cliente no está registrado previamente en el sistema. |
| **Escenario principal** | 1. El vendedor busca al cliente por nombre o teléfono para verificar que no exista ya.<br>2. El sistema confirma que no hay coincidencias.<br>3. El vendedor captura los datos de contacto del cliente.<br>4. El sistema guarda al cliente.<br>5. El sistema asocia al cliente con el vendedor que lo registró como su responsable.<br>6. El sistema muestra la ficha del cliente recién creada, lista para continuar el proceso de venta. |
| **Flujos alternos** | **2a.** El cliente ya existe en el sistema: el sistema muestra la ficha existente y cancela el alta duplicada. Fin del caso de uso.<br>**3a.** Falta un dato de contacto obligatorio: el sistema no guarda y señala cuál dato falta. Regresa al paso 3. |
| **Postcondición** | El cliente queda registrado y visible en la lista de clientes del vendedor. |
| **Requisitos que realiza** | RF-001, RNF-USA-001, RNF-SEG-001 |
 
---
 
### CU-02 · Generar una cotización
 
| Campo | Información |
|---|---|
| **Actor principal** | Vendedor |
| **Objetivo** | Entregar al cliente una cotización formal del automóvil de su interés. |
| **Precondición** | El cliente está registrado y tiene un automóvil de interés asignado. |
| **Escenario principal** | 1. El vendedor abre la ficha del cliente.<br>2. El sistema muestra el automóvil de interés registrado.<br>3. El vendedor solicita generar la cotización.<br>4. El sistema genera la cotización con el modelo, precio y condiciones vigentes.<br>5. El sistema asocia la cotización al historial del cliente con la fecha en que se generó. |
| **Flujos alternos** | **2a.** El cliente aún no tiene automóvil de interés registrado: el sistema pide asignarlo antes de continuar (enlaza con RF-002). Una vez asignado, regresa al paso 3.<br>**4a.** El automóvil no tiene precio o condiciones vigentes cargadas: el sistema no genera la cotización y lo señala al vendedor. Fin del caso de uso. |
| **Postcondición** | La cotización queda registrada en el historial del cliente y disponible para consulta posterior. |
| **Requisitos que realiza** | RF-002, RF-003 |
 
---
 
### CU-03 · Programar una prueba de manejo
 
| Campo | Información |
|---|---|
| **Actor principal** | Vendedor |
| **Objetivo** | Reservar una prueba de manejo del automóvil de interés para un cliente en una fecha determinada. |
| **Precondición** | El cliente está registrado y tiene un automóvil de interés asignado. |
| **Escenario principal** | 1. El vendedor abre la ficha del cliente.<br>2. El vendedor selecciona programar una prueba de manejo.<br>3. El sistema muestra el automóvil de interés del cliente.<br>4. El vendedor elige fecha y hora para la prueba.<br>5. El sistema registra la prueba de manejo con esos datos.<br>6. El sistema muestra la prueba en el historial del cliente. |
| **Flujos alternos** | **4a.** No se indica fecha u hora: el sistema no guarda y señala el dato faltante. Regresa al paso 4.<br>**5a.** El cliente ya tiene una prueba de manejo pendiente sin realizar: el sistema advierte al vendedor y pregunta si desea reprogramarla o agregar una nueva. Tras la elección del vendedor, continúa en el paso 5. |
| **Postcondición** | La prueba de manejo queda registrada y visible en el historial del cliente. |
| **Requisitos que realiza** | RF-004 |
 
---
 
### CU-04 · Avanzar la etapa de venta de un cliente
 
| Campo | Información |
|---|---|
| **Actor principal** | Vendedor |
| **Objetivo** | Reflejar en el sistema el avance real de un cliente dentro del proceso de venta, de modo que tanto el vendedor como el gerente sepan en qué parte se encuentra sin tener que preguntarlo. |
| **Precondición** | El cliente ya está registrado, tiene una venta en curso y una etapa asignada (la etapa inicial es "interesado"). Este caso cubre el avance de interesado a apartado; el cierre y la entrega son CU-08 y CU-09. |
| **Escenario principal** | 1. El vendedor busca al cliente por nombre o teléfono.<br>2. El sistema muestra la ficha del cliente, con su etapa actual y el historial de avance.<br>3. El vendedor selecciona avanzar a la siguiente etapa.<br>4. El sistema verifica que la nueva etapa sea la siguiente en el orden establecido (interesado → cotización → prueba de manejo → negociación → apartado).<br>5. El sistema registra el cambio de etapa con fecha en el historial del cliente.<br>6. El sistema muestra la ficha actualizada con la nueva etapa. |
| **Flujos alternos** | **4a.** El vendedor intenta saltar una etapa: el sistema no permite el cambio y muestra cuál es la siguiente etapa válida. Regresa al paso 3.<br>**4b.** El cliente estaba marcado como inactivo: el sistema sugiere confirmar primero si el cliente sigue interesado en el mismo automóvil (enlaza con CU-05). Una vez reactivado, regresa al paso 3.<br>**4c.** La venta ya está cerrada (vendida, completada o perdida): el sistema no permite modificar la etapa y solo muestra el historial. Fin del caso de uso. |
| **Postcondición** | La etapa del cliente queda actualizada y visible tanto en la ficha del vendedor como en el panel del gerente, con la fecha del cambio registrada en el historial. |
| **Requisitos que realiza** | RF-006, RF-008, RNF-SEG-001 |
 
---
 
### CU-05 · Reactivar el seguimiento de un cliente inactivo
 
| Campo | Información |
|---|---|
| **Actor principal** | Vendedor |
| **Objetivo** | Retomar el proceso de un cliente que dejó de responder y después volvió a contactar, sin perder la información previa. |
| **Precondición** | El cliente existe en el sistema y está marcado como inactivo. |
| **Escenario principal** | 1. El vendedor busca al cliente que volvió a contactar.<br>2. El sistema muestra la ficha del cliente marcada como inactiva, junto con su última etapa registrada.<br>3. El vendedor confirma que el cliente sigue interesado en el mismo automóvil.<br>4. El sistema marca al cliente como reactivado.<br>5. El sistema continúa el proceso desde la última etapa registrada.<br>6. El sistema conserva el historial anterior del cliente. |
| **Flujos alternos** | **3a.** El cliente cambió de automóvil de interés: el vendedor actualiza el modelo antes de continuar (enlaza con RF-007). Continúa en el paso 4.<br>**3b.** El cliente ya no está interesado en comprar: el vendedor marca la venta como perdida (CU-11) y el sistema no reactiva el proceso. Fin del caso de uso. |
| **Postcondición** | El cliente queda reactivado y su proceso de venta continúa visible en la lista de pendientes del vendedor, sin perder el historial previo. |
| **Requisitos que realiza** | RF-007, RF-008 |
 
---
 
### CU-06 · Consultar el avance de ventas de la agencia
 
| Campo | Información |
|---|---|
| **Actor principal** | Gerente |
| **Objetivo** | Conocer el estado de todas las ventas en curso y el avance de cada vendedor sin tener que pedírselo directamente a cada uno. |
| **Precondición** | Existen clientes y ventas registradas en el sistema. |
| **Escenario principal** | 1. El gerente ingresa al sistema.<br>2. El gerente accede al panel de ventas.<br>3. El sistema muestra la lista de ventas en curso de todos los vendedores con su etapa actual.<br>4. El gerente filtra por vendedor, etapa o rango de fechas.<br>5. El sistema actualiza la lista según el filtro aplicado.<br>6. El gerente selecciona una venta.<br>7. El sistema muestra el detalle de la venta. |
| **Flujos alternos** | **5a.** No hay ventas que cumplan el filtro aplicado: el sistema muestra un mensaje indicando que no hay resultados. Regresa al paso 4. |
| **Postcondición** | El gerente obtiene una visión actualizada del estado de las ventas sin depender de reportes manuales de los vendedores. |
| **Requisitos que realiza** | RF-010, RNF-REN-001, RNF-SEG-001 |
 
---
 
### CU-07 · Consultar el catálogo y elegir autos de interés
 
| Campo | Información |
|---|---|
| **Actor principal** | Cliente |
| **Objetivo** | Ver los automóviles disponibles de la agencia y marcar los que le interesan. |
| **Precondición** | El cliente tiene acceso al sistema (ya sea registrado por un vendedor o con cuenta propia). |
| **Escenario principal** | 1. El cliente ingresa al sistema.<br>2. El sistema muestra el catálogo de automóviles disponibles de la agencia y de la marca.<br>3. El cliente selecciona uno o más automóviles de su interés.<br>4. El sistema guarda la selección en la ficha del cliente. |
| **Flujos alternos** | **3a.** El cliente ya tiene un automóvil de interés registrado por el vendedor: el sistema le pregunta si desea mantenerlo o cambiarlo. Tras su respuesta, continúa en el paso 4. |
| **Postcondición** | El cliente conoce los automóviles disponibles y los que seleccionó quedan en su ficha. |
| **Requisitos que realiza** | RF-012, RF-021 |
 
---
 
### CU-08 · Cerrar una venta
 
| Campo | Información |
|---|---|
| **Actor principal** | Vendedor |
| **Objetivo** | Marcar una venta como vendida una vez definido el canal de venta. |
| **Precondición** | La venta del cliente se encuentra en la etapa "apartado". |
| **Escenario principal** | 1. El vendedor abre la ficha del cliente cuya venta está por cerrarse.<br>2. El sistema muestra la etapa actual y el resumen del proceso de venta.<br>3. El vendedor indica el canal de venta (financiamiento o de contado).<br>4. El vendedor confirma el cierre de la venta.<br>5. El sistema cambia la etapa a vendida y registra la fecha del cierre. |
| **Flujos alternos** | **4a.** El vendedor confirma sin haber indicado el canal de venta: el sistema no cierra la venta y señala el dato faltante. Regresa al paso 3. |
| **Postcondición** | La venta queda en etapa "vendida", pendiente de entrega (CU-09), con el canal de venta y la fecha de cierre en su historial. |
| **Requisitos que realiza** | RF-009 |
 
---
 
### CU-09 · Entregar el vehículo
 
| Campo | Información |
|---|---|
| **Actor principal** | Vendedor |
| **Objetivo** | Registrar la entrega del vehículo y completar la venta, conservando su historial. |
| **Precondición** | La venta del cliente se encuentra en la etapa "vendida" y el vehículo está listo para entrega. |
| **Escenario principal** | 1. El vendedor abre la ficha del cliente cuya venta está vendida.<br>2. El sistema muestra la etapa actual y el resumen del proceso de venta.<br>3. El vendedor registra la entrega del vehículo.<br>4. El sistema cambia la etapa a completada y registra la fecha de entrega.<br>5. El sistema retira la venta de la lista de pendientes del vendedor.<br>6. El sistema agrega la venta al historial de ventas concretadas. |
| **Flujos alternos** | **3a.** El vehículo aún no está disponible para entrega: el sistema no permite registrar la entrega y muestra la fecha estimada de disponibilidad. Fin del caso de uso. |
| **Postcondición** | La venta queda completada, deja de aparecer en pendientes y su historial queda disponible para consulta del vendedor y del gerente. |
| **Requisitos que realiza** | RF-014 |
 
---
 
### CU-10 · Retroceder la etapa de venta de un cliente
 
| Campo | Información |
|---|---|
| **Actor principal** | Vendedor |
| **Objetivo** | Regresar la venta a la etapa anterior cuando hay que repetir pasos con el cliente. |
| **Precondición** | El cliente tiene una venta en curso en una etapa distinta de "interesado". |
| **Escenario principal** | 1. El vendedor busca al cliente por nombre o teléfono.<br>2. El sistema muestra la ficha del cliente, con su etapa actual.<br>3. El vendedor selecciona retroceder a la etapa anterior.<br>4. El sistema solicita un motivo breve.<br>5. El vendedor captura el motivo.<br>6. El sistema registra el retroceso con fecha y motivo en el historial del cliente.<br>7. El sistema muestra la ficha con la etapa anterior. |
| **Flujos alternos** | **3a.** La venta está en "interesado" o ya está cerrada (vendida, completada o perdida): el sistema no permite retroceder. Fin del caso de uso.<br>**5a.** El vendedor no captura el motivo: el sistema no cambia la etapa y señala que el motivo es obligatorio. Regresa al paso 5. |
| **Postcondición** | La venta queda en la etapa anterior y el motivo queda registrado en el historial. |
| **Requisitos que realiza** | RF-018, RNF-SEG-001 |
 
---
 
### CU-11 · Marcar una venta como perdida
 
| Campo | Información |
|---|---|
| **Actor principal** | Vendedor |
| **Objetivo** | Cerrar como perdida una venta en la que el cliente desiste, sin perder su historial. |
| **Precondición** | La venta está en curso y aún no está vendida (etapa de interesado a apartado). |
| **Escenario principal** | 1. El vendedor abre la ficha del cliente.<br>2. El sistema muestra la etapa actual y el historial de la venta.<br>3. El vendedor selecciona marcar la venta como perdida.<br>4. El sistema cambia la etapa a perdida y registra la fecha.<br>5. El sistema retira la venta de la lista de pendientes del vendedor. |
| **Flujos alternos** | **3a.** La venta ya está vendida o completada: el sistema no permite marcarla como perdida. Fin del caso de uso. |
| **Postcondición** | La venta queda perdida, deja de aparecer en pendientes y su historial se conserva. |
| **Requisitos que realiza** | RF-019 |
 
---
 
### CU-12 · Consultar el estado de mi proceso de compra
 
| Campo | Información |
|---|---|
| **Actor principal** | Cliente |
| **Objetivo** | Revisar en qué parte de su proceso de compra se encuentra, sin contactar al vendedor. |
| **Precondición** | El cliente tiene acceso al sistema. |
| **Escenario principal** | 1. El cliente ingresa al sistema.<br>2. El cliente accede a su proceso de compra.<br>3. El sistema muestra la etapa actual de su venta. |
| **Flujos alternos** | **3a.** El cliente aún no tiene un proceso de compra iniciado: el sistema muestra un mensaje indicando que debe contactar a un vendedor para comenzar. Fin del caso de uso. |
| **Postcondición** | El cliente conoce el estado de su propio proceso de compra. |
| **Requisitos que realiza** | RF-020, RNF-SEG-001 |
 
---
 
### CU-13 · Generar un reporte de ventas o de seguimiento
 
| Campo | Información |
|---|---|
| **Actor principal** | Gerente |
| **Objetivo** | Obtener un reporte de ventas o de seguimiento de un periodo. |
| **Precondición** | Existen ventas registradas en el sistema. |
| **Escenario principal** | 1. El gerente accede a la sección de reportes.<br>2. El sistema muestra los reportes disponibles: ventas por etapa, ventas por vendedor y seguimiento a clientes.<br>3. El gerente selecciona un reporte.<br>4. El gerente indica el periodo.<br>5. El sistema genera el reporte del periodo indicado.<br>6. El sistema muestra el reporte. |
| **Flujos alternos** | **4a.** El gerente no indica el periodo: el sistema no genera el reporte y señala el dato faltante. Regresa al paso 4.<br>**5a.** No hay información en el periodo indicado: el sistema muestra un mensaje indicando que no hay resultados. Fin del caso de uso. |
| **Postcondición** | El gerente cuenta con el reporte del periodo indicado. |
| **Requisitos que realiza** | RF-011, RF-016, RF-017 |
 
---
 
### CU-14 · Consultar las ventas concretadas
 
| Campo | Información |
|---|---|
| **Actor principal** | Vendedor (también el gerente) |
| **Objetivo** | Consultar las ventas completadas y su historial. |
| **Precondición** | Existen ventas completadas en el sistema. |
| **Escenario principal** | 1. El usuario accede al historial de ventas concretadas.<br>2. El sistema muestra las ventas completadas a las que tiene acceso (el vendedor, las suyas; el gerente, las de todos).<br>3. El usuario selecciona una venta.<br>4. El sistema muestra el historial de etapas de la venta. |
| **Flujos alternos** | **2a.** No hay ventas completadas: el sistema muestra un mensaje indicando que no hay resultados. Fin del caso de uso. |
| **Postcondición** | El usuario conoce el historial de la venta consultada. |
| **Requisitos que realiza** | RF-015, RNF-SEG-001 |


## 6. Trazabilidad


| Requisito | Origen | Caso de uso | Elemento del prototipo |
|---|---|---|---|
| RF-001 | Entrevista 15 sep, preguntas 2 y 3 | CU-01 Registrar un cliente nuevo | Pantalla "Nuevo cliente" |
| RF-002 | Entrevista 15 sep, pregunta 3 | CU-01 Registrar un cliente nuevo; CU-02 (flujo 2a) | Pantalla "Nuevo cliente" (campo automóvil de interés) |
| RF-003 | Entrevista 15 sep, pregunta 4 | CU-02 Generar una cotización | Pantalla "Cotización" |
| RF-004 | Entrevista 15 sep, pregunta 5 | CU-03 Programar una prueba de manejo | Pantalla "Agendar prueba de manejo" |
| RF-005 | Entrevista 15 sep, pregunta 6 | CU-03 Programar una prueba de manejo (flujo posterior) | Pantalla "Ficha del cliente" (sección seguimiento) |
| RF-006 | Entrevista 15 sep, pregunta 7; Visión del producto, regla de negocio 2 | CU-04 Avanzar la etapa de venta | Pantalla "Ficha del cliente" (selector de etapa) |
| RF-007 | Entrevista 15 sep, pregunta 12 | CU-05 Reactivar el seguimiento (flujo 3a) | Pantalla "Ficha del cliente" (campo automóvil de interés, editable) |
| RF-008 | Entrevista 15 sep, pregunta 11 | CU-04 (flujo 4b); CU-05 Reactivar el seguimiento de un cliente inactivo | Pantalla "Ficha del cliente" (etiqueta "inactivo" y botón reactivar) |
| RF-009 | Visión del producto, secciones 2 y 3 | CU-08 Cerrar una venta | Pantalla "Cierre de venta" |
| RF-010 | Entrevista 15 sep, contexto general; Visión del producto, sección 2 | CU-06 Consultar el avance de ventas de la agencia | Panel "Ventas de la agencia" (vista gerente) |
| RF-011 | Visión del producto, sección 3 (alcance) | CU-13 Generar un reporte | No entra en este prototipo |
| RF-012 | Visión del producto, secciones 2 y 3 | CU-07 Consultar el catálogo y elegir autos de interés | No entra en este prototipo |
| RF-014 | Visión del producto, sección 2 y regla de negocio 3 | CU-09 Entregar el vehículo | Pantalla "Cierre de venta" |
| RF-015 | Visión del producto, secciones 2 y 3 | CU-14 Consultar las ventas concretadas | No entra en este prototipo |
| RF-016 | Visión del producto, sección 3 (alcance) | CU-13 Generar un reporte | No entra en este prototipo |
| RF-017 | Visión del producto, sección 3 (alcance) | CU-13 Generar un reporte | No entra en este prototipo |
| RF-018 | Entrevista 15 sep, pregunta 11 | CU-10 Retroceder la etapa de venta | Pantalla "Ficha del cliente" (selector de etapa) |
| RF-019 | Entrevista 15 sep, pregunta 11; diagrama de estados | CU-11 Marcar una venta como perdida; CU-05 (flujo 3b) | Por confirmar |
| RF-020 | Visión del producto, secciones 2 y 3 | CU-12 Consultar el estado de mi proceso de compra | No entra en este prototipo |
| RF-021 | Visión del producto, secciones 2 y 3 | CU-07 Consultar el catálogo y elegir autos de interés | No entra en este prototipo |
| RNF-REN-001 | Derivado del tipo de sistema; entrevista, pregunta 9 | CU-01, CU-06 | Pantalla "Ficha del cliente" |
| RNF-SEG-001 | Visión del producto, sección 4 | CU-01, CU-04, CU-06, CU-10, CU-12, CU-14 | Control de acceso por rol (login) |
| RNF-USA-001 | Entrevista 15 sep, pregunta 9; Visión del producto, sección 4 | CU-01 Registrar un cliente nuevo | Pantalla "Nuevo cliente" |
| RNF-DIS-001 | Visión del producto, sección 4 | CU-04, CU-05 | Infraestructura del sistema (no es una pantalla) |


## 7. Registro de cambios

| Fecha | Requisito | Qué cambió | Por qué |
|---|---|---|---|
| 20 sep 2026 | RF-005 | Prioridad cambió de "Importante" a "Imprescindible" | El gerente indicó que el seguimiento post-prueba de manejo es indispensable para no perder ventas, no solo deseable. |
| 22 sep 2026 | RF-013 (eliminado) | Se eliminó el requisito de envío de recordatorios automáticos | Estaba fuera del alcance definido en la Visión del producto; se agregó por error en una revisión anterior. |
| 19 oct 2026 | RF-005 | La ficha se corrigió a "Imprescindible" | La ficha seguía en "Importante" y no coincidía con el resumen ni con el cambio del 20 sep. |
| 11 nov 2026 | Etapas de la venta (alcance, RF-006, CU-04, CU-08) | Se unificó una sola lista de etapas: interesado, cotización, prueba de manejo, negociación, apartado, vendida, completada y perdida | Las secciones usaban listas distintas (revisión de la dupla, sección 8). |
| 11 nov 2026 | RF-006, RF-009, RF-011, RF-012 | Cada uno se dividió para tener un solo objetivo. Nuevos: RF-014 (entrega), RF-015 (ventas concretadas), RF-016 y RF-017 (reportes), RF-018 (retroceso), RF-019 (venta perdida), RF-020 (estado de compra) y RF-021 (selección de autos) | Retroalimentación de la evaluación: requisitos con más de un objetivo y un reporte por requisito. |
| 16 nov 2026 | CU-04 a CU-08 | Se separaron los casos con más de un objetivo. Nuevos: CU-09 a CU-14. Se redactaron los pasos con una sola acción y todos los flujos alternos regresan al flujo normal o terminan | Retroalimentación de la evaluación: pasos con varias acciones y cursos alternos sin cierre. |
| 16 nov 2026 | CU-06 | Se quitó el flujo 5a (marcar una venta para seguimiento o notificar al vendedor) | No tenía requisito asociado y era un objetivo distinto. |


## 8. Revisión de la dupla
<li>Las etapas de venta no coinciden entre secciones. El alcance menciona interesado, cotización, prueba de manejo, apartado, canal de venta, cierre y entrega. RF-006 define interesado → cotización → prueba de manejo → negociación → apartado → venta. "Negociación" no aparece en el alcance, y "entrega/completada", "inactivo" y "perdida" no forman parte del flujo formal. Conviene definir una sola lista de estados y usarla en todo el documento.</li>
<li>Gestión de catálogo e inventario. El alcance habla de autos en agencia y en planta, y CU-02 y CU-08 dependen de precios, condiciones y fechas de disponibilidad cargadas. Ningún RF define quién da de alta los autos ni cómo se mantienen esos datos.</li>
<li>Registro de vendedores y gerente. Está en el alcance, pero no tiene RF.</li>
<li>Paso a inactivo. RF-008 cubre la reactivación, pero no cómo un cliente se vuelve inactivo: ¿es manual o automático después de X días sin actividad?</li>
<li>RNF-DIS-001: el "horario laboral" no está definido, y "fines de semana si la agencia opera" es ambiguo. Para medir el 99% hace falta fijar las horas.</li>
<li>Faltan respaldo e integridad del historial. Varios RF dependen de que el historial no se pierda, pero no hay RNF de respaldos ni de bitácora de cambios (quién modificó qué).</li>
<li>RF-001: dice "el dato de contacto". ¿Cuáles son obligatorios: teléfono, correo, ambos? La validación de duplicados está en CU-01, pero no en el criterio del RF.</li>

* Pendientes que en la próxima entrega estarán modificados

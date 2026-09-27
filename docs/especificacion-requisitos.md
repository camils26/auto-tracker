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
| ID     | Nombre                                           | Prioridad      | Origen                                                                          |
| ------ | ------------------------------------------------ | -------------- | ------------------------------------------------------------------------------- |
| RF-001 | Registro de cliente                              | Imprescindible | Entrevista con el vendedor, preguntas 2 y 3                                     |
| RF-002 | Registro del automóvil de interés                | Imprescindible | Entrevista con el vendedor, pregunta 3                                          |
| RF-003 | Generación de cotización                         | Imprescindible | Entrevista con el vendedor, pregunta 4                                          |
| RF-004 | Programación de prueba de manejo                 | Imprescindible | Entrevista con el vendedor, pregunta 5                                          |
| RF-005 | Registro de seguimiento tras la prueba de manejo | Importante     | Entrevista con el vendedor, pregunta 6                                          |
| RF-006 | Actualización de la etapa de venta               | Imprescindible | Entrevista con el vendedor, pregunta 7; Visión del producto, regla de negocio 2 |
| RF-007 | Cambio de automóvil de interés                   | Importante     | Entrevista con el vendedor, pregunta 12                                         |
| RF-008 | Reactivación de cliente inactivo                 | Importante     | Entrevista con el vendedor, pregunta 11                                         |
| RF-009 | Cierre y entrega de la venta                     | Imprescindible | Visión del producto, sección 2 ("¿Qué pasa cuando se concreta una venta?")      |
| RF-010 | Consulta de estado por el gerente                | Importante     | Entrevista con el vendedor, contexto general; Visión del producto, sección 2    |
| RF-011 | Generación de reportes de venta y seguimiento    | Importante     | Visión del producto, sección 3 (alcance)                                        |
| RF-012 | Consulta de catálogo por el cliente              | Deseable       | Visión del producto, sección 3 (alcance)                                        |


**RF-001 · Registro de cliente**
| Campo                  | Contenido                                                                                                                                                                                   |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Descripción            | El sistema permite al vendedor registrar los datos de contacto de un cliente y asociarlo como su responsable de seguimiento.                                                                |
| Origen                 | Entrevista con el vendedor, preguntas 2 y 3, 15 de septiembre.                                                                                                                              |
| Prioridad              | Imprescindible                                                                                                                                                                              |
| Criterio de aceptación | Al guardar un cliente con sus datos de contacto, este aparece en la lista de clientes del vendedor que lo registró. Si falta el dato de contacto, el sistema no guarda y señala cuál falta. |
| Relacionado con        | RF-002, RNF-SEG-001                                                                                                                                                                         |

**RF-002 · Registro del automóvil de interés**
| Campo                  | Contenido                                                                                                                       |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| Descripción            | El sistema permite registrar qué automóvil (modelo) le interesa a cada cliente, y consultarlo en cualquier momento del proceso. |
| Origen                 | Entrevista con el vendedor, pregunta 3, 15 de septiembre.                                                                       |
| Prioridad              | Imprescindible                                                                                                                  |
| Criterio de aceptación | Al guardar el automóvil de interés de un cliente, este queda visible en la ficha del cliente junto con sus demás datos.         |
| Relacionado con        | RF-001, RF-007                                                                                                                  |

**RF-003 · Generación de cotización**
| Campo                  | Contenido                                                                                                                            |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| Descripción            | El sistema permite al vendedor generar una cotización para el automóvil de interés de un cliente, antes de que se concrete la venta. |
| Origen                 | Entrevista con el vendedor, pregunta 4, 15 de septiembre.                                                                            |
| Prioridad              | Imprescindible                                                                                                                       |
| Criterio de aceptación | Al generar una cotización, esta queda asociada al cliente y visible en su historial, con la fecha en que se generó.                  |
| Relacionado con        | RF-006                                                                                                                               |

**RF-004 · Programación de prueba de manejo**
| Campo                  | Contenido                                                                                                                                             |
| ---------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| Descripción            | El sistema permite al vendedor programar una prueba de manejo con un cliente para el automóvil de su interés.                                         |
| Origen                 | Entrevista con el vendedor, pregunta 5, 15 de septiembre.                                                                                             |
| Prioridad              | Imprescindible                                                                                                                                        |
| Criterio de aceptación | Al programar una prueba de manejo con fecha, esta aparece en el historial del cliente. Si no se indica fecha, el sistema no guarda y señala el error. |
| Relacionado con        | RF-005, RF-006                                                                                                                                        |

**RF-005 · Registro de seguimiento tras la prueba de manejo**
| Campo                  | Contenido                                                                                                                                               |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Descripción            | El sistema permite al vendedor registrar la opinión o comentarios del cliente después de realizada la prueba de manejo.                                 |
| Origen                 | Entrevista con el vendedor, pregunta 6, 15 de septiembre.                                                                                               |
| Prioridad              | Importante                                                                                                                                              |
| Criterio de aceptación | Al guardar un seguimiento asociado a una prueba de manejo ya registrada, este queda visible en el historial del cliente con la fecha en que se realizó. |
| Relacionado con        | RF-004, RF-007                                                                                                                                          |

**RF-006 · Actualización de la etapa de venta**
| Campo                  | Contenido                                                                                                                                                                                          |
| ---------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Descripción            | El sistema permite actualizar la etapa en la que se encuentra la venta de un cliente, siguiendo el orden establecido: interesado → cotización → prueba de manejo → negociación → apartado → venta. |
| Origen                 | Entrevista con el vendedor, pregunta 7, 15 de septiembre; Visión del producto, regla de negocio 2.                                                                                                 |
| Prioridad              | Imprescindible                                                                                                                                                                                     |
| Criterio de aceptación | Al cambiar la etapa de un cliente, el sistema no permite saltar etapas fuera de orden ni retroceder sin justificación, y el cambio queda reflejado con fecha en el historial del cliente.          |
| Relacionado con        | RF-003, RF-004, RF-008, RF-009                                                                                                                                                                     |

**RF-007 · Cambio de automóvil de interés**
| Campo                  | Contenido                                                                                                                                            |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| Descripción            | El sistema permite modificar el automóvil de interés de un cliente que cambió de opinión, sin necesidad de crear un nuevo proceso de venta.          |
| Origen                 | Entrevista con el vendedor, pregunta 12, 15 de septiembre.                                                                                           |
| Prioridad              | Importante                                                                                                                                           |
| Criterio de aceptación | Al cambiar el automóvil de interés de un cliente existente, el proceso de venta conserva su historial previo y solo se actualiza el dato del modelo. |
| Relacionado con        | RF-002                                                                                                                                               |

**RF-008 · Reactivación de cliente inactivo**
| Campo                  | Contenido                                                                                                                                                                       |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Descripción            | El sistema permite retomar el seguimiento de un cliente que dejó de responder y después vuelve a contactar, permitiendo repetir o ajustar los pasos necesarios del proceso.     |
| Origen                 | Entrevista con el vendedor, pregunta 11, 15 de septiembre.                                                                                                                      |
| Prioridad              | Importante                                                                                                                                                                      |
| Criterio de aceptación | Al marcar a un cliente inactivo como "reactivado", el sistema conserva su historial anterior y permite continuar o repetir etapas del proceso sin perder la información previa. |
| Relacionado con        | RF-006                                                                                                                                                                          |

**RF-009 · Cierre y entrega de la venta**
| Campo                  | Contenido                                                                                                                                                   |
| ---------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Descripción            | El sistema permite marcar una venta como completada una vez entregado el vehículo, y conserva su historial para consulta posterior.                         |
| Origen                 | Visión del producto, sección 2 ("¿Qué pasa cuando se concreta una venta?"); regla de negocio 3.                                                             |
| Prioridad              | Imprescindible                                                                                                                                              |
| Criterio de aceptación | Al marcar una venta como completada, esta deja de aparecer en la lista de pendientes del vendedor y queda disponible en el historial de ventas concretadas. |
| Relacionado con        | RF-006, RF-011                                                                                                                                              |

**RF-010 · Consulta de estado por el gerente**
| Campo                  | Contenido                                                                                                                                                                    |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Descripción            | El sistema permite al gerente consultar todas las ventas, la etapa del proceso de cada cliente y el avance de cada vendedor, sin depender de que se lo reporten manualmente. |
| Origen                 | Entrevista con el vendedor, contexto general; Visión del producto, sección 2.                                                                                                |
| Prioridad              | Importante                                                                                                                                                                   |
| Criterio de aceptación | Al ingresar al sistema, el gerente puede ver la lista de ventas en curso de todos los vendedores con su etapa actual, sin necesidad de solicitarla directamente a cada uno.  |
| Relacionado con        | RF-006, RF-011                                                                                                                                                               |

**RF-011 · Generación de reportes de venta y seguimiento**
| Campo                  | Contenido                                                                                                                           |
| ---------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| Descripción            | El sistema permite generar reportes sobre el estado de las ventas y el seguimiento realizado a los clientes.                        |
| Origen                 | Visión del producto, sección 3 (alcance).                                                                                           |
| Prioridad              | Importante                                                                                                                          |
| Criterio de aceptación | Al solicitar un reporte, el sistema genera un resumen con las ventas por etapa y por vendedor, correspondiente al periodo indicado. |
| Relacionado con        | RF-006, RF-010                                                                                                                      |

**RF-012 · Consulta de catálogo por el cliente**
| Campo                  | Contenido                                                                                                                                         |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| Descripción            | El sistema permite al cliente consultar el catálogo de autos disponibles de la marca y seleccionar los que le interesan.                          |
| Origen                 | Visión del producto, sección 3 (alcance); sección 2 ("¿Quién puede hacer qué?").                                                                  |
| Prioridad              | Deseable                                                                                                                                          |
| Criterio de aceptación | Al ingresar al sistema, el cliente puede ver la lista de autos disponibles y marcar uno o más como de su interés, quedando reflejado en su ficha. |
| Relacionado con        | RF-002                                                                                                                                            |

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

| Campo                      | Información                                                                                                                                                                                                                                                                                                                                                                                                 |
| -------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Actor principal**        | Vendedor                                                                                                                                                                                                                                                                                                                                                                                                    |
| **Objetivo**               | Guardar en el sistema los datos de contacto de un cliente nuevo y quedar como su vendedor responsable.                                                                                                                                                                                                                                                                                                      |
| **Precondición**           | El cliente no está registrado previamente en el sistema.                                                                                                                                                                                                                                                                                                                                                    |
| **Escenario principal**    | 1. El vendedor busca al cliente por nombre o teléfono para verificar que no exista ya.<br>2. El sistema confirma que no hay coincidencias.<br>3. El vendedor captura los datos de contacto del cliente.<br>4. El sistema guarda al cliente y lo asocia como responsable al vendedor que lo registró.<br>5. El sistema muestra la ficha del cliente recién creada, lista para continuar el proceso de venta. |
| **Flujos alternos**        | **2a.** El cliente ya existe en el sistema: el sistema muestra la ficha existente y cancela el alta duplicada.<br>**3a.** Falta un dato de contacto obligatorio: el sistema no guarda y señala cuál dato falta.                                                                                                                                                                                             |
| **Postcondición**          | El cliente queda registrado y visible en la lista de clientes del vendedor.                                                                                                                                                                                                                                                                                                                                 |
| **Requisitos que realiza** | RF-001, RNF-USA-001, RNF-SEG-001                                                                                                                                                                                                                                                                                                                                                                            |

---

### CU-02 · Generar una cotización

| Campo                      | Información                                                                                                                                                                                                                                                                                                                               |
| -------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Actor principal**        | Vendedor                                                                                                                                                                                                                                                                                                                                  |
| **Objetivo**               | Entregar al cliente una cotización formal del automóvil de su interés.                                                                                                                                                                                                                                                                    |
| **Precondición**           | El cliente está registrado y tiene un automóvil de interés asignado.                                                                                                                                                                                                                                                                      |
| **Escenario principal**    | 1. El vendedor abre la ficha del cliente.<br>2. El sistema muestra el automóvil de interés registrado.<br>3. El vendedor solicita generar la cotización.<br>4. El sistema calcula y genera la cotización con el modelo, precio y condiciones vigentes.<br>5. El sistema la asocia al historial del cliente con la fecha en que se generó. |
| **Flujos alternos**        | **2a.** El cliente aún no tiene automóvil de interés registrado: el sistema pide asignarlo antes de continuar (enlaza con RF-002).<br>**4a.** El automóvil no tiene precio o condiciones vigentes cargadas: el sistema no genera la cotización y lo señala al vendedor.                                                                   |
| **Postcondición**          | La cotización queda registrada en el historial del cliente y disponible para consulta posterior.                                                                                                                                                                                                                                          |
| **Requisitos que realiza** | RF-002, RF-003                                                                                                                                                                                                                                                                                                                            |

---

### CU-03 · Programar una prueba de manejo

| Campo                      | Información                                                                                                                                                                                                                                                                                                                     |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Actor principal**        | Vendedor                                                                                                                                                                                                                                                                                                                        |
| **Objetivo**               | Reservar una prueba de manejo del automóvil de interés para un cliente en una fecha determinada.                                                                                                                                                                                                                                |
| **Precondición**           | El cliente está registrado y tiene un automóvil de interés asignado.                                                                                                                                                                                                                                                            |
| **Escenario principal**    | 1. El vendedor abre la ficha del cliente y selecciona programar una prueba de manejo.<br>2. El sistema muestra el automóvil de interés del cliente.<br>3. El vendedor elige fecha y hora para la prueba.<br>4. El sistema registra la prueba de manejo con esos datos.<br>5. El sistema la muestra en el historial del cliente. |
| **Flujos alternos**        | **3a.** No se indica fecha u hora: el sistema no guarda y señala el dato faltante.<br>**4a.** El cliente ya tiene una prueba de manejo pendiente sin realizar: el sistema advierte al vendedor y pregunta si desea reprogramarla o agregar una nueva.                                                                           |
| **Postcondición**          | La prueba de manejo queda registrada y visible en el historial del cliente.                                                                                                                                                                                                                                                     |
| **Requisitos que realiza** | RF-004                                                                                                                                                                                                                                                                                                                          |

---

### CU-04 · Actualizar la etapa de venta de un cliente

| Campo                      | Información                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| -------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Actor principal**        | Vendedor                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| **Objetivo**               | Reflejar en el sistema el avance real de un cliente dentro del proceso de venta, de modo que tanto el vendedor como el gerente sepan en qué parte se encuentra sin tener que preguntarlo.                                                                                                                                                                                                                                                                                                                                                                                                                            |
| **Precondición**           | El cliente ya está registrado y tiene una etapa asignada (la etapa inicial es "interesado").                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| **Escenario principal**    | 1. El vendedor busca al cliente por nombre o teléfono.<br>2. El sistema muestra la ficha del cliente, incluyendo su etapa actual y el historial de avance.<br>3. El vendedor selecciona la nueva etapa a la que quiere mover al cliente.<br>4. El sistema verifica que la nueva etapa sea la siguiente en el orden establecido (interesado → cotización → prueba de manejo → negociación → apartado → venta).<br>5. El sistema registra el cambio de etapa con fecha y lo agrega al historial del cliente.<br>6. El sistema muestra la ficha actualizada del cliente con su nueva etapa.                             |
| **Flujos alternos**        | **4a.** El vendedor intenta saltar una etapa: el sistema no permite el cambio y muestra cuál es la siguiente etapa válida.<br>**4b.** El vendedor intenta retroceder una etapa: el sistema permite el retroceso, pero pide un motivo breve, el cual queda registrado en el historial.<br>**4c.** El cliente estaba marcado como inactivo: antes de avanzar la etapa, el sistema sugiere confirmar primero si el cliente sigue interesado en el mismo automóvil (enlaza con CU-05).<br>**4d.** El cliente ya tiene una venta cerrada: el sistema no permite modificar la etapa; solo se puede consultar su historial. |
| **Postcondición**          | La etapa del cliente queda actualizada y visible tanto en la ficha del vendedor como en el panel del gerente, con la fecha del cambio registrada en el historial.                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| **Requisitos que realiza** | RF-006, RF-008, RF-009, RNF-SEG-001                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |

---

### CU-05 · Reactivar el seguimiento de un cliente inactivo

| Campo                      | Información                                                                                                                                                                                                                                                                                                                                                                                                                 |
| -------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Actor principal**        | Vendedor                                                                                                                                                                                                                                                                                                                                                                                                                    |
| **Objetivo**               | Retomar el proceso de un cliente que dejó de responder y después volvió a contactar, sin perder la información previa.                                                                                                                                                                                                                                                                                                      |
| **Precondición**           | El cliente existe en el sistema y está marcado como inactivo.                                                                                                                                                                                                                                                                                                                                                               |
| **Escenario principal**    | 1. El vendedor busca al cliente que volvió a contactar.<br>2. El sistema muestra la ficha del cliente marcada como inactiva, junto con su última etapa registrada.<br>3. El vendedor confirma que el cliente sigue interesado en el mismo automóvil.<br>4. El sistema marca al cliente como reactivado y continúa el proceso desde la última etapa registrada.<br>5. El sistema conserva el historial anterior del cliente. |
| **Flujos alternos**        | **3a.** El cliente cambió de automóvil de interés: el vendedor actualiza el modelo antes de continuar (enlaza con RF-007).<br>**3b.** El cliente ya no está interesado en comprar: el vendedor marca la venta como perdida y el sistema conserva el historial sin reactivar el proceso.                                                                                                                                     |
| **Postcondición**          | El cliente queda reactivado y su proceso de venta continúa visible en la lista de pendientes del vendedor, sin perder el historial previo.                                                                                                                                                                                                                                                                                  |
| **Requisitos que realiza** | RF-007, RF-008                                                                                                                                                                                                                                                                                                                                                                                                              |

---

### CU-06 · Consultar el avance de ventas de la agencia

| Campo                      | Información                                                                                                                                                                                                                                                                                                                                                                              |
| -------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Actor principal**        | Gerente                                                                                                                                                                                                                                                                                                                                                                                  |
| **Objetivo**               | Conocer el estado de todas las ventas en curso y el avance de cada vendedor sin tener que pedírselo directamente a cada uno.                                                                                                                                                                                                                                                             |
| **Precondición**           | Existen clientes y ventas registradas en el sistema.                                                                                                                                                                                                                                                                                                                                     |
| **Escenario principal**    | 1. El gerente ingresa al sistema y accede al panel de ventas.<br>2. El sistema muestra la lista de ventas en curso de todos los vendedores con su etapa actual.<br>3. El gerente filtra por vendedor, etapa o rango de fechas si lo necesita.<br>4. El sistema actualiza la lista según el filtro aplicado.<br>5. El gerente consulta el detalle de una venta específica si lo requiere. |
| **Flujos alternos**        | **3a.** No hay ventas que cumplan el filtro aplicado: el sistema muestra un mensaje indicando que no hay resultados.<br>**5a.** El gerente detecta una venta sin actividad reciente: el sistema le permite marcarla para dar seguimiento o notificar al vendedor responsable.                                                                                                            |
| **Postcondición**          | El gerente obtiene una visión actualizada del estado de las ventas sin depender de reportes manuales de los vendedores.                                                                                                                                                                                                                                                                  |
| **Requisitos que realiza** | RF-010, RF-011, RNF-REN-001                                                                                                                                                                                                                                                                                                                                                              |

---

### CU-07 · Consultar el catálogo y el proceso de compra

| Campo                      | Información                                                                                                                                                                                                                                                                                                                       |
| -------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Actor principal**        | Cliente                                                                                                                                                                                                                                                                                                                           |
| **Objetivo**               | Ver los automóviles disponibles de la agencia y revisar en qué parte de su proceso de compra se encuentra.                                                                                                                                                                                                                        |
| **Precondición**           | El cliente tiene acceso al sistema (ya sea registrado por un vendedor o con cuenta propia).                                                                                                                                                                                                                                       |
| **Escenario principal**    | 1. El cliente ingresa al sistema.<br>2. El sistema muestra el catálogo de automóviles disponibles de la agencia y de la marca.<br>3. El cliente selecciona uno o más automóviles de su interés.<br>4. El sistema guarda la selección en la ficha del cliente.<br>5. El cliente consulta el estado actual de su proceso de compra. |
| **Flujos alternos**        | **3a.** El cliente ya tiene un automóvil de interés registrado por el vendedor: el sistema le pregunta si desea mantenerlo o cambiarlo.<br>**5a.** El cliente aún no tiene un proceso de compra iniciado: el sistema muestra un mensaje indicando que debe contactar a un vendedor para comenzar.                                 |
| **Postcondición**          | El cliente conoce los automóviles disponibles y el estado de su propio proceso de compra, sin necesidad de contactar directamente al vendedor para esa información.                                                                                                                                                               |
| **Requisitos que realiza** | RF-012                                                                                                                                                                                                                                                                                                                            |

---

### CU-08 · Cerrar y entregar una venta

| Campo                      | Información                                                                                                                                                                                                                                                                                                                                                                            |
| -------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Actor principal**        | Vendedor                                                                                                                                                                                                                                                                                                                                                                               |
| **Objetivo**               | Marcar una venta como completada una vez que el vehículo fue entregado al cliente, conservando su historial.                                                                                                                                                                                                                                                                           |
| **Precondición**           | El cliente se encuentra en la etapa "apartado" o "venta" y el vehículo está listo para entrega.                                                                                                                                                                                                                                                                                        |
| **Escenario principal**    | 1. El vendedor abre la ficha del cliente cuya venta está por cerrarse.<br>2. El sistema muestra la etapa actual y el resumen del proceso de venta.<br>3. El vendedor confirma la entrega del vehículo.<br>4. El sistema marca la venta como completada y registra la fecha de entrega.<br>5. El sistema mueve al cliente del listado de pendientes al historial de ventas concretadas. |
| **Flujos alternos**        | **3a.** El vehículo aún no está disponible para entrega: el sistema no permite cerrar la venta y muestra la fecha estimada de disponibilidad.<br>**4a.** Falta información obligatoria del canal de venta (financiamiento o contado): el sistema no cierra la venta hasta que ese dato se complete.                                                                                    |
| **Postcondición**          | La venta queda marcada como completada, deja de aparecer en pendientes y su historial queda disponible para consulta del vendedor y del gerente.                                                                                                                                                                                                                                       |
| **Requisitos que realiza** | RF-006, RF-009, RF-011                                                                                                                                                                                                                                                                                                                                                                 |




## 6. Trazabilidad


| Requisito   | Origen                                                                 | Caso de uso                                                                                           | Elemento del prototipo                                               |
| ----------- | ---------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------- |
| RF-001      | Entrevista 15 sep, preguntas 2 y 3                                     | CU-01 Registrar un cliente nuevo                                                                      | Pantalla "Nuevo cliente"                                             |
| RF-002      | Entrevista 15 sep, pregunta 3                                          | CU-01 Registrar un cliente nuevo                                                                      | Pantalla "Nuevo cliente" (campo automóvil de interés)                |
| RF-003      | Entrevista 15 sep, pregunta 4                                          | CU-02 Generar una cotización                                                                          | Pantalla "Cotización"                                                |
| RF-004      | Entrevista 15 sep, pregunta 5                                          | CU-03 Programar una prueba de manejo                                                                  | Pantalla "Agendar prueba de manejo"                                  |
| RF-005      | Entrevista 15 sep, pregunta 6                                          | CU-03 Programar una prueba de manejo (flujo posterior)                                                | Pantalla "Ficha del cliente" (sección seguimiento)                   |
| RF-006      | Entrevista 15 sep, pregunta 7; Visión del producto, regla de negocio 2 | CU-04 Actualizar la etapa de venta / CU-08 Cerrar y entregar una venta                                | Pantalla "Ficha del cliente" (selector de etapa)                     |
| RF-007      | Entrevista 15 sep, pregunta 12                                         | CU-05 Reactivar el seguimiento de un cliente inactivo                                                 | Pantalla "Ficha del cliente" (campo automóvil de interés, editable)  |
| RF-008      | Entrevista 15 sep, pregunta 11                                         | CU-04 Actualizar la etapa de venta (flujo 4c) / CU-05 Reactivar el seguimiento de un cliente inactivo | Pantalla "Ficha del cliente" (etiqueta "inactivo" y botón reactivar) |
| RF-009      | Visión del producto, sección 2 y regla de negocio 3                    | CU-04 Actualizar la etapa de venta (flujo 4d) / CU-08 Cerrar y entregar una venta                     | Pantalla "Cierre de venta"                                           |
| RF-010      | Entrevista 15 sep, contexto general; Visión del producto, sección 2    | CU-06 Consultar el avance de ventas de la agencia                                                     | Panel "Ventas de la agencia" (vista gerente)                         |
| RF-011      | Visión del producto, sección 3 (alcance)                               | CU-06 Consultar el avance de ventas de la agencia / CU-08 Cerrar y entregar una venta                 | Panel "Reportes"                                                     |
| RF-012      | Visión del producto, sección 3 (alcance) y sección 2                   | CU-07 Consultar el catálogo y el proceso de compra                                                    | Pantalla "Catálogo" (vista cliente)                                  |
| RNF-REN-001 | Derivado del tipo de sistema; entrevista, pregunta 9                   | CU-01, CU-06                                                                                          | Pantalla "Ficha del cliente" / Panel "Ventas de la agencia"          |
| RNF-SEG-001 | Visión del producto, sección 4                                         | CU-01, CU-04, CU-06                                                                                   | Control de acceso por rol (login)                                    |
| RNF-USA-001 | Entrevista 15 sep, pregunta 9; Visión del producto, sección 4          | CU-01 Registrar un cliente nuevo                                                                      | Pantalla "Nuevo cliente"                                             |
| RNF-DIS-001 | Visión del producto, sección 4                                         | CU-04, CU-05                                                                                          | Infraestructura del sistema (no es una pantalla)                     |



## 7. Registro de cambios

| Fecha       | Requisito          | Qué cambió                                                    | Por qué                                                                                                              |
| ----------- | ------------------ | ------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| 20 sep 2026 | RF-005             | Prioridad cambió de "Importante" a "Imprescindible"           | El gerente indicó que el seguimiento post-prueba de manejo es indispensable para no perder ventas, no solo deseable. |
| 22 sep 2026 | RF-013 (eliminado) | Se eliminó el requisito de envío de recordatorios automáticos | Estaba fuera del alcance definido en la Visión del producto; se agregó por error en una revisión anterior.           |
| 25 sep 2026 | RF-014             | Nuevo requisito: exportar la ficha de un cliente a PDF        | Solicitado por el gerente durante la revisión del prototipo.                                                         |


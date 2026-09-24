# Especificación de requisitos

#### **Sistema:** AutoTrack
#### **Autor:** Ana Camila López Sánchez
#### **Fecha de la última actualización:** 


## 1. Propósito y alcance

**Propósito del documento:** El propósito de este documento es definir las características, usuarios, necesidades y límites del sistema AutoTrack, así como establecer los requisitos que deberá cumplir para apoyar el seguimiento del proceso de venta de automóviles.

**Alcance del sistema:** AutoTrack será un sistema para gestionar y dar seguimiento al proceso de venta de automóviles. Permitirá registrar clientes, vendedores y gerentes, así como consultar y actualizar el avance de cada cliente en las diferentes etapas del proceso: interesado, cotización, prueba de manejo, negociación y venta.

**Fuera del alcance:** El sistema no realizará pagos, facturación, contabilidad, inventario de vehículos ni procesos administrativos externos a la gestión y seguimiento de las ventas.

## 2. Usuarios y su contexto

| Usuario | Qué hace hoy sin el sistema | Qué espera del sistema |
|---|---|---|
| **Vendedor** | Da seguimiento a los clientes mediante mensajes, llamadas, notas o registros separados. Puede perder información sobre el avance de una venta. | Registrar clientes, consultar su información y actualizar fácilmente la etapa en la que se encuentra cada venta. |
| **Gerente** | Supervisa las ventas y consulta el avance de los vendedores mediante información que puede estar dispersa. | Consultar el progreso de las ventas y tener una visión general de los clientes y operaciones en curso. |
| **Cliente** | Se comunica con el vendedor para recibir información, cotizaciones y dar seguimiento a su proceso de compra. | Recibir un seguimiento organizado y que su información y avance en el proceso de compra estén correctamente registrados. |

**Conflictos identificados entre usuarios:** El principal conflicto puede surgir entre vendedores y gerentes, ya que el vendedor necesita actualizar y gestionar la información de sus clientes de manera rápida, mientras que el gerente necesita tener acceso a información suficiente para supervisar el avance de las ventas. El sistema debe permitir ambas necesidades sin hacer que el registro de información sea complicado para el vendedor.

## 3. Requisitos funcionales

**3.1 Resumen**
| ID | Nombre | Prioridad | Origen |
|---|---|---|---|
| RF-001 | Registrar cliente | Imprescindible | Entrevista con el vendedor |
| RF-002 | Registrar seguimiento de venta | Imprescindible | Entrevista con el vendedor |
| RF-003 | Actualizar etapa de venta | Imprescindible | Entrevista con el vendedor |
| RF-004 | Consultar información del cliente | Importante | Entrevista con el vendedor |
| RF-005 | Consultar avance de ventas | Importante | Entrevista con el vendedor |

RF-001 · Registrar cliente
| Campo | Contenido |
|---|---|
| **Descripción** | El sistema permite al vendedor registrar un cliente con sus datos básicos y la información del vehículo de interés. |
| **Origen** | Entrevista con el vendedor. |
| **Prioridad** | Imprescindible |
| **Criterio de aceptación** | Al guardar un cliente con los datos obligatorios, este aparece en el sistema con su información correctamente registrada. Si falta un dato obligatorio, el sistema indica cuál falta y no permite guardar el registro. |
| **Relacionado con** | RF-002, RF-004 |

RF-002 · Registrar seguimiento de venta
| Campo | Contenido |
|---|---|
| **Descripción** | El sistema permite registrar el seguimiento realizado a un cliente durante su proceso de compra. |
| **Origen** | Entrevista con el vendedor. |
| **Prioridad** | Imprescindible |
| **Criterio de aceptación** | Al registrar una actividad de seguimiento, esta queda asociada al cliente correspondiente y puede consultarse posteriormente. |
| **Relacionado con** | RF-001, RF-003 |

RF-003 · Actualizar etapa de venta
| Campo | Contenido |
|---|---|
| **Descripción** | El sistema permite actualizar la etapa en la que se encuentra cada cliente: interesado, cotización, prueba de manejo, negociación o venta. |
| **Origen** | Entrevista con el vendedor. |
| **Prioridad** | Imprescindible |
| **Criterio de aceptación** | Al cambiar la etapa de un cliente, el sistema guarda el nuevo estado y lo muestra correctamente al consultar su información. |
| **Relacionado con** | RF-002, RF-005 |

RF-004 · Consultar información del cliente
| Campo | Contenido |
|---|---|
| **Descripción** | El sistema permite al vendedor consultar los datos y el historial de seguimiento de un cliente registrado. |
| **Origen** | Entrevista con el vendedor. |
| **Prioridad** | Importante |
| **Criterio de aceptación** | Al buscar un cliente registrado, el sistema muestra sus datos, vehículo de interés, etapa actual y seguimiento realizado. |
| **Relacionado con** | RF-001, RF-002, RF-003 |

RF-005 · Consultar avance de ventas
| Campo | Contenido |
|---|---|
| **Descripción** | El sistema permite al gerente consultar el avance de las ventas y conocer en qué etapa se encuentran los clientes. |
| **Origen** | Entrevista con el gerente. |
| **Prioridad** | Importante |
| **Criterio de aceptación** | Al consultar el avance de ventas, el gerente puede visualizar los clientes registrados y la etapa actual de cada proceso de venta. |
| **Relacionado con** | RF-003, RF-004 |

## 4. Requisitos no funcionales

**4.1 Resumen**
| ID | Atributo | Nombre | Prioridad | Origen |
|---|---|---|---|---|
| RNF-REN-001 | Rendimiento | Tiempo de consulta de clientes | Importante | Derivado del tipo de sistema |
| RNF-SEG-001 | Seguridad | Protección de información | Imprescindible | Derivado de la información manejada |
| RNF-USA-001 | Usabilidad | Facilidad de registro | Imprescindible | Entrevista con el vendedor |

**4.2 Fichas**
RNF-REN-001 · Tiempo de consulta de clientes
| Campo | Contenido |
|---|---|
| **Atributo de calidad** | Rendimiento |
| **Descripción** | La información de un cliente registrado debe mostrarse en un máximo de tres segundos después de realizar una consulta. |
| **Métrica** | Tiempo entre la solicitud de consulta y la visualización completa de la información del cliente, medido con hasta 500 clientes registrados. |
| **Origen** | Derivado del tipo de sistema: de información, utilizado para consultar y actualizar datos durante el proceso de venta. |
| **Prioridad** | Importante |
| **Por qué importa** | El vendedor necesita consultar rápidamente la información de los clientes para dar seguimiento a las ventas sin perder tiempo. |
| **Afecta a** | RF-001, RF-004, RF-005 |

RNF-SEG-001 · Protección de información
| Campo | Contenido |
|---|---|
| **Atributo de calidad** | Seguridad |
| **Descripción** | El sistema debe restringir el acceso a la información de clientes y ventas de acuerdo con el tipo de usuario. |
| **Métrica** | Un usuario sin los permisos correspondientes no puede consultar ni modificar información restringida. |
| **Origen** | Derivado de la información de clientes y ventas que maneja el sistema. |
| **Prioridad** | Imprescindible |
| **Por qué importa** | AutoTrack manejará datos de clientes y operaciones de venta que deben estar protegidos y disponibles únicamente para los usuarios autorizados. |
| **Afecta a** | RF-001, RF-004, RF-005 |

RNF-USA-001 · Facilidad de registro
| Campo | Contenido |
|---|---|
| **Atributo de calidad** | Usabilidad |
| **Descripción** | El registro y actualización de información de un cliente debe poder realizarse de forma clara y sencilla. |
| **Métrica** | Un vendedor que conozca el proceso de venta debe poder registrar un cliente nuevo en un máximo de tres minutos sin recibir ayuda externa. |
| **Origen** | Entrevista con el vendedor. |
| **Prioridad** | Imprescindible |
| **Por qué importa** | El vendedor necesita registrar y actualizar información sin que el sistema interrumpa o complique el seguimiento de sus clientes. |
| **Afecta a** | RF-001, RF-002, RF-003 |

## 5. Casos de uso

### CU-001 · Registrar cliente

| Campo | Contenido |
|---|---|
| **Actor principal** | Vendedor |
| **Objetivo** | Registrar los datos de un nuevo cliente y su vehículo de interés para iniciar el seguimiento de la venta. |
| **Precondición** | El vendedor tiene acceso al sistema. |
| **Escenario principal** | 1. El vendedor selecciona la opción para registrar un cliente.<br>2. El sistema muestra el formulario de registro.<br>3. El vendedor captura los datos del cliente y del vehículo de interés.<br>4. El sistema verifica que los datos obligatorios estén completos.<br>5. El sistema registra al cliente y lo muestra en la lista de clientes. |
| **Flujos alternos** | **3a. El cliente ya está registrado:** el sistema muestra el registro existente para evitar duplicarlo.<br>**4a. Falta un dato obligatorio:** el sistema indica qué dato falta y solicita completarlo.<br>**4b. Los datos ingresados no son válidos:** el sistema señala el dato incorrecto y permite corregirlo. |
| **Postcondición** | El cliente queda registrado en AutoTrack y disponible para darle seguimiento. |
| **Requisitos que realiza** | RF-001, RNF-USA-001 |

### CU-002 · Registrar seguimiento de venta

| Campo | Contenido |
|---|---|
| **Actor principal** | Vendedor |
| **Objetivo** | Registrar las actividades realizadas con un cliente durante el proceso de venta. |
| **Precondición** | El cliente ya está registrado en el sistema. |
| **Escenario principal** | 1. El vendedor busca al cliente.<br>2. El sistema muestra la información del cliente y su etapa actual.<br>3. El vendedor selecciona registrar seguimiento.<br>4. El vendedor captura la información de la actividad realizada.<br>5. El sistema registra el seguimiento y lo asocia al cliente. |
| **Flujos alternos** | **1a. El cliente no existe:** el sistema informa que no se encontró y permite realizar una nueva búsqueda.<br>**4a. Falta información del seguimiento:** el sistema indica el dato que falta y solicita completarlo.<br>**4b. El vendedor cancela el registro:** el sistema no guarda la actividad y regresa a la información del cliente. |
| **Postcondición** | El seguimiento queda registrado en el historial del cliente. |
| **Requisitos que realiza** | RF-002, RF-004 |

### CU-003 · Actualizar etapa de venta

| Campo | Contenido |
|---|---|
| **Actor principal** | Vendedor |
| **Objetivo** | Actualizar la etapa en la que se encuentra un cliente dentro del proceso de venta. |
| **Precondición** | El cliente ya está registrado en el sistema. |
| **Escenario principal** | 1. El vendedor busca al cliente.<br>2. El sistema muestra la etapa actual del proceso.<br>3. El vendedor selecciona una nueva etapa.<br>4. El sistema muestra las etapas disponibles: interesado, cotización, prueba de manejo, negociación y venta.<br>5. El vendedor selecciona la nueva etapa.<br>6. El sistema actualiza y guarda la etapa del cliente. |
| **Flujos alternos** | **1a. El cliente no existe:** el sistema informa que no se encontró el registro.<br>**5a. El vendedor cancela el cambio:** el sistema conserva la etapa anterior.<br>**5b. La etapa seleccionada no es válida:** el sistema solicita seleccionar una etapa disponible. |
| **Postcondición** | La nueva etapa queda registrada y visible en la información del cliente. |
| **Requisitos que realiza** | RF-003, RNF-USA-001 |

### CU-004 · Consultar información del cliente

| Campo | Contenido |
|---|---|
| **Actor principal** | Vendedor |
| **Objetivo** | Consultar los datos, vehículo de interés, etapa y seguimiento de un cliente. |
| **Precondición** | El cliente está registrado en el sistema. |
| **Escenario principal** | 1. El vendedor busca al cliente por sus datos.<br>2. El sistema muestra los clientes que coinciden con la búsqueda.<br>3. El vendedor selecciona al cliente.<br>4. El sistema muestra sus datos, vehículo de interés, etapa actual e historial de seguimiento. |
| **Flujos alternos** | **1a. No se encuentra el cliente:** el sistema muestra un mensaje indicando que no hay coincidencias.<br>**2a. Existen varios clientes con información similar:** el sistema muestra los resultados para que el vendedor seleccione el correcto. |
| **Postcondición** | El vendedor puede consultar la información actualizada del cliente. |
| **Requisitos que realiza** | RF-004, RNF-REN-001 |

### CU-005 · Consultar avance de ventas

| Campo | Contenido |
|---|---|
| **Actor principal** | Gerente |
| **Objetivo** | Consultar el avance de los clientes dentro del proceso de venta. |
| **Precondición** | El gerente tiene acceso al sistema y existen clientes registrados. |
| **Escenario principal** | 1. El gerente ingresa a la sección de avance de ventas.<br>2. El sistema muestra los clientes registrados y su etapa actual.<br>3. El gerente consulta la información de las ventas en proceso.<br>4. El sistema muestra la información actualizada de cada cliente. |
| **Flujos alternos** | **2a. No existen clientes registrados:** el sistema muestra un mensaje indicando que no hay ventas para consultar.<br>**2b. El gerente busca una venta específica:** el sistema muestra los resultados que coinciden con la búsqueda.<br>**4a. El gerente no tiene permisos para consultar cierta información:** el sistema restringe el acceso y muestra un mensaje. |
| **Postcondición** | El gerente obtiene una vista actualizada del avance de las ventas. |
| **Requisitos que realiza** | RF-005, RNF-SEG-001, RNF-REN-001 |



## 6. Trazabilidad


| Requisito | Origen | Caso de uso | Elemento del prototipo |
|---|---|---|---|
| RF-001 Registrar cliente | Entrevista con el vendedor | CU-01 Registrar cliente | Pantalla de registro de cliente |
| RF-002 Registrar seguimiento de venta | Entrevista con el vendedor | CU-02 Registrar seguimiento de venta | Pantalla de seguimiento |
| RF-003 Actualizar etapa de venta | Entrevista con el vendedor | CU-03 Actualizar etapa de venta | Pantalla de seguimiento |
| RF-004 Consultar información del cliente | Entrevista con el vendedor | CU-04 Consultar información del cliente | Pantalla de clientes |
| RF-005 Consultar avance de ventas | Entrevista con el gerente | CU-05 Consultar avance de ventas | Pantalla de avance de ventas |


## 7. Registro de cambios

| Fecha | Requisito | Qué cambió | Por qué |
|---|---|---|---|
| 22 sep 2026 | RF-001 a RF-005 | Se establecieron los cinco requisitos funcionales iniciales | Se definió el alcance del sistema a partir de las entrevistas con el vendedor y el gerente |

# Especificación de requisitos

#### **Sistema:** AutoTrack
#### **Autor:** Ana Camila López Sánchez
#### **Fecha de la última actualización:** 


## 1. Propósito y alcance

**Propósito del documento:** Definir las características, usuarios, necesidades y límites del sistema AutoTrack, para establecer claramente qué debe hacer el sistema y qué problemas busca resolver.

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
| RF-005 | Consultar avance de ventas | Importante | Entrevista con el gerente |

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

## 5. Casos de uso
Se trabajan en la semana 7, después de la entrevista. Cada caso de uso se relaciona con los requisitos funcionales que realiza.

## 6. Trazabilidad
Esta tabla es la que hace posible el análisis de impacto de la semana 15. Mantenla actualizada conforme cambien los requisitos.

Requisito	Origen	Caso de uso	Elemento del prototipo
RF-001	Entrevista 15 sep	CU-01 Registrar consulta	Pantalla de consulta

## 7. Registro de cambios
Cada modificación posterior a la primera versión se anota aquí. Un requisito eliminado se marca como tal, pero su identificador no se reutiliza.

Fecha	Requisito	Qué cambió	Por qué

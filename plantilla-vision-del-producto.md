# Visión del producto

---

**Autor: Ana Camila Lopez Sanchez**
**Fecha de la última versión: 1 de septiembre de 2026**
**Repositorio: AutoTrack**

---

## 1. Descripción del sistema


**Nombre: AutoTrack** 

**Descripción:** 

AutoTrack es un sistema que ayuda a una agencia de autos a organizar y dar seguimiento a las oportunidades de venta. Permite a los vendedores registrar la información de sus clientes, identificar qué vehículos les interesan, conocer en qué parte del proceso de compra se encuentran y saber cuándo deben volver a contactarlos. De esta manera, la agencia puede mantener la información organizada y evitar que se pierdan clientes por olvidar datos o seguimientos importantes.

---

## 2. Problema y usuarios


**El problema:** En una agencia de autos, un vendedor puede atender a varios clientes al mismo tiempo y cada uno puede estar interesado en diferentes vehículos y encontrarse en una etapa distinta de compra. Cuando la información no está organizada, es fácil olvidar contactar a un cliente, perder datos sobre sus intereses o no saber qué seguimiento corresponde realizar. Esto puede provocar que se pierdan oportunidades de venta y que los clientes reciban una atención poco organizada.

**Cómo se resuelve hoy sin el sistema:** Actualmente, los vendedores suelen guardar la información de sus clientes en conversaciones de WhatsApp, llamadas, notas, hojas de cálculo o incluso confiando en su memoria. El gerente puede solicitar actualizaciones directamente a los vendedores para conocer cómo van las ventas. Esto hace que la información esté distribuida en diferentes lugares y que sea difícil saber rápidamente qué clientes necesitan atención y cuál es el estado de cada posible venta.

**Usuarios del sistema:** 

| Tipo de usuario | Qué necesita del sistema | Qué le preocupa |
|---|---|---|
| Cliente | Consultar autos y recibir seguimiento de su compra.  | Recibir información incorrecta o demasiados mensajes.  |
| Vendedor | Organizar clientes y dar seguimiento a las ventas.  | Perder una venta.  |
| Gerente | Revisar el avance de las ventas.  | No tener información actualizada.  |



**Un conflicto entre usuarios:** El vendedor quiere contactar al cliente para aumentar las posibilidades de concretar una venta, mientras que el cliente puede preferir recibir únicamente información importante y no ser contactado constantemente. Por lo tanto, el sistema tendrá que encontrar un equilibrio entre permitir que el vendedor trabaje rápidamente y establecer la información mínima que todos deben registrar.

**Huecos importantes:** 

¿Quién puede hacer qué?
<li>Cliente: Puede entrar al sistema, consultar los autos disponibles, seleccionar los que le interesan y revisar el estado de su proceso de compra.</li>
<li>Vendedor: Registra clientes, autos de interés, cotizaciones y actualiza el avance de cada venta. Solo puede modificar la información de sus clientes.</li>
<li>Gerente: Puede consultar todas las ventas y clientes, supervisar a los vendedores y modificar información cuando sea necesario.</li>


¿Qué pasa cuando se concreta una venta?
<li>La venta se marca como completada: El cliente pasa de estar en proceso a tener una venta finalizada.</li>
<li>Deja de aparecer en pendientes: Ya no necesita seguimientos de venta y deja de aparecer entre los clientes pendientes.</li>
<li>Se guarda el historial: La información de la venta queda registrada para que el vendedor y el gerente puedan consultarla posteriormente.</li>


---

## 3. Alcance


### Dentro del alcance

- Registrar clientes y su información de contacto
- Registrar los automóviles disponibles en la agencia y el automóvil de interés de cada cliente
- Actualizar el estado de cada venta (interesado, cotización, apartado, venta, etc.)
- Registrar el seguimiento de la venta de los clientes
- Guardar las ventas concretadas para que el asesor de ventas y el gerente puedan tener acceso a ellas

### Explícitamente fuera del alcance

- No procesará pagos ni generará contratos de compra.
- No enviará mensajes automáticos por WhatsApp, SMS o correo electrónico.
- No permitirá realizar la compra del automóvil directamente desde el sistema.

**Por qué queda fuera:** El envío automático de mensajes queda fuera porque requeriría integrar servicios externos de mensajería y aumentaría la complejidad del proyecto. AutoTrack solamente indicará al vendedor cuándo debe realizar un seguimiento.


---

## 4. Tipo de sistema y restricciones


**Tipo de sistema:** Sistema de información


**Por qué es de ese tipo:** AutoTrack almacena y organiza información de clientes, automóviles y ventas para facilitar el seguimiento y la consulta de datos por parte de vendedores y gerentes.

**Atributos de calidad que impone:**

| Atributo | Por qué importa en mi caso | Qué pasa si no se cumple |
|---|---|---|
| Seguridad | Protege los datos de clientes y ventas | Personas no autorizadas podrían acceder a información |
| Disponibilidad | Vendedores y gerentes necesitan consultar el sistema cuando trabajan | Se podrían perder seguimientos u oportunidades de venta |
| Usabilidad | Los vendedores deben poder registrar información fácilmente | Podrían cometer errores o dejar de registrar datos |

**Reglas de negocio que ya identifiqué:**


1. Cada cliente debe tener un vendedor responsable de su seguimiento.
2. Una venta debe avanzar por las etapas establecidas en orden: interesado → cotización → prueba de manejo → negociación → apartado → venta.
3. Cuando una venta se concreta, debe marcarse como completada y conservar su historial.

---

## 5. Ciclo de vida elegido

*Instrucción: este apartado se trabaja en la semana 3, después de ver los modelos de desarrollo. La justificación pesa más que la elección: no hay un modelo correcto, hay uno defendible para tu caso.*

**Modelo elegido:** Prototipado rápido

**Por qué le conviene a este proyecto:** AutoTrack tiene tres tipos de usuarios con necesidades diferentes: cliente, vendedor y gerente. Algunas de estas necesidades pueden ser difíciles de definir únicamente con explicaciones, por lo que crear un prototipo nos permitirá mostrar cómo funcionaría el sistema, recibir comentarios de los usuarios y realizar cambios antes de desarrollar el sistema completo.

### Alternativas descartadas

**Alternativa 1:** Cascada

*Por qué la descarté:* Requiere que los requisitos estén definidos y sean estables desde el inicio. En AutoTrack pueden surgir cambios al mostrar el sistema a los usuarios y conocer mejor sus necesidades.

**Alternativa 2:** Espiral

*Por qué la descarté:* Está pensado para proyectos grandes y con un nivel alto de riesgo técnico. AutoTrack es un proyecto de menor tamaño y no necesita realizar un análisis de riesgos en cada ciclo.

---

## Antes de entregar

Reviso que el documento cumpla lo siguiente:

[ ] La descripción del apartado 1 se entiende sin ser del área
[ ] Hay al menos dos tipos de usuario con necesidades distintas
[ ] Identifiqué un conflicto real entre usuarios
[ ] El alcance dice qué queda fuera, no solo qué queda dentro
[ ] Las exclusiones son específicas, no genéricas
[ ] Identifiqué el tipo de sistema y al menos dos atributos de calidad
[ ] Anoté al menos tres reglas de negocio no obvias
[ ✓ ] Justifiqué el ciclo de vida contra dos alternativas descartadas
[ ✓ ] El documento está en mi repositorio y se puede leer desde el navegador
[ ✓ ] Borré todas las instrucciones en cursiva de la plantilla

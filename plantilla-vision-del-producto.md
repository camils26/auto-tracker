# Visión del producto

> **Plantilla del curso · Ingeniería de Software I · SIS3407**
> Este documento es el primer entregable del semestre y la base de todo lo que viene después.
> Se entrega completo en la **semana 4** y se presenta ante el grupo.
>
> **Cómo usarla:** copia este archivo a tu repositorio como `docs/vision-del-producto.md`, borra las instrucciones en gris de cada apartado y escribe tu contenido en su lugar. Conserva los títulos.

---

**Autor: Ana Camila Lopez Sanchez**
**Fecha de la última versión:**
**Repositorio:**

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



**Un conflicto entre usuarios:** El vendedor puede querer registrar la información de manera rápida y con la libertad de agregar notas según cada cliente, mientras que el gerente necesita que la información esté organizada de una misma forma para poder comparar y revisar las ventas. Por lo tanto, el sistema tendrá que encontrar un equilibrio entre permitir que el vendedor trabaje rápidamente y establecer la información mínima que todos deben registrar.

**Huecos importantes:** 

**¿Quién puede hacer qué?**
<li>Cliente: Puede entrar al sistema, consultar los autos disponibles, seleccionar los que le interesan y revisar el estado de su proceso de compra.</li>
<li>Vendedor: Registra clientes, autos de interés, cotizaciones y actualiza el avance de cada venta. Solo puede modificar la información de sus clientes.</li>
<li>Gerente: Puede consultar todas las ventas y clientes, supervisar a los vendedores y modificar información cuando sea necesario.
</li>

**¿Qué pasa cuando se concreta una venta?**
<li>La venta se marca como completada: El cliente pasa de estar en proceso a tener una venta finalizada.</li>
<li>Deja de aparecer en pendientes: Ya no necesita seguimientos de venta, por lo que sale de la lista de clientes pendientes.</li>
<li>Se guarda el historial: La información de la venta queda registrada para que el vendedor y el gerente puedan consultarla posteriormente.</li>


---

## 3. Alcance

*Instrucción: lo que escribes en "fuera del alcance" es lo que después evita que el proyecto crezca sin control. Sé específico: "reportes" no dice nada, "reportes de ventas mensuales exportables a PDF" sí.*

### Dentro del alcance

-
-
-
-

### Explícitamente fuera del alcance

-
-
-

**Por qué queda fuera:**

*Instrucción: para al menos una de las exclusiones, explica la razón. Puede ser tiempo, complejidad, o que no aporta al problema central.*

---

## 4. Tipo de sistema y restricciones

*Instrucción: identifica de qué tipo es tu sistema y qué te obliga a garantizar ese tipo. Un sistema de información y un sistema crítico no se diseñan igual.*

**Tipo de sistema:**

*(De información · Embebido · Crítico · Web y SaaS · De datos y análisis)*

**Por qué es de ese tipo:**

**Atributos de calidad que impone:**

| Atributo | Por qué importa en mi caso | Qué pasa si no se cumple |
|---|---|---|
| | | |
| | | |
| | | |

**Reglas de negocio que ya identifiqué:**

*Instrucción: reglas que no son obvias desde fuera y que alguien que conoce el dominio tendría que explicarte. Si no encuentras ninguna, tu caso puede ser demasiado simple.*

1.
2.
3.

---

## 5. Ciclo de vida elegido

*Instrucción: este apartado se trabaja en la semana 3, después de ver los modelos de desarrollo. La justificación pesa más que la elección: no hay un modelo correcto, hay uno defendible para tu caso.*

**Modelo elegido:**

**Por qué le conviene a este proyecto:**

*Instrucción: argumenta con las características reales de tu caso. Estabilidad de los requisitos, disponibilidad del cliente, nivel de riesgo, tamaño del equipo, frecuencia de entregas esperada.*

### Alternativas descartadas

**Alternativa 1:**

*Por qué la descarté:*

**Alternativa 2:**

*Por qué la descarté:*

---

## Antes de entregar

Reviso que el documento cumpla lo siguiente:

- [ ] La descripción del apartado 1 se entiende sin ser del área
- [ ] Hay al menos dos tipos de usuario con necesidades distintas
- [ ] Identifiqué un conflicto real entre usuarios
- [ ] El alcance dice qué queda fuera, no solo qué queda dentro
- [ ] Las exclusiones son específicas, no genéricas
- [ ] Identifiqué el tipo de sistema y al menos dos atributos de calidad
- [ ] Anoté al menos tres reglas de negocio no obvias
- [ ] Justifiqué el ciclo de vida contra dos alternativas descartadas
- [ ] El documento está en mi repositorio y se puede leer desde el navegador
- [ ] Borré todas las instrucciones en cursiva de la plantilla

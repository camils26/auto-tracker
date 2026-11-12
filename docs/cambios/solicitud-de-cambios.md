# SC-001: Detectar clientes sin actividad reciente

## Estado

Propuesta · 12 de noviembre de 2026

## Quién la pide

Miriam Gómez, dupla de revisión.

## Qué se pide

Quiero que el vendedor pueda ver, sin buscar uno por uno, qué clientes
con una venta en curso llevan mucho tiempo sin que se registre nada con
ellos, para saber a quién debe darle seguimiento. La agencia debería poder
decidir cuánto tiempo sin actividad se considera "mucho".

## Por qué

Según la entrevista con el vendedor, perderle la pista a un cliente puede
significar perder una venta, y hoy se le olvida dar seguimiento a algunos
porque es difícil mantener el orden de las etapas. La documentación
define cómo reactivar a un cliente inactivo (RF-008), pero no cómo un
cliente llega a estar inactivo, así que el vendedor depende de su memoria
para notarlo.

## Qué pasa si no se hace

El sistema ordena la información pero no evita el problema que motivó el
proyecto: los clientes que dejan de responder siguen pasando
desapercibidos hasta que ya es tarde. No es grave para operar, pero
reduce el valor principal del sistema.

## Tipo de mantenimiento

- [ ] Correctivo
- [ ] Adaptativo
- [x] **Perfectivo** · el sistema funciona, pero puede cumplir mejor su
  objetivo de evitar que se pierda el seguimiento.
- [ ] Preventivo

## Criterio de aceptación

- Si un cliente con venta en curso no tiene actividad registrada durante
  el plazo definido por la agencia, aparece en la lista "Sin actividad"
  de su vendedor.
- Al registrar cualquier actividad con ese cliente, deja de aparecer en
  esa lista.
- Un cliente con la venta completada o perdida nunca aparece en la lista.
- El vendedor solo ve los clientes sin actividad que son suyos.

## Prioridad que sugiere el solicitante

Media. Atiende el dolor central del vendedor, pero el sistema ya es
usable sin esto y hay requisitos imprescindibles que van antes.

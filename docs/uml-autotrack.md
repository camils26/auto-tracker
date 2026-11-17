# Modelo UML de AutoTrack

Modelo estructural (clases) y de comportamiento (secuencia y estados), en texto de Mermaid.

## Diagrama de clases

```mermaid
classDiagram
  class Vendedor {
    -nombre: string
    -telefono: string
    -correo: string
    +registrarCliente(datos) Cliente
    +generarCotizacion(venta) Cotizacion
    +programarPrueba(venta, fecha, hora) PruebaDeManejo
    +avanzarEtapa(venta) void
    +reactivarCliente(cliente) void
    +cerrarVenta(venta) void
  }

  class Cliente {
    -nombre: string
    -telefono: string
    -correo: string
    -necesidades: string
    -hobbies: string
    -activo: boolean
    +consultarCatalogo() List~Automovil~
    +marcarAutoDeInteres(auto) void
    +consultarEstadoDeCompra() Etapa
  }

  class Gerente {
    -nombre: string
    -telefono: string
    -correo: string
    +consultarVentas() List~Venta~
    +pedirReporte(periodo) void
    +corregirInformacion(venta) void
  }

  class Venta {
    -etapa: Etapa
    -canalDeVenta: string
    -fechaEntrega: Date
    -estado: string
    +avanzarEtapa() void
    +retroceder(motivo) void
    +cambiarAutomovil(auto) void
    +completar() void
    +marcarPerdida() void
    +notificarCambio() void
  }

  class Cotizacion {
    -precio: double
    -condiciones: string
    -fecha: Date
    +calcularTotal() double
  }

  class PruebaDeManejo {
    -fecha: Date
    -hora: string
    -realizada: boolean
    -opinion: string
    +reprogramar(fecha, hora) void
    +registrarOpinion(texto) void
  }

  class CambioDeEtapa {
    -etapaAnterior: Etapa
    -etapaNueva: Etapa
    -fecha: Date
    -motivo: string
  }

  class Automovil {
    -modelo: string
    -marca: string
    -precio: double
    -condiciones: string
    -disponible: boolean
    -ubicacion: string
  }

  class Etapa {
    <<enumeration>>
    interesado
    cotizacion
    pruebaDeManejo
    negociacion
    apartado
    vendida
    completada
    perdida
  }

  Vendedor "1" --> "*" Cliente : es responsable de
  Vendedor "1" --> "*" Venta : atiende
  Cliente "1" --> "*" Venta : tiene
  Gerente "1" ..> "*" Venta : consulta y corrige
  Venta "1" *-- "*" Cotizacion : contiene
  Venta "1" *-- "*" PruebaDeManejo : contiene
  Venta "1" *-- "*" CambioDeEtapa : registra
  Venta "*" --> "1" Automovil : auto de interes
  Cotizacion "*" --> "1" Automovil : cotiza
  PruebaDeManejo "*" --> "1" Automovil : prueba
  Venta ..> Etapa
```

## Diagrama de secuencia: avanzar la etapa de venta (CU-04)

```mermaid
sequenceDiagram
  autonumber
  actor Vend as Vendedor
  participant Web as App web
  participant CyV as Clientes y ventas
  participant Seg as Seguimiento y reportes
  participant BD as Base de datos

  Vend->>Web: Avanza la venta a "cotización"
  Web->>CyV: avanzarEtapa(venta)
  CyV->>BD: Lee etapa actual
  BD-->>CyV: interesado
  Note over CyV: Valida que "cotización" sea la siguiente etapa
  CyV->>BD: Guarda cambio de etapa con fecha
  BD-->>CyV: Listo
  CyV->>Seg: notificarCambio(venta)
  Seg-->>CyV: Aviso recibido
  CyV-->>Web: Etapa actualizada
  Web-->>Vend: Muestra la ficha con la nueva etapa
```

## Diagrama de estados: ciclo de vida de la venta

```mermaid
stateDiagram-v2
  [*] --> Interesado
  Interesado --> Cotizacion: avanza [es la siguiente etapa] / registrar cambio y notificar
  Cotizacion --> PruebaDeManejo: avanza [es la siguiente etapa] / registrar cambio y notificar
  PruebaDeManejo --> Negociacion: avanza [es la siguiente etapa] / registrar cambio y notificar
  Negociacion --> PruebaDeManejo: retrocede [con motivo] / registrar motivo
  Negociacion --> Apartado: avanza [es la siguiente etapa] / registrar cambio y notificar
  Apartado --> Vendida: avanza [canal de venta definido] / registrar cambio y notificar
  Vendida --> Completada: entrega el vehículo [vehículo disponible] / completar y registrar fecha de entrega
  Interesado --> Perdida: cliente desiste / marcarPerdida
  Cotizacion --> Perdida: cliente desiste / marcarPerdida
  PruebaDeManejo --> Perdida: cliente desiste / marcarPerdida
  Negociacion --> Perdida: cliente desiste / marcarPerdida
  Apartado --> Perdida: cliente desiste / marcarPerdida
  Completada --> [*]
  Perdida --> [*]
```

## Concordancia entre diagramas

| Secuencia (CU-04) | Clases | Estados |
|---|---|---|
| Mensaje 2, `avanzarEtapa(venta)` | `Venta.avanzarEtapa()` y `Vendedor.avanzarEtapa(venta)` | Transición "avanza" |
| Nota de validación, "sea la siguiente etapa" | Regla dentro de `Venta.avanzarEtapa()` | Guarda `[es la siguiente etapa]` |
| Mensaje 5, "Guarda cambio de etapa con fecha" | Clase `CambioDeEtapa` (etapaAnterior, etapaNueva, fecha, motivo) | Acción "registrar cambio" |
| Mensaje 7, `notificarCambio(venta)` | `Venta.notificarCambio()` | Acción "notificar" |
| Mensaje 3, "Lee etapa actual" | Atributo `Venta.etapa` | Estado actual de la venta |
| Etapas "interesado" y "cotización" | Enumeración `Etapa` | Estados `Interesado` y `Cotizacion` |

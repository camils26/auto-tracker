Nivel 1 · Diagrama de contexto 
flowchart TD
  rec([Recepcionista])
  vet([Veterinario])
  sis[Sistema de la clinica]
  lab[Laboratorio externo]
  pago[Pasarela de pagos]
  rec -->|agenda y cobra| sis
  vet -->|consulta expedientes| sis
  sis -->|envia estudios| lab
  sis -->|cobra consultas| pago
  style sis fill:#ff5d00,color:#fff

Nivel 2 · Diagrama de contenedores
flowchart TD
  rec([Recepcionista])

  subgraph sistema[Sistema de la clinica]
    web[App web<br/>React]
    api[API<br/>Node.js]
    db[(Base de datos<br/>PostgreSQL)]
  end
  lab[Laboratorio externo]
    rec -->|usa| web
    web -->|HTTPS/JSON| api
    api -->|lee y escribe| db
    api -->|SFTP| lab
  style api fill:#ff5d00,color:#fff

Nivel 3 · Diagrama de componentes
flowchart TD
  web[App web]

  subgraph api[API del sistema]
    agenda[Agenda<br/>citas y horarios]
    cobros[Cobros<br/>cuentas y pagos]
    exp[Expedientes<br/>historial clinico]
    notif[Notificador<br/>interfaz de envio]
  end

  db[(Base de datos)]
    correo[Servicio de correo]
    web --> agenda
    web --> cobros
    web --> exp
    cobros -->|pregunta que se atendio| agenda
    cobros -->|enviarRecibo| notif
    notif --> correo
    agenda --> db
    cobros --> db
    exp --> db

  style cobros fill:#ff5d00,color:#fff

Diagrama de flujo con decisiones
%%{init: {'theme':'base','flowchart':{'curve':'basis'},'themeVariables':{'fontFamily':'Verdana','lineColor':'#0f766e'}}}%%
flowchart LR
  ini([Inicio])
  val{Monto mayor a cero?}
  exc{Excede el saldo?}
  apl[Aplicar el abono]
  err1[Monto invalido]
  err2[Excede el saldo]
  fin([Fin])

  ini ==> val
  val -.->|No| err1
  val ==>|Si| exc
  exc -.->|Si| err2
  exc ==>|No| apl
  err1 -.-> fin
  err2 -.-> fin
  apl ==> fin

  classDef inicioFin fill:#0f172a,stroke:#0f172a,color:#fff,stroke-width:2px
  classDef decision fill:#fef3c7,stroke:#d97706,color:#78350f,stroke-width:2px
  classDef error fill:#ffe4e6,stroke:#e11d48,color:#881337,stroke-width:2px
  classDef exito fill:#0d9488,stroke:#115e59,color:#fff,stroke-width:2px

  class ini,fin inicioFin
  class val,exc decision
  class err1,err2 error
  class apl exito

  linkStyle 0,2,4,7 stroke:#0d9488,stroke-width:3px
  linkStyle 1,3,5,6 stroke:#e11d48,stroke-width:2px

Diagrama de secuencia
%%{init: {'theme':'base','themeVariables':{
  'fontFamily':'Verdana',
  'actorBkg':'#4f46e5','actorTextColor':'#ffffff','actorBorder':'#312e81',
  'actorLineColor':'#a5b4fc',
  'signalColor':'#7c3aed','signalTextColor':'#1e1b4b',
  'noteBkgColor':'#ede9fe','noteTextColor':'#1e1b4b',
  'activationBkgColor':'#ddd6fe','activationBorderColor':'#7c3aed'
}}}%%
sequenceDiagram
  autonumber
  actor Rec as Recepcionista
  participant Web as App web
  participant Cob as Cobros
  participant Age as Agenda
  participant BD as Base de datos

  Rec->>+Web: Registra un abono de 500
  Web->>+Cob: abonar(cuenta, 500)
  Cob->>+Age: Que servicio se atendio?
  Age-->>-Cob: Consulta general
  Cob->>+BD: Guarda el pago
  BD-->>-Cob: Listo
  Cob-->>-Web: Pago registrado
  Web-->>-Rec: Muestra el nuevo saldo

Diagrama de clases
classDiagram
  class CuentaDePaciente {
    -saldo: double
    -pagos: List~Pago~
    +abonar(monto) string
    +consultarSaldo() double
  }

  class Pago {
    -monto: double
    -fecha: Date
  }

  class Paciente {
    -nombre: string
    -especie: string
  }

  Paciente "1" --> "1" CuentaDePaciente : tiene
  CuentaDePaciente "1" --> "*" Pago : registra

**Diagrama de estados**
%%{init: {'theme':'base','themeVariables':{'fontFamily':'Verdana','lineColor':'#9333ea','classText':'#1f2937'}}}%%
classDiagram
  direction LR

  class Paciente {
    -nombre: string
    -especie: string
  }

  class CuentaDePaciente {
    -saldo: double
    -pagos: List~Pago~
    +abonar(monto) string
    +consultarSaldo() double
  }

  class Pago {
    -monto: double
    -fecha: Date
  }

  Paciente "1" ..> "1" CuentaDePaciente : tiene
  CuentaDePaciente "1" ..> "*" Pago : registra

  style Paciente fill:#e0f2fe,stroke:#0284c7,stroke-width:2px,color:#0c4a6e
  style CuentaDePaciente fill:#f3e8ff,stroke:#9333ea,stroke-width:2px,color:#581c87
  style Pago fill:#dcfce7,stroke:#16a34a,stroke-width:2px,color:#14532d

Diagrama entidad-relacion
%%{init: {'theme':'base','themeVariables':{
  'fontFamily':'Verdana',
  'primaryColor':'#ccfbf1','primaryBorderColor':'#0f766e','primaryTextColor':'#134e4a',
  'lineColor':'#0f766e','secondaryColor':'#fef3c7','tertiaryColor':'#f0fdfa'
}}}%%
erDiagram
  PACIENTE ||--o{ CITA : tiene
  PACIENTE ||--|| CUENTA : tiene
  CITA ||--o| EXPEDIENTE : genera
  CUENTA ||--o{ PAGO : registra

  PACIENTE {
    int id
    string nombre
    string especie
  }

  CITA {
    int id
    date fecha
    string motivo
  }

  PAGO {
    int id
    decimal monto
    date fecha
  }




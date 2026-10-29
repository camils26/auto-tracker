

## Estado
Aceptada, 29 de octubre de 2026

## Contexto
AutoTrack es el sistema con el que una agencia de autos da seguimiento a sus
oportunidades de venta. Lo usan clientes, vendedores y un gerente. El sistema
lo construye una sola persona, o un equipo muy pequeño, así que no hay quien
despliegue y mantenga varios servicios por separado.

Las fronteras entre módulos están claras: usuarios y accesos, clientes y
ventas, catálogo de autos, y seguimiento y reportes. El catálogo casi no
depende de nada y solo responde cuando clientes y ventas le pregunta algo.
Seguimiento y reportes lee la información de clientes y ventas, pero no la
modifica. Cada cambio de etapa de una venta avisa a otros módulos
(recordatorios, historial, reportes y vista del cliente).

Se evaluó separar los módulos en microservicios. Se descartó porque el
proyecto sigue un ciclo de prototipado rápido, así que los requisitos van a
cambiar al mostrar el sistema a los usuarios, y porque repartirlo solo
complicaría más el proyecto.

## Decisión
Construimos un monolito modular: una sola aplicación y una sola base de datos,
con los cuatro módulos separados por carpetas e interfaces, y con la regla de
que ningún módulo lee las tablas de otro. Si un módulo necesita información
de otro, la pide a través de su interfaz.

## Consecuencias
Hay un solo despliegue, un solo registro de errores y una sola base de datos.
Esto es lo que se puede operar hoy y permite hacer los cambios que pidan los
usuarios sobre el prototipo sin coordinar varios servicios. Además, el aviso
de cambio de etapa (Observer) ocurre dentro de la misma aplicación, sin
necesidad de mensajería entre servicios.

No podemos escalar un módulo por separado. Si la aplicación se cae, se caen
todos los módulos a la vez, lo que afecta la disponibilidad que necesitan
vendedores y gerente.

Si algún día hay que separar un módulo, el primero sería seguimiento y
reportes, porque es el que más carga tendría: cada cambio de etapa dispara
recordatorios y los reportes del gerente recorren el historial de todos los
clientes. La señal de que llegó ese día sería que los reportes tarden más de
unos segundos en cargar, que el sistema se ponga lento para los vendedores
cuando el gerente genera un reporte, o que este módulo necesite desplegarse
mucho más seguido que los demás porque se le agregan reportes cada mes.
Como las fronteras ya están puestas, el corte es por donde ya cortamos.

El riesgo real es que alguien lea las tablas de otro módulo por atajo y se
pierda el límite, por ejemplo que seguimiento y reportes consulte
directamente las tablas de clientes y ventas. Lo revisamos en cada pull
request.

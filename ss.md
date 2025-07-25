# 9.1. Revision de Entradas

### Funcionalidades primarias (Casos de Uso)

Las funcionalidades primarias de la plataforma SportSync consideran las siguientes historias de usuario, que son criticas para el negocio y guian el diseno inicial.

| ID | Modulo | Nombre | Historia de Usuario |
| :--- | :--- | :--- | :--- |
| RF1.1 | Gestion de Reservas | Busqueda de Polideportivos | **Como** usuario, **quiero** buscar polideportivos segun fecha, hora, ubicacion y tipo, **para** encontrar facilmente una opcion que se adapte a mis necesidades. |
| RF1.4 | Gestion de Reservas | Realizar Reserva | **Como** usuario, **quiero** reservar una cancha seleccionando un horario disponible, **para** asegurar mi espacio. |
| RF1.5 | Gestion de Reservas | Administracion de Canchas | **Como** administrador, **quiero** registrar, editar o eliminar canchas, **para** mantener actualizada la oferta del sistema. |
| RF1.6 | Gestion de Reservas | Aprobacion de Reserva | **Como** administrador, **quiero** aprobar o cancelar reservas, **para** tener control sobre la disponibilidad. |
| RF2.1 | Gestion de Pagos | Metodos de Pago Integrados | **Como** usuario, **quiero** pagar con metodos como Yape, Plin o tarjeta, **para** tener flexibilidad al momento del pago. |
| RF2.2 | Gestion de Pagos | Vinculacion con Reservas | **Como** sistema, **quiero** asociar cada pago con una reserva, **para** garantizar que solo reservas pagadas esten activas. |
| RF3.2 | Gestion de Proveedores | Solicitudes de Servicio | **Como** administrador, **quiero** crear solicitudes para servicios en canchas, **para** resolver necesidades puntuales. |
| RF3.3 | Gestion de Proveedores | Recomendacion de Proveedores | **Como** administrador, **quiero** ver sugerencias de proveedores segun criterios, **para** tomar decisiones optimas. |
| RF4.1 | Gestion Financiera | Reportes de Ingresos | **Como** administrador, **quiero** generar reportes de ingresos, **para** evaluar el desempeno economico del negocio. |
| RF5.1 | Gestion de Usuarios | Registro de Usuarios | **Como** usuario, **quiero** registrarme con mi correo o numero, **para** usar la plataforma como jugador individual. |
| RF5.2 | Gestion de Usuarios | Registro de Entidades | **Como** entidad, **quiero** registrarme con datos institucionales (RUC, representante), **para** realizar reservas a nombre de mi organizacion. |
| RF5.3 | Gestion de Usuarios | Gestion de Perfil | **Como** usuario, **quiero** editar mis datos personales y foto, **para** mantener mi informacion actualizada. |
| RF6.1 | Notificaciones | Notificaciones de Evento | **Como** usuario, **quiero** recibir notificaciones cuando haya una reserva, pago pendiente o cambio, **para** estar al tanto de mis actividades. |

### Escenarios de Atributos de Calidad

Los siguientes escenarios, refinados y priorizados, son los principales impulsores del diseno arquitectonico.

| ID | Atributo de calidad | Fuente Estimulo | Estimulo | Artefacto | Entorno | Respuesta | Medida de Respuesta | Casos de uso relacionados |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| ESC-01 | Disponibilidad | Falla del servidor principal | Servidor en la nube | Modulo de reservas | Operacion normal | Conmutacion automatica entre instancias activas | >= 98% de disponibilidad mensual | RF1.1, RF1.4, RF1.6 |
| ESC-02 | Disponibilidad | API de pago no responde | Plataforma externa | Modulo de pagos | Pago en proceso | Reintento automatico antes de fallo | Recuperacion del 90% de transacciones | RF2.1, RF2.2 |
| ESC-11 | Interoperabilidad | Solicitud de cobro tras reserva confirmada | Modulo de reservas | Microservicio de Pagos | Operacion integrada con terceros (Yape, Plin, Stripe) | Llamada a pasarela de pago externa con transformacion de datos segun API del proveedor | 98% de transacciones procesadas correctamente en primera llamada | RF2.1, RF2.2, RF2.4 |
| ESC-19 | Rendimiento | 100 usuarios reservando a la vez | Usuario concurrente | Modulo de reservas + DB | Horario pico | Caching temporal y acceso concurrente controlado | 85% de reservas < 3.5s (medicion Prometheus) | RF1.2, RF1.4, RF1.6 |
| ESC-20 | Seguridad | 100+ intentos de login fallidos desde una misma IP | Ataque automatizado | Endpoint de autenticacion | Produccion | Bloqueo temporal + CAPTCHA progresivo | <0.1% exito en ataques brute force | RF5.1, RF5.2 |
| ESC-22 | Seguridad | Intercepcion de datos en transito | Atacante externo | Modulo de pagos | En linea | Encriptacion HTTPS + Validacion HMAC | 100% comunicaciones encriptadas | RF2.1, RF2.3, RF2.4 |
| ESC-23 | Seguridad | Acceso no autorizado a datos sensibles | Atacante externo | Modulo de proveedores | Produccion | RBAC + cifrado AES-256 de datos | 0 accesos no autorizados | RF3.1, RF5.6 |
| ESC-26 | Usabilidad | 35% de abandono en registro | Google Analytics | Formulario de registro | Mobile (60% trafico) | Rediseno progresivo con validacion inmediata | Reduccion al 15% de abandono | RF5.1, RF5.2 |
| ESC-32 | Escalabilidad | Solicita habilitar sedes en nuevas ciudades | Administrador del sistema | Gestion de reservas | Despliegue de nuevas sedes | Sistema permite registrar nuevas sedes y canchas | Tiempo promedio de despliegue < 4 horas | RF1.5, RF4.4 |

### Restricciones

Las siguientes restricciones definen el marco tecnico y operativo dentro del cual se debe construir el sistema.

| ID | Nombre | Descripcion |
| :--- | :--- | :--- |
| CON-01 | Stack Tecnologico Fijo | El frontend del sistema sera desarrollado utilizando React.js. El backend sera desarrollado en Node.js con Express.js y Sequelize como ORM. |
| CON-02 | Arquitectura en Capas | La arquitectura debera seguir el enfoque N-Tier desacoplado, favoreciendo la escalabilidad y facilidad de mantenimiento. |
| CON-03 | Base de Datos Relacional | Las credenciales y datos del sistema se almacenaran en una base de datos PostgreSQL. |
| CON-04 | Seguridad de Sesiones | La autenticacion debe implementarse utilizando JSON Web Tokens (JWT) para sesiones seguras y escalables. |
| CON-05 | Seguridad de Contrasenas | Las credenciales de los usuarios deberan ser protegidas mediante hashing con bcrypt. |
| CON-06 | Integracion de Pagos Locales | El sistema debera integrar metodos de pago locales (Yape, Plin) y tarjetas bancarias, respetando las regulaciones peruanas. |
| CON-07 | Control de Acceso | El sistema debe implementar un control de acceso por roles (RBAC) para asegurar que cada tipo de usuario acceda solo a las funcionalidades permitidas. |
| CON-08 | Entorno de Despliegue | El sistema debera estar preparado para su despliegue en entornos cloud como Heroku, Render o Railway. |

### Preocupaciones a Nivel de Arquitectura

Estas son las principales preocupaciones y desafios que la arquitectura debe abordar para garantizar el exito del proyecto.

| ID | Nombre | Descripcion |
| :--- | :--- | :--- |
| CRN-01 | Disponibilidad del Sistema Core | Garantizar que los modulos de reservas y pagos permanezcan operativos y con alta disponibilidad, incluso durante fallos del servidor o de las APIs externas de pago, ya que son el nucleo del negocio. |
| CRN-02 | Escalabilidad ante Crecimiento | Asegurar que la plataforma pueda escalar de manera eficiente para soportar un aumento en el numero de usuarios, complejos deportivos y ciudades sin degradar el rendimiento. |
| CRN-03 | Seguridad de Transacciones y Datos | Proteger de forma robusta toda la informacion sensible, incluyendo los datos de pago durante las transacciones y las credenciales de los usuarios en la base de datos, previniendo accesos no autorizados. |
| CRN-04 | Mantenibilidad a Largo Plazo | Disenar el sistema con un bajo acoplamiento y alta cohesion para que sea facil de mantener, modificar y extender en el futuro sin que los cambios en un modulo afecten a otros. |
| CRN-05 | Rendimiento en Horarios Pico | Optimizar las consultas y el manejo de concurrencia para que el sistema responda rapidamente durante los horarios de mayor demanda, como cuando multiples usuarios buscan y reservan canchas simultaneamente. |
| CRN-06 | Integracion Fiable con APIs Externas | Gestionar de forma resiliente la comunicacion con servicios de terceros, como pasarelas de pago y sistemas de geolocalizacion, manejando errores, reintentos y posibles latencias. |
| CRN-07 | Usabilidad y Experiencia de Usuario | Garantizar que la plataforma sea intuitiva y facil de usar tanto para los deportistas como para los administradores, simplificando procesos clave como el registro, la reserva y el pago para minimizar la friccion. |

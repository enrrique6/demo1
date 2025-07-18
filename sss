# 9.1. Revisión de Entradas

### Funcionalidades primarias (Casos de Uso)

Las funcionalidades primarias de la plataforma SportSync consideran las siguientes historias de usuario, que son críticas para el negocio y guían el diseño inicial.

| ID | Módulo | Nombre | Historia de Usuario |
| :--- | :--- | :--- | :--- |
| RF1.1 | GestiÃ³n de Reservas | BÃºsqueda de Polideportivos | [cite_start]**Como** usuario, **quiero** buscar polideportivos segÃºn fecha, hora, ubicaciÃ³n y tipo, **para** encontrar fÃ¡cilmente una opciÃ³n que se adapte a mis necesidades. [cite: 310] |
| RF1.4 | GestiÃ³n de Reservas | Realizar Reserva | [cite_start]**Como** usuario, **quiero** reservar una cancha seleccionando un horario disponible, **para** asegurar mi espacio. [cite: 316] |
| RF1.5 | GestiÃ³n de Reservas | AdministraciÃ³n de Canchas | [cite_start]**Como** administrador, **quiero** registrar, editar o eliminar canchas, **para** mantener actualizada la oferta del sistema. [cite: 317] |
| RF1.6 | GestiÃ³n de Reservas | AprobaciÃ³n de Reserva | [cite_start]**Como** administrador, **quiero** aprobar o cancelar reservas, **para** tener control sobre la disponibilidad. [cite: 319] |
| RF2.1 | GestiÃ³n de Pagos | MÃ©todos de Pago Integrados | [cite_start]**Como** usuario, **quiero** pagar con mÃ©todos como Yape, Plin o tarjeta, **para** tener flexibilidad al momento del pago. [cite: 326] |
| RF2.2 | GestiÃ³n de Pagos | VinculaciÃ³n con Reservas | [cite_start]**Como** sistema, **quiero** asociar cada pago con una reserva, **para** garantizar que solo reservas pagadas estÃ©n activas. [cite: 328] |
| RF3.2 | GestiÃ³n de Proveedores | Solicitudes de Servicio | [cite_start]**Como** administrador, **quiero** crear solicitudes para servicios en canchas, **para** resolver necesidades puntuales. [cite: 344] |
| RF3.3 | GestiÃ³n de Proveedores | RecomendaciÃ³n de Proveedores | [cite_start]**Como** administrador, **quiero** ver sugerencias de proveedores segÃºn criterios, **para** tomar decisiones Ã³ptimas. [cite: 345] |
| RF4.1 | GestiÃ³n Financiera | Reportes de Ingresos | [cite_start]**Como** administrador, **quiero** generar reportes de ingresos, **para** evaluar el desempeÃ±o econÃ³mico del negocio. [cite: 357] |
| RF5.1 | GestiÃ³n de Usuarios | Registro de Usuarios | [cite_start]**Como** usuario, **quiero** registrarme con mi correo o nÃºmero, **para** usar la plataforma como jugador individual. [cite: 372] |
| RF5.2 | GestiÃ³n de Usuarios | Registro de Entidades | [cite_start]**Como** entidad, **quiero** registrarme con datos institucionales (RUC, representante), **para** realizar reservas a nombre de mi organizaciÃ³n. [cite: 374] |
| RF5.3 | GestiÃ³n de Usuarios | GestiÃ³n de Perfil | [cite_start]**Como** usuario, **quiero** editar mis datos personales y foto, **para** mantener mi informaciÃ³n actualizada. [cite: 376] |
| RF6.1 | Notificaciones | Notificaciones de Evento | [cite_start]**Como** usuario, **quiero** recibir notificaciones cuando haya una reserva, pago pendiente o cambio, **para** estar al tanto de mis actividades. [cite: 388] |

### Escenarios de Atributos de Calidad

Los siguientes escenarios, refinados y priorizados, son los principales impulsores del diseño arquitectónico.

| ID | Atributo de calidad | Fuente EstÃ­mulo | EstÃ­mulo | Artefacto | Entorno | Respuesta | Medida de Respuesta | Casos de uso relacionados |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| ESC-01 | Disponibilidad | Falla del servidor principal | Servidor en la nube | MÃ³dulo de reservas | OperaciÃ³n normal | ConmutaciÃ³n automÃ¡tica entre instancias activas | â‰¥ 98% de disponibilidad mensual | RF1.1, RF1.4, RF1.6 |
| ESC-02 | Disponibilidad | API de pago no responde | Plataforma externa | MÃ³dulo de pagos | Pago en proceso | Reintento automÃ¡tico antes de fallo | [cite_start]RecuperaciÃ³n del 90% de transacciones [cite: 1142] | RF2.1, RF2.2 |
| ESC-11 | Interoperabilidad | Solicitud de cobro tras reserva confirmada | MÃ³dulo de reservas | Microservicio de Pagos | OperaciÃ³n integrada con terceros (Yape, Plin, Stripe) | Llamada a pasarela de pago externa con transformaciÃ³n de datos segÃºn API del proveedor | 98% de transacciones procesadas correctamente en primera llamada | RF2.1, RF2.2, RF2.4 |
| ESC-19 | Rendimiento | 100 usuarios reservando a la vez | Usuario concurrente | MÃ³dulo de reservas + DB | Horario pico | Caching temporal y acceso concurrente controlado | 85% de reservas < 3.5s (mediciÃ³n Prometheus) | RF1.2, RF1.4, RF1.6 |
| ESC-20 | Seguridad | 100+ intentos de login fallidos desde una misma IP | Ataque automatizado | Endpoint de autenticaciÃ³n | ProducciÃ³n | Bloqueo temporal + CAPTCHA progresivo | <0.1% Ã©xito en ataques brute force | RF5.1, RF5.2 |
| ESC-22 | Seguridad | InterceptaciÃ³n de datos en trÃ¡nsito | Atacante externo | MÃ³dulo de pagos | En lÃ­nea | EncriptaciÃ³n HTTPS + ValidaciÃ³n HMAC | 100% comunicaciones encriptadas | RF2.1, RF2.3, RF2.4 |
| ESC-23 | Seguridad | Acceso no autorizado a datos sensibles | Atacante externo | MÃ³dulo de proveedores | ProducciÃ³n | RBAC + cifrado AES-256 de datos | 0 accesos no autorizados | RF3.1, RF5.6 |
| ESC-26 | Usabilidad | 35% de abandono en registro | Google Analytics | Formulario de registro | Mobile (60% trÃ¡fico) | RediseÃ±o progresivo con validaciÃ³n inmediata | ReducciÃ³n al 15% de abandono | RF5.1, RF5.2 |
| ESC-32 | Escalabilidad | Solicita habilitar sedes en nuevas ciudades | Administrador del sistema | GestiÃ³n de reservas | Despliegue de nuevas sedes | Sistema permite registrar nuevas sedes y canchas | Tiempo promedio de despliegue < 4 horas | RF1.5, RF4.4 |

### Restricciones

Las siguientes restricciones definen el marco técnico y operativo dentro del cual se debe construir el sistema.

| ID | Nombre | Descripción |
| :--- | :--- | :--- |
| CON-01 | Stack Tecnológico Fijo | [cite_start]El frontend del sistema serÃ¡ desarrollado utilizando React.js. [cite: 487] [cite_start]El backend serÃ¡ desarrollado en Node.js con Express.js y Sequelize como ORM. [cite: 488] |
| CON-02 | Arquitectura en Capas | [cite_start]La arquitectura deberÃ¡ seguir el enfoque N-Tier desacoplado, favoreciendo la escalabilidad y facilidad de mantenimiento. [cite: 490] |
| CON-03 | Base de Datos Relacional | [cite_start]Las credenciales y datos del sistema se almacenarÃ¡n en una base de datos PostgreSQL. [cite: 484] |
| CON-04 | Seguridad de Sesiones | [cite_start]La autenticaciÃ³n debe implementarse utilizando JSON Web Tokens (JWT) para sesiones seguras y escalables. [cite: 485] |
| CON-05 | Seguridad de Contraseñas | [cite_start]Las credenciales de los usuarios deberÃ¡n ser protegidas mediante hashing con bcrypt. [cite: 484] |
| CON-06 | Integración de Pagos Locales | [cite_start]El sistema deberÃ¡ integrar mÃ©todos de pago locales (Yape, Plin) y tarjetas bancarias, respetando las regulaciones peruanas. [cite: 473] |
| CON-07 | Control de Acceso | [cite_start]El sistema debe implementar un control de acceso por roles (RBAC) para asegurar que cada tipo de usuario acceda solo a las funcionalidades permitidas. [cite: 477] |
| CON-08 | Entorno de Despliegue | [cite_start]El sistema deberÃ¡ estar preparado para su despliegue en entornos cloud como Heroku, Render o Railway. [cite: 491] |

### Preocupaciones a Nivel de Arquitectura

Estas son las principales preocupaciones y desafíos que la arquitectura debe abordar para garantizar el éxito del proyecto.

| ID | Nombre | Descripción |
| :--- | :--- | :--- |
| CRN-01 | Disponibilidad del Sistema Core | [cite_start]Garantizar que los módulos de reservas y pagos permanezcan operativos y con alta disponibilidad, incluso durante fallos del servidor o de las APIs externas de pago, ya que son el núcleo del negocio. [cite: 1462, 414] |
| CRN-02 | Escalabilidad ante Crecimiento | [cite_start]Asegurar que la plataforma pueda escalar de manera eficiente para soportar un aumento en el número de usuarios, complejos deportivos y ciudades sin degradar el rendimiento. [cite: 408, 444] |
| CRN-03 | Seguridad de Transacciones y Datos | [cite_start]Proteger de forma robusta toda la información sensible, incluyendo los datos de pago durante las transacciones y las credenciales de los usuarios en la base de datos, previniendo accesos no autorizados. [cite: 412, 447] |
| CRN-04 | Mantenibilidad a Largo Plazo | [cite_start]Diseñar el sistema con un bajo acoplamiento y alta cohesión para que sea fácil de mantener, modificar y extender en el futuro sin que los cambios en un módulo afecten a otros. [cite: 1341, 1349] |
| CRN-05 | Rendimiento en Horarios Pico | [cite_start]Optimizar las consultas y el manejo de concurrencia para que el sistema responda rápidamente durante los horarios de mayor demanda, como cuando múltiples usuarios buscan y reservan canchas simultáneamente. [cite: 405] |
| CRN-06 | Integración Fiable con APIs Externas | [cite_start]Gestionar de forma resiliente la comunicación con servicios de terceros, como pasarelas de pago y sistemas de geolocalización, manejando errores, reintentos y posibles latencias. [cite: 414, 482] |
| CRN-07 | Usabilidad y Experiencia de Usuario | [cite_start]Garantizar que la plataforma sea intuitiva y fácil de usar tanto para los deportistas como para los administradores, simplificando procesos clave como el registro, la reserva y el pago para minimizar la fricción. [cite: 401, 416, 449] |

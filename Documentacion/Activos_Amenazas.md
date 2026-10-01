# SecureShop – Actividad 1: Identificación y clasificación de activos

**Materia:** Desarrollo de Software Seguro

**NRC:** 36900

**Integrantes:**
1. Xavier Altamirano
2. Alisson Ayo
3. Yuliana Valencia

**Fecha:** 29-09-2026

| N.º | Activo | Tipo | Consecuencia de acceso no autorizado, modificación o indisponibilidad | Amenazas | Mecanismo de control |
|---|---|---|---|---|---|
| 1 | Datos de usuarios | Información / Datos | Si se accede a este activo hay filtración de datos personales, sanciones legales, pérdida de confianza y daño reputacional. Si se modifica puede darse suplantación de identidad y envíos a direcciones erróneas. Si queda indisponible no se pueden gestionar cuentas ni atender a los clientes. | 1. Inyección SQL.<br>2. Acceso a datos de otros usuarios (IDOR).<br>3. Interceptación de datos en tránsito. | 1. Consultas parametrizadas y validación de entradas.<br>2. Verificar en cada petición que el recurso pertenece al usuario autenticado.<br>3. HTTPS/TLS obligatorio en todas las comunicaciones. |
| 2 | Credenciales (usuarios, contraseñas, hashes) | Información sensible | Si se accede a este activo se pueden tomar cuentas, incluidas las administrativas, y cometer fraude. Si se modifica se bloquea a usuarios legítimos o se crean accesos falsos. Si queda indisponible nadie puede iniciar sesión y se detiene la operación. | 1. Fuerza bruta y credential stuffing.<br>2. Robo de la base de hashes.<br>3. Uso de contraseñas débiles. | 1. Limitación de intentos (rate limiting) y bloqueo temporal de cuenta.<br>2. Almacenar contraseñas con bcrypt o Argon2 con sal.<br>3. Política de contraseñas robustas y MFA para cuentas administrativas. |
| 3 | Catálogo de productos | Información / Datos | Si se accede a este activo la competencia conoce precios y estrategia comercial. Si se modifica hay precios alterados, pérdidas económicas y ventas incorrectas. Si queda indisponible no se puede vender y se pierden ingresos. | 1. Modificación no autorizada de precios.<br>2. Scraping masivo del catálogo.<br>3. Envío de datos manipulados (precios negativos, stock inválido). | 1. Control de acceso por roles (solo el administrador actualiza productos).<br>2. Rate limiting y detección de bots en el API Gateway.<br>3. Validación de esquema y rangos en el servidor (precio mayor a 0, stock mayor o igual a 0). |
| 4 | Información de pedidos (historial, estados, montos) | Datos | Si se accede a este activo se exponen hábitos de compra y datos de clientes. Si se modifica se puede crear fraude, pedidos falsos o cancelados indebidamente. Si queda indisponible existe la imposibilidad de procesar, rastrear o entregar compras. | 1. Consulta de pedidos ajenos.<br>2. Alteración de montos desde el cliente.<br>3. Cambios de estado sin rastro (repudio). | 1. Autorización a nivel de objeto: el pedido debe pertenecer al usuario del token.<br>2. El servidor calcula el total con los precios de la base de datos, nunca los del cliente.<br>3. Registro de auditoría con usuario, fecha y estado anterior y nuevo. |
| 5 | Información de pago y facturación | Información sensible | Si se accede a este activo se puede crear fraude financiero, incumplimiento de PCI-DSS, multas y demandas. Si se modifica puede haber cobros incorrectos y facturación fraudulenta. Si queda indisponible no se pueden cobrar ni facturar las ventas. | 1. Robo de datos de tarjeta.<br>2. Alteración de facturas.<br>3. Exposición de datos de pago en logs o respuestas. | 1. No almacenar datos de tarjeta; usar tokenización con una pasarela certificada PCI-DSS.<br>2. Hash de integridad en facturas y registros inmutables.<br>3. Enmascarar datos sensibles (mostrar solo los últimos 4 dígitos). |

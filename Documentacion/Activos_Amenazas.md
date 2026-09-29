# SecureShop – Actividad 1: Identificación y clasificación de activos

**Materia:** Desarrollo de Software Seguro

**NRC:** 36900

**Integrantes:**
1. Xavier Altamirano
2. Alisson Ayo
3. Yuliana Valencia

**Fecha:** 29-09-2026

| Activo | Tipo | Consecuencia de acceso no autorizado, modificación o indisponibilidad |
|---|---|---|
| Datos de usuarios  | Información / Datos | Filtración de datos personales, sanciones legales, pérdida de confianza y daño reputacional. Uuplantación de identidad, envíos a direcciones erróneas. Imposibilidad de gestionar cuentas y atender clientes. |
| Credenciales (usuarios, contraseñas, hashes) | Información sensible | Toma de control de cuentas, incluidas las administrativas, y fraude. Bloqueo de usuarios legítimos o creación de accesos falsos. Nadie puede iniciar sesión y se detiene la operación. |
| Catálogo de productos  | Información / Datos |La competencia conoce precios y estrategia comercial. Precios alterados, pérdidas económicas, ventas incorrectas. No se puede vender, se pierden ingresos. |
| Información de pedidos (historial, estados, montos) | Datos | Si se accede a este activo queda la exposición de hábitos de compra y datos de clientes. Si se modifica se  puede crear fraude, pedidos falsos o cancelados indebidamente. Si queda indisponible exite la imposibilidad de procesar, rastrear o entregar compras. |
| Información de pago y facturación | Información sensible | Si se accede a este activo se puede crear fraude financiero, incumplimiento de PCI-DSS, multas y demandas. Si se modifica puede existir cobros incorrectos, facturación fraudulenta.|
| Microservicio de usuarios | Software / Servicio | Si se accede a este activo puede existir un abuso de la API para extraer o alterar cuentas.|

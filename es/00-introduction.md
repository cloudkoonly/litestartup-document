# Introducción a LiteStartup
 
 LiteStartup (presentado en el sitio web como *Lite Email for Startups*) es una **plataforma de servicios de correo impulsada por IA** para startups que reúne **Workmail (correo empresarial)**, **correo transaccional** y **correo de marketing** en un solo producto, con una API REST sencilla para integrarlo en minutos.
 
 ## ¿Qué es LiteStartup?
 
 LiteStartup es una plataforma SaaS de correo para startups. En una frase:
 
 - **Un modelo de servicio de correo impulsado por IA** que simplifica tu flujo de trabajo de email (contenido, automatización y entrega)
 - **Una pila unificada para correo empresarial + correo transaccional + correo de marketing**, reduciendo la proliferación de proveedores
 - **Integración pensada para desarrolladores** mediante APIs RESTful estándar (sin SDKs complejos)
 
 A diferencia de las plataformas tradicionales de email marketing que cobran por contacto, LiteStartup prioriza el enfoque de **pago por email enviado**, para que pagues por lo que envías y no por almacenar contactos.
 
 ## Qué nos hace diferentes
 
 ### Workmail como Gmail
 La ÚNICA plataforma de email marketing con correo empresarial tipo `support@yourcompany.com` en cuestión de minutos.
 
 ### AI Content Assistant
 La IA genera emails de marketing y variantes para pruebas A/B para acelerar la redacción y la iteración.
 
 ### Asequible
 Pago por email enviado, no por contacto.
 
 - **Pro**: $20/month por 110,000 emails/month
 - **Overage**: $0.20 por 1,000 emails tras superar el límite
 
 ### Infraestructura de nivel empresarial
 Construido por ingenieros de AWS y Google Cloud. 99.9% de uptime con cumplimiento de SOC2 y GDPR.
 
 ### Notificaciones de email gratuitas
 Obtén un email gratuito como `yourname@litestartup.net` para alertas, reportes y actualizaciones en tu bandeja de entrada preferida.
 
 ### AI Website Builder
 Chatea con la IA para crear landing pages, páginas de lista de espera, newsletters y blogs. Sin necesidad de programar.
 
 ### Ticket + Live Chat
 Gestiona conversaciones con clientes mediante tickets (por email) y un widget de live chat en tiempo real.
 
 ### AI Automation
 Automatización siempre activa: emails de bienvenida, seguimiento y prospección, con captación de leads y workflows de crecimiento integrados.
 
 ## ¿Quién debería usar LiteStartup?
 
 LiteStartup es ideal para:
 
 - **Startups en fase temprana** que están creando su primera base de clientes
 - **Productos SaaS** que necesitan correo transaccional + marketing en un mismo lugar
 - **Equipos de growth** que quieren contenido asistido por IA y experimentos más rápidos
 - **Equipos de producto** que gestionan landing pages y listas de espera
 - **Desarrolladores** que prefieren APIs REST simples con dependencias mínimas
 - **Equipos que evitan el vendor lock-in** y quieren poder cambiar de proveedor más adelante
 
 ## Cómo funciona LiteStartup
 
 ### 1. Registrarte
 Crea una cuenta y empieza con el plan Free (10,000 emails/month).
 
 ### 2. Obtener credenciales de API
 Recupera tu API key desde el dashboard.
 
 ### 3. Integrar
 Envía emails mediante llamadas a la API RESTful. Funciona con cualquier lenguaje o framework.
 
 ### 4. Enviar emails
 Envía emails transaccionales, campañas de marketing o workflows automatizados.
 
 ### 5. Medir y optimizar
 Supervisa analíticas básicas e itera con mejoras asistidas por IA.
 
 ## LiteStartup vs. plataformas tradicionales de email
 
 | Funcionalidad | LiteStartup | Plataformas tradicionales |
 |---|---|---|
 | Workmail (correo empresarial) | ✓ Incluido | ✗ Servicio separado |
 | AI Content Assistant | ✓ Sí | ✗ No |
 | Modelo de precios | Por email enviado | Por contacto |
 | Tiempo de configuración | 5 minutos | 30+ minutos |
 | Integración por API | ✓ API REST simple | ✓ SDKs complejos |
 | Vendor lock-in | ✗ Ninguno | ✓ Sí |
 | Plan gratuito | 10K emails/month | Limitado |
 | Uptime (sitio web) | 99.9% | 99.9% |
 
 ## Primeros pasos
 
 ¿Listo para empezar a enviar emails? Esto es lo siguiente que debes hacer:
 
 1. **[Guía de inicio](/es/01-getting-started.md)** - Regístrate y envía tu primer email en minutos
 2. **[Referencia de la API](/es/02-api-reference.md)** - Documentación completa de la API y endpoints
 3. **[Guía de funcionalidades](/es/03-features.md)** - Explora todas las funciones en detalle
 4. **[Ejemplos de código](/es/04-examples.md)** - Ejemplos de implementación en varios lenguajes
 5. **[Precios y planes](/es/05-pricing.md)** - Entiende precios y facturación
 
 ## Ejemplo de inicio rápido
 
 Envía tu primer email en solo unas pocas líneas de código:

 ```bash
 curl -X POST https://api.litestartup.com/client/v2/emails \
   -H "Authorization: Bearer YOUR_API_KEY" \
   -H "Content-Type: application/json" \
   -d '{
     "to": "user@example.com",
     "from": "noreply@yourapp.com",
     "subject": "Welcome!",
     "html": "<h1>Hello</h1>"
   }'
 ```

 ## Beneficios clave
 
 - **Menor costo** - Pago por email enviado, no por contacto
 - **Mayor productividad** - La asistencia de contenido con IA y la automatización con IA reducen el trabajo manual
 - **Kit todo en uno** - Workmail + envío + landing pages/listas de espera + ticket/live chat
 - **Integración rápida** - API REST sin dependencias complejas de SDK
 - **Menos lock-in** - APIs estándar facilitan cambiar de proveedor
 
 ## Soporte y recursos
 
 - **Documentación**: Guías completas y referencia de la API
 - **Ejemplos de código**: Ejemplos listos para usar en varios lenguajes
 - **Comunidad**: Conecta con otros usuarios de LiteStartup
 
 ## Próximos pasos
 
 - Empieza con la [Guía de inicio rápido](/es/01-getting-started.md)
 - Explora la [Referencia de la API](/es/02-api-reference.md)
 - Revisa [Ejemplos de código](/es/04-examples.md) para tu lenguaje de programación
 - Consulta [Precios y planes](/es/05-pricing.md) para encontrar el plan adecuado

---
 
 **¿Listo para enviar tu primer email?** Empieza con la [Guía de inicio rápido](/es/01-getting-started.md).

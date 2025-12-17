# Guía de características

Explora todas las potentes funcionalidades que ofrece LiteStartup para ayudar a tu startup a tener éxito.

## Workmail - Correo empresarial

LiteStartup incluye funcionalidad de correo empresarial integrada, eliminando la necesidad de servicios de email separados como Google Workspace.

### ¿Qué es Workmail?

Workmail es un servicio de correo empresarial completo integrado directamente en LiteStartup. Envía y recibe emails desde tu dominio personalizado sin suscripciones adicionales.

### Beneficios

- **Ahorra dinero**: $72-144 al año por miembro del equipo (vs. Google Workspace)
- **Plataforma unificada**: Email y marketing en un solo lugar
- **Imagen profesional**: Usa tu dominio personalizado
- **Funciones completas**: Reenvío, alias, autorespuestas

### Primeros pasos con Workmail

1. Ve a **Configuración** → **Workmail**
2. Agrega tu dominio (por ejemplo, `hello@tudominio.com`)
3. Verifica los registros DNS
4. Crea cuentas de correo electrónico para los miembros del equipo
5. Comienza a enviar y recibir correos electrónicos

### Crear cuentas de email

```
1. Click "Add Email Account"
2. Enter username (e.g., "john")
3. Set password
4. Assign to team member
5. Click "Create"
```

La dirección de email será: `john@yourdomain.com`

### Reenvío de email

Configura el reenvío automático:

```
1. Go to email account settings
2. Click "Forwarding"
3. Enter forwarding address
4. Confirm forwarding
5. Emails now forward automatically
```

### Autorespuestas

Configura respuestas automáticas:

```
1. Go to email account settings
2. Click "Auto-Responder"
3. Enable auto-responder
4. Set message and date range
5. Save
```

## AI Content Assistant

El AI Content Assistant de LiteStartup te ayuda a escribir mejores emails más rápido.

### Funciones

- **Generación de asuntos**: La IA sugiere asuntos optimizados
- **Texto del email**: Genera el contenido del cuerpo del email
- **Pruebas A/B**: Crea variaciones para testear
- **Ajuste de tono**: Adapta el texto a la voz de tu marca
- **Optimización**: Sugerencias para mejorar la tasa de apertura

### Uso del asistente de IA

#### Generar asuntos

```
1. Click "AI Assistant" in email editor
2. Select "Generate Subject Lines"
3. Describe your email purpose
4. AI generates 5 variations
5. Click to use or regenerate
```

Ejemplo:
- Entrada: "Welcome email for new users"
- Sugerencias de la IA:
  - "Welcome! Get started in 3 minutes"
  - "You're in! Here's what's next"
  - "Welcome aboard - your journey starts now"

#### Generar texto del email

```
1. Click "AI Assistant"
2. Select "Generate Email Body"
3. Provide key points
4. Choose tone (professional, friendly, casual)
5. AI generates email content
6. Edit and customize as needed
```

#### Variaciones para pruebas A/B

```
1. Click "AI Assistant"
2. Select "Create A/B Variations"
3. AI generates alternative versions
4. Choose which to test
5. LiteStartup tracks performance
```

### Consejos de escritura con IA

- ✓ Sé específico sobre tu objetivo
- ✓ Menciona tu público objetivo
- ✓ Indica el tono deseado
- ✓ Incluye la información clave que debe aparecer
- ✓ Revisa y personaliza las sugerencias de la IA

## Automatización y workflows

Crea workflows inteligentes que envían emails automáticamente según el comportamiento del usuario.

### Tipos de workflow

#### Serie de bienvenida

Envía automáticamente una serie de emails a nuevos suscriptores.

```
1. Go to Automation → Workflows
2. Click "Create Workflow"
3. Select "Welcome Series"
4. Add emails (1-5 emails)
5. Set delays between emails
6. Activate workflow
```

Ejemplo de serie de bienvenida:
- Email 1: Welcome (inmediato)
- Email 2: Getting Started (1 día después)
- Email 3: Feature Highlight (3 días después)
- Email 4: Success Story (7 días después)

#### Campaña de re-engagement

Recupera suscriptores inactivos.

```
1. Create workflow
2. Select "Re-engagement"
3. Set inactivity threshold (e.g., 30 days)
4. Add re-engagement emails
5. Set follow-up actions
6. Activate
```

#### Campaña win-back

Dirigida a clientes que no han comprado recientemente.

```
1. Create workflow
2. Select "Win-back"
3. Define inactive period
4. Create compelling offer
5. Set retry schedule
6. Activate
```

#### Recuperación de carrito abandonado

Recuerda a los clientes los artículos que dejaron en el carrito.

```
1. Create workflow
2. Select "Abandoned Cart"
3. Set delay (e.g., 1 hour)
4. Customize email with product details
5. Add follow-up emails
6. Activate
```

### Disparadores del workflow

Los workflows pueden activarse por:

- **Acciones del usuario**: Signup, purchase, download
- **Basado en tiempo**: Specific date/time, anniversary
- **Comportamiento**: Opens, clicks, inactivity
- **Custom**: API triggers, webhooks

### Condiciones del workflow

Añade condiciones para controlar el flujo del workflow:

```
IF user.plan == "pro" THEN send_email("pro_features")
IF user.location == "US" THEN send_email("us_offer")
IF user.opened_count > 5 THEN send_email("vip_offer")
```

### Analíticas del workflow

Monitoriza el rendimiento del workflow:

- Emails sent
- Delivery rate
- Open rate
- Click rate
- Conversion rate
- Revenue generated

## Formularios de suscripción

Construye tu lista de suscriptores con formularios de registro incrustados.

### Crear formulario de suscripción

```
1. Go to Forms → Create Form
2. Choose form type:
   - Simple signup
   - Double opt-in
   - Custom fields
3. Design form
4. Add fields (email, name, custom fields)
5. Set confirmation message
6. Get embed code
```

### Tipos de formulario

#### Registro simple

Formulario de un solo paso para registros rápidos.

```html
<iframe src="https://forms.litestartup.com/simple/form_id"></iframe>
```

#### Doble opt-in

Confirmación en dos pasos para cumplimiento.

```
1. User enters email
2. Confirmation email sent
3. User clicks confirmation link
4. Subscription confirmed
```

#### Campos personalizados

Recopila información adicional:

```
- Email (required)
- Name (optional)
- Company (optional)
- Plan Interest (dropdown)
- Budget (multiple choice)
```

### Personalización del formulario

- **Colores**: Combina con tu marca
- **Texto**: Etiquetas y mensajes personalizados
- **Campos**: Añadir/eliminar campos
- **Redirección**: Redirigir después del registro
- **Webhook**: Enviar datos a tu sistema

### Incrustar formularios

#### En sitio web

```html
<div id="litestartup-form"></div>
<script>
  LiteStartup.loadForm('form_id', {
    container: '#litestartup-form',
    onSuccess: function() {
      console.log('User subscribed!');
    }
  });
</script>
```

#### En landing page

```html
<!-- Embed directly -->
<iframe src="https://forms.litestartup.com/form_id" 
        width="100%" height="500"></iframe>
```

#### Formulario emergente

```javascript
LiteStartup.showPopup('form_id', {
  trigger: 'exit', // Show on exit intent
  delay: 5000,     // Show after 5 seconds
  frequency: 'once' // Show once per session
});
```

## Gestión de lista de espera

Crea expectativa antes del lanzamiento con la gestión de lista de espera.

### Crear lista de espera

```
1. Go to Waitlist → Create Waitlist
2. Name your waitlist
3. Set launch date
4. Customize signup page
5. Generate signup link
6. Share with audience
```

### Funciones de la lista de espera

- **Seguimiento de referidos**: Los usuarios ganan posiciones al referir amigos
- **Códigos de invitación**: Envía códigos de invitación personalizados
- **Ranking**: Muestra la posición del usuario en la lista
- **Notificaciones por email**: Notifica cuando se invita
- **Analíticas**: Rastrea las fuentes de registro

### Programa de referidos

Permite que los usuarios obtengan acceso anticipado al referir amigos:

```
1. Enable referral in waitlist settings
2. Users get unique referral link
3. Each successful referral = 1 spot
4. Leaderboard shows top referrers
5. Send invites to top referrers first
```

### Enviar invitaciones

```
1. Go to Waitlist → Manage
2. Select users to invite
3. Generate invite codes
4. Send invite emails
5. Track acceptance
```

### Analíticas de la lista de espera

Monitoriza el crecimiento de la lista de espera:

- Registros totales
- Registros por referidos
- Tasa de conversión
- Principales referidores
- Fuentes de registro
- Distribución geográfica

## Plantillas de email

Crea y gestiona plantillas de email reutilizables.

### Biblioteca de plantillas

Accede a plantillas predefinidas:

- Emails de bienvenida
- Emails promocionales
- Emails transaccionales
- Plantillas de newsletter
- Invitaciones a eventos
- Restablecimiento de contraseña

### Crear plantilla personalizada

```
1. Go to Templates → Create
2. Choose layout
3. Add content blocks
4. Insert variables ({{name}}, {{company}})
5. Preview
6. Save template
```

### Variables de plantilla

Usa variables dinámicas en las plantillas:

```
Hello {{first_name}},

Welcome to {{company_name}}!

Your account: {{email}}
Plan: {{plan_type}}

Best regards,
The {{company_name}} Team
```

### Pruebas de plantilla

Prueba las plantillas antes de enviar:

```
1. Click "Send Test"
2. Enter test email
3. Review email
4. Make adjustments
5. Send to list
```

## Gestión de contactos

Organiza y gestiona tu lista de suscriptores.

### Importar contactos

#### CSV Import

```
1. Go to Contacts → Import
2. Upload CSV file
3. Map columns to fields
4. Review preview
5. Import
```

Formato CSV:
```
email,first_name,last_name,company,plan
john@example.com,John,Doe,Acme Inc,pro
jane@example.com,Jane,Smith,Tech Corp,free
```

#### Importación por API

```php
$contacts = [
    ['email' => 'john@example.com', 'name' => 'John'],
    ['email' => 'jane@example.com', 'name' => 'Jane']
];

foreach ($contacts as $contact) {
    $response = $client->post('/contacts', [
        'email' => $contact['email'],
        'name' => $contact['name']
    ]);
}
```

### Organizar contactos

#### Tags

Organiza contactos con tags:

```
- "vip"
- "trial_user"
- "paying_customer"
- "inactive"
- "churned"
```

#### Segmentos

Crea segmentos dinámicos:

```
- Active users (opened email in last 30 days)
- High-value customers (spent > $1000)
- Trial users (signup < 14 days ago)
- Inactive (no activity > 60 days)
```

### Datos del contacto

Guarda atributos personalizados:

```
- Company
- Job title
- Industry
- Location
- Plan type
- Signup date
- Last purchase
- Lifetime value
```

## Analíticas y reportes

Haz seguimiento del rendimiento del email con analíticas detalladas.

### Métricas de email

- **Sent**: Total de emails enviados
- **Delivered**: Entregados correctamente
- **Bounced**: Rebotes hard/soft
- **Opened**: Aperturas únicas
- **Clicked**: Clics únicos
- **Unsubscribed**: Solicitudes de baja
- **Spam**: Quejas de spam

### Analíticas de campañas

```
Campaign: Q1 Newsletter
├── Sent: 10,000
├── Delivered: 9,950 (99.5%)
├── Bounced: 50 (0.5%)
├── Opened: 4,500 (45.2%)
├── Clicked: 1,200 (12.0%)
├── Unsubscribed: 50 (0.5%)
└── Conversion: 150 (1.5%)
```

### Seguimiento de engagement

Haz seguimiento del engagement de usuarios individuales:

- Aperturas de email
- Clics en enlaces
- Historial de compras
- Puntuación de engagement
- Fecha de última actividad

### Reportes personalizados

Crea reportes personalizados:

```
1. Go to Reports → Create
2. Select metrics
3. Choose date range
4. Add filters
5. Generate report
6. Export as PDF/CSV
```

## Cumplimiento y entregabilidad

### Cumplimiento de GDPR

- ✓ Gestión de consentimiento
- ✓ Exportación de datos
- ✓ Derecho al olvido
- ✓ Plantillas de política de privacidad
- ✓ Logs de auditoría

### Cumplimiento CAN-SPAM

- ✓ Opción clara de baja
- ✓ Información del remitente precisa
- ✓ Asuntos honestos
- ✓ Dirección física obligatoria
- ✓ Baja respetada en un plazo de 10 días

### Funciones de entregabilidad

- ✓ Configuración SPF/DKIM/DMARC
- ✓ Verificación de dominio
- ✓ Gestión de rebotes
- ✓ Pruebas de spam
- ✓ Monitorización de reputación IP

## Integración

### Eventos de webhook

Recibe notificaciones en tiempo real:

- Email sent
- Email delivered
- Email opened
- Link clicked
- Email bounced
- Unsubscribed

### Integración por API

Integra con tu aplicación:

```php
// Send email via API
$response = $client->post('/emails/send', [
    'to' => 'user@example.com',
    'from' => 'hello@yourdomain.com',
    'subject' => 'Welcome!',
    'html' => '<h1>Hello</h1>'
]);
```

### Integraciones con terceros

Conecta con herramientas populares:

- Zapier
- Make (Integromat)
- IFTTT
- Slack
- Discord
- Webhooks personalizados

---

**Siguiente:** Revisa [Ejemplos de código](/es/04-examples.md) o [Precios y planes](/es/05-pricing.md)!

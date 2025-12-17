# Guia de recursos

Explore todos os recursos poderosos que o LiteStartup oferece para ajudar sua startup a ter sucesso.

## Workmail - E-mail corporativo

O LiteStartup inclui funcionalidades de e-mail corporativo integradas, eliminando a necessidade de serviços separados como o Google Workspace.

### O que é Workmail?

Workmail é um serviço completo de e-mail corporativo integrado diretamente ao LiteStartup. Envie e receba e-mails do seu domínio personalizado sem assinaturas adicionais.

### Benefícios

- **Economize**: $72-144 por ano por membro da equipe (vs. Google Workspace)
- **Plataforma unificada**: E-mail e marketing em um só lugar
- **Imagem profissional**: Use seu domínio personalizado
- **Recursos completos**: Encaminhamento, aliases, respostas automáticas

### Primeiros passos com Workmail

1. Vá para **Settings** → **Workmail**
2. Adicione seu domínio (por exemplo, `hello@yourdomain.com`)
3. Verifique os registros DNS
4. Crie contas de e-mail para os membros da equipe
5. Comece a enviar e receber e-mails

### Criar contas de e-mail

```
1. Click "Add Email Account"
2. Enter username (e.g., "john")
3. Set password
4. Assign to team member
5. Click "Create"
```

O endereço de e-mail será: `john@yourdomain.com`

### Encaminhamento de e-mail

Configure o encaminhamento automático:

```
1. Go to email account settings
2. Click "Forwarding"
3. Enter forwarding address
4. Confirm forwarding
5. Emails now forward automatically
```

### Respostas automáticas

Configure respostas automáticas:

```
1. Go to email account settings
2. Click "Auto-Responder"
3. Enable auto-responder
4. Set message and date range
5. Save
```

## AI Content Assistant

O AI Content Assistant do LiteStartup ajuda você a escrever e-mails melhores, mais rápido.

### Recursos

- **Geração de assunto**: a IA sugere linhas de assunto otimizadas
- **Texto do e-mail**: gere conteúdo para o corpo do e-mail
- **Testes A/B**: crie variações para testes
- **Ajuste de tom**: combine com a voz da sua marca
- **Otimização**: sugestões para melhorar taxas de abertura

### Como usar o AI Assistant

#### Gerar linhas de assunto

```
1. Click "AI Assistant" in email editor
2. Select "Generate Subject Lines"
3. Describe your email purpose
4. AI generates 5 variations
5. Click to use or regenerate
```

Exemplo:
- Entrada: "Welcome email for new users"
- Sugestões da IA:
  - "Welcome! Get started in 3 minutes"
  - "You're in! Here's what's next"
  - "Welcome aboard - your journey starts now"

#### Gerar texto do e-mail

```
1. Click "AI Assistant"
2. Select "Generate Email Body"
3. Provide key points
4. Choose tone (professional, friendly, casual)
5. AI generates email content
6. Edit and customize as needed
```

#### Variações de teste A/B

```
1. Click "AI Assistant"
2. Select "Create A/B Variations"
3. AI generates alternative versions
4. Choose which to test
5. LiteStartup tracks performance
```

### Dicas de escrita com IA

- ✓ Seja específico sobre seu objetivo
- ✓ Mencione seu público-alvo
- ✓ Defina o tom desejado
- ✓ Informe os pontos-chave a incluir
- ✓ Revise e personalize as sugestões da IA

## Automação e fluxos de trabalho

Crie fluxos inteligentes que enviam e-mails automaticamente com base no comportamento do usuário.

### Tipos de workflow

#### Série de boas-vindas

Envie automaticamente uma sequência de e-mails para novos assinantes.

```
1. Go to Automation → Workflows
2. Click "Create Workflow"
3. Select "Welcome Series"
4. Add emails (1-5 emails)
5. Set delays between emails
6. Activate workflow
```

Exemplo de série de boas-vindas:
- E-mail 1: Boas-vindas (imediato)
- E-mail 2: Primeiros passos (1 dia depois)
- E-mail 3: Destaque de recurso (3 dias depois)
- E-mail 4: Caso de sucesso (7 dias depois)

#### Campanha de reengajamento

Recupere assinantes inativos.

```
1. Create workflow
2. Select "Re-engagement"
3. Set inactivity threshold (e.g., 30 days)
4. Add re-engagement emails
5. Set follow-up actions
6. Activate
```

#### Campanha de win-back

Segmente clientes que não compram há algum tempo.

```
1. Create workflow
2. Select "Win-back"
3. Define inactive period
4. Create compelling offer
5. Set retry schedule
6. Activate
```

#### Recuperação de carrinho abandonado

Lembre clientes sobre itens deixados no carrinho.

```
1. Create workflow
2. Select "Abandoned Cart"
3. Set delay (e.g., 1 hour)
4. Customize email with product details
5. Add follow-up emails
6. Activate
```

### Gatilhos de workflow

Workflows podem ser acionados por:

- **Ações do usuário**: cadastro, compra, download
- **Baseado em tempo**: data/hora específica, aniversário
- **Comportamental**: aberturas, cliques, inatividade
- **Personalizado**: gatilhos por API, webhooks

### Condições do workflow

Adicione condições para controlar o fluxo do workflow:

```
IF user.plan == "pro" THEN send_email("pro_features")
IF user.location == "US" THEN send_email("us_offer")
IF user.opened_count > 5 THEN send_email("vip_offer")
```

### Analytics de workflow

Monitore o desempenho do workflow:

- E-mails enviados
- Taxa de entrega
- Taxa de abertura
- Taxa de cliques
- Taxa de conversão
- Receita gerada

## Formulários de assinatura

Crie sua lista de assinantes com formulários de cadastro incorporáveis.

### Criar formulário de assinatura

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

### Tipos de formulário

#### Cadastro simples

Formulário de uma etapa para cadastros rápidos.

```html
<iframe src="https://forms.litestartup.com/simple/form_id"></iframe>
```

#### Duplo opt-in

Confirmação em duas etapas para conformidade.

```
1. User enters email
2. Confirmation email sent
3. User clicks confirmation link
4. Subscription confirmed
```

#### Campos personalizados

Colete informações adicionais:

```
- Email (required)
- Name (optional)
- Company (optional)
- Plan Interest (dropdown)
- Budget (multiple choice)
```

### Personalização do formulário

- **Cores**: combine com sua marca
- **Texto**: rótulos e mensagens personalizados
- **Campos**: adicionar/remover campos
- **Redirect**: redirecionar após o cadastro
- **Webhook**: enviar dados para seu sistema

### Incorporar formulários

#### No site

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

#### Na landing page

```html
<!-- Embed directly -->
<iframe src="https://forms.litestartup.com/form_id" 
        width="100%" height="500"></iframe>
```

#### Formulário popup

```javascript
LiteStartup.showPopup('form_id', {
  trigger: 'exit', // Show on exit intent
  delay: 5000,     // Show after 5 seconds
  frequency: 'once' // Show once per session
});
```

## Gestão de waitlist

Crie expectativa antes do lançamento com gestão de waitlist.

### Criar waitlist

```
1. Go to Waitlist → Create Waitlist
2. Name your waitlist
3. Set launch date
4. Customize signup page
5. Generate signup link
6. Share with audience
```

### Recursos da waitlist

- **Rastreamento de indicação**: usuários ganham posições ao indicar amigos
- **Códigos de convite**: envie códigos de convite personalizados
- **Ranking**: mostre a posição do usuário na waitlist
- **Notificações por e-mail**: notifique quando for convidado
- **Analytics**: acompanhe as fontes de cadastro

### Programa de indicações

Permita que usuários ganhem acesso antecipado indicando amigos:

```
1. Enable referral in waitlist settings
2. Users get unique referral link
3. Each successful referral = 1 spot
4. Leaderboard shows top referrers
5. Send invites to top referrers first
```

### Enviar convites

```
1. Go to Waitlist → Manage
2. Select users to invite
3. Generate invite codes
4. Send invite emails
5. Track acceptance
```

### Analytics da waitlist

Monitore o crescimento da waitlist:

- Total de cadastros
- Cadastros por indicação
- Taxa de conversão
- Principais indicantes
- Fontes de cadastro
- Distribuição geográfica

## Templates de e-mail

Crie e gerencie templates de e-mail reutilizáveis.

### Biblioteca de templates

Acesse templates prontos:

- E-mails de boas-vindas
- E-mails promocionais
- E-mails transacionais
- Templates de newsletter
- Convites para eventos
- Redefinição de senha

### Criar template personalizado

```
1. Go to Templates → Create
2. Choose layout
3. Add content blocks
4. Insert variables ({{name}}, {{company}})
5. Preview
6. Save template
```

### Variáveis de template

Use variáveis dinâmicas em templates:

```
Hello {{first_name}},

Welcome to {{company_name}}!

Your account: {{email}}
Plan: {{plan_type}}

Best regards,
The {{company_name}} Team
```

### Teste de template

Teste templates antes de enviar:

```
1. Click "Send Test"
2. Enter test email
3. Review email
4. Make adjustments
5. Send to list
```

## Gestão de contatos

Organize e gerencie sua lista de assinantes.

### Importar contatos

#### Importação por CSV

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

#### Importação via API

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

### Organizar contatos

#### Tags

Organize contatos com tags:

```
- "vip"
- "trial_user"
- "paying_customer"
- "inactive"
- "churned"
```

#### Segmentos

Crie segmentos dinâmicos:

```
- Active users (opened email in last 30 days)
- High-value customers (spent > $1000)
- Trial users (signup < 14 days ago)
- Inactive (no activity > 60 days)
```

### Dados do contato

Armazene atributos personalizados:

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

## Analytics e relatórios

Acompanhe o desempenho de e-mails com analytics detalhado.

### Métricas de e-mail

- **Sent**: total de e-mails enviados
- **Delivered**: entregues com sucesso
- **Bounced**: bounces hard/soft
- **Opened**: aberturas únicas
- **Clicked**: cliques únicos
- **Unsubscribed**: solicitações de descadastro
- **Spam**: reclamações de spam

### Analytics de campanhas

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

### Rastreamento de engajamento

Acompanhe o engajamento individual de usuários:

- Aberturas de e-mail
- Cliques em links
- Histórico de compras
- Pontuação de engajamento
- Data da última atividade

### Relatórios personalizados

Crie relatórios personalizados:

```
1. Go to Reports → Create
2. Select metrics
3. Choose date range
4. Add filters
5. Generate report
6. Export as PDF/CSV
```

## Conformidade e entregabilidade

### Conformidade com GDPR

- ✓ Gestão de consentimento
- ✓ Exportação de dados
- ✓ Direito ao esquecimento
- ✓ Templates de política de privacidade
- ✓ Logs de auditoria

### Conformidade com CAN-SPAM

- ✓ Opção clara de descadastro
- ✓ Informações corretas do remetente
- ✓ Linhas de assunto honestas
- ✓ Endereço físico obrigatório
- ✓ Descadastro atendido em até 10 dias

### Recursos de entregabilidade

- ✓ Configuração de SPF/DKIM/DMARC
- ✓ Verificação de domínio
- ✓ Gestão de bounces
- ✓ Testes de spam
- ✓ Monitoramento de reputação de IP

## Integrações

### Eventos de webhook

Receba notificações em tempo real:

- E-mail enviado
- E-mail entregue
- E-mail aberto
- Link clicado
- E-mail com bounce
- Descadastrado

### Integração via API

Integre com seu aplicativo:

```php
// Send email via API
$response = $client->post('/emails/send', [
    'to' => 'user@example.com',
    'from' => 'hello@yourdomain.com',
    'subject' => 'Welcome!',
    'html' => '<h1>Hello</h1>'
]);
```

### Integrações com terceiros

Conecte-se com ferramentas populares:

- Zapier
- Make (Integromat)
- IFTTT
- Slack
- Discord
- Webhooks personalizados

---

**Próximo:** Confira [Code Examples](/pt/04-examples.md) ou [Pricing & Plans](/pt/05-pricing.md)!

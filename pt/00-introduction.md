# Introdução ao LiteStartup
 
 LiteStartup (apresentado no site como *Lite Email for Startups*) é uma **plataforma de serviços de e-mail orientada por IA** para startups que reúne **Workmail (e-mail corporativo)**, **e-mail transacional** e **e-mail de marketing** em um único produto, com uma API REST simples para integrar em minutos.
 
 ## O que é o LiteStartup?
 
 LiteStartup é uma plataforma de e-mail SaaS para startups. Em uma frase:
 
 - **Um modelo de serviço de e-mail orientado por IA** que simplifica seu fluxo de e-mail (conteúdo, automação e entrega)
 - **Uma pilha unificada para e-mail corporativo + e-mail transacional + e-mail de marketing**, reduzindo a dependência de vários fornecedores
 - **Integração amigável para desenvolvedores** via APIs RESTful padrão (sem SDKs complexos)
 
 Diferente das plataformas tradicionais de e-mail marketing que cobram por contato, o LiteStartup enfatiza **pay per email sent**, então você paga pelo que envia — não por armazenar contatos.
 
 ## O que nos torna diferentes
 
 ### Workmail como o Gmail
 A ÚNICA plataforma de e-mail marketing com e-mail corporativo como `support@yourcompany.com` em minutos.
 
 ### AI Content Assistant
 A IA gera e-mails de marketing e variações para testes A/B para acelerar a escrita e a iteração.
 
 ### Acessível
 Pay per email sent, não por contato.
 
 - **Pro**: $20/month for 110,000 emails/month
 - **Overage**: $0.20 per 1,000 emails after limit
 
 ### Enterprise Infrastructure
 Criado por engenheiros da AWS e do Google Cloud. 99.9% de uptime com conformidade SOC2 e GDPR.
 
 ### Free Email Notifications
 Obtenha um e-mail gratuito como `yourname@litestartup.net` para alertas, relatórios e atualizações na sua caixa de entrada preferida.
 
 ### AI Website Builder
 Converse com a IA para criar landing pages, páginas de waitlist, newsletters e blogs. Sem precisar programar.
 
 ### Ticket + Live Chat
 Gerencie conversas com clientes com tickets (via e-mail) e um widget de live chat em tempo real.
 
 ### AI Automation
 Automação sempre ativa: e-mails de boas-vindas, follow-up e prospecção, com captura de leads e fluxos de crescimento integrados.
 
 ## Quem deve usar o LiteStartup?
 
 O LiteStartup é ideal para:
 
 - **Startups em estágio inicial** construindo sua primeira base de clientes
 - **Produtos SaaS** que precisam de e-mail transacional + e-mail de marketing em um só lugar
 - **Times de growth** que querem conteúdo com suporte de IA e experimentos mais rápidos
 - **Times de produto** gerenciando landing pages e waitlists
 - **Desenvolvedores** que preferem APIs REST simples com poucas dependências
 - **Times que evitam lock-in de fornecedor** e querem a opção de trocar de provedor depois
 
 ## Como o LiteStartup funciona
 
 ### 1. Cadastre-se
 Crie uma conta e comece com o plano Free (10,000 emails/month).
 
 ### 2. Obtenha as credenciais de API
 Recupere sua chave de API no dashboard.
 
 ### 3. Integre
 Envie e-mails por chamadas de API RESTful. Funciona com qualquer linguagem ou framework.
 
 ### 4. Envie e-mails
 Envie e-mails transacionais, campanhas de marketing ou fluxos automatizados.
 
 ### 5. Acompanhe e otimize
 Monitore análises básicas e itere com melhorias assistidas por IA.
 
 ## LiteStartup vs. Plataformas tradicionais de e-mail
 
 | Recurso | LiteStartup | Plataformas tradicionais |
 |---|---|---|
 | Workmail (Business Email) | ✓ Included | ✗ Separate service |
 | AI Content Assistant | ✓ Yes | ✗ No |
 | Modelo de preço | Per email sent | Por contato |
 | Tempo de configuração | 5 minutes | 30+ minutes |
 | API Integration | ✓ Simple REST API | ✓ Complex SDKs |
 | Vendor Lock-in | ✗ None | ✓ Yes |
 | Free Tier | 10K emails/month | Limited |
 | Uptime (website) | 99.9% | 99.9% |
 
 ## Primeiros passos
 
 Pronto para começar a enviar e-mails? Veja o que fazer a seguir:
 
 1. **[Getting Started Guide](/pt/01-getting-started.md)** - Cadastre-se e envie seu primeiro e-mail em minutos
 2. **[API Reference](/pt/02-api-reference.md)** - Documentação completa da API e endpoints
 3. **[Features Guide](/pt/03-features.md)** - Explore todos os recursos em detalhes
 4. **[Code Examples](/pt/04-examples.md)** - Exemplos de implementação em várias linguagens
 5. **[Pricing & Plans](/pt/05-pricing.md)** - Entenda preços e cobrança
 
 ## Exemplo de início rápido
 
 Envie seu primeiro e-mail com apenas algumas linhas de código:

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

 ## Principais benefícios
 
 - **Menor custo** - Pay per email sent, não por contato
 - **Maior produtividade** - AI Content Assistant e AI Automation reduzem trabalho manual
 - **Kit tudo-em-um** - Workmail + envio + landing pages/waitlists + ticket/live chat
 - **Integração rápida** - API REST sem dependências de SDK complexas
 - **Menos lock-in** - APIs padrão tornam mais fácil trocar de provedor
 
 ## Suporte e recursos
 
 - **Documentation**: Guias completos e referência de API
 - **Code Examples**: Exemplos prontos para uso em várias linguagens
 - **Community**: Conecte-se com outros usuários do LiteStartup
 
 ## Próximos passos
 
 - Comece com o [Getting Started Guide](/pt/01-getting-started.md)
 - Explore o [API Reference](/pt/02-api-reference.md)
 - Veja os [Code Examples](/pt/04-examples.md) na sua linguagem
 - Confira [Pricing & Plans](/pt/05-pricing.md) para encontrar o plano certo

---
 
 **Pronto para enviar seu primeiro e-mail?** Comece pelo [Getting Started Guide](/pt/01-getting-started.md).

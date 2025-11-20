# Introdução ao LiteStartup

O LiteStartup é uma plataforma de email marketing inteligente construída especificamente para startups. Combina o poder de um serviço de email empresarial (workmail), geração de conteúdo impulsionada por IA e entrega confiável de emails em uma plataforma acessível e fácil de usar.

## O que é o LiteStartup?

O LiteStartup é uma plataforma de email SaaS (Software as a Service) que ajuda startups a:

- **Enviar emails de marketing** com assistência de conteúdo de IA integrada
- **Gerenciar email empresarial** com funcionalidade de workmail (como o Gmail)
- **Automatizar campanhas** com fluxos de trabalho inteligentes
- **Construir listas de assinantes** com formulários de inscrição incorporados
- **Gerenciar listas de espera** antes do lançamento do produto
- **Integrar facilmente** via API REST em minutos

Ao contrário das plataformas de email marketing tradicionais que cobram por contato, o LiteStartup cobra por email enviado. Isso significa que você pode importar contatos ilimitados e pagar apenas pelos emails que realmente enviar.

## Principais Recursos

### Workmail como o Gmail
A única plataforma de email marketing com email empresarial integrado. Não há necessidade de assinaturas separadas do Google Workspace. Economize de $72 a $144 por ano por membro da equipe.

### Assistente de Conteúdo de IA
Gere automaticamente linhas de assunto, textos de email e variações de teste A/B. Escreva emails 10x mais rápido com taxas de abertura 10x melhores. Da ideia ao envio em apenas 1 minuto.

### Preços Acessíveis
- **Plano Gratuito**: 10.000 emails por mês
- **Plano Pro**: 110.000 emails por mês por $20/mês
- **Pagamento por uso**: $0,20 por 1.000 emails após o limite do seu plano
- **Sem taxas por contato**: Importe 100 mil contatos, pague apenas pelos emails enviados

### Contatos Ilimitados
Importe e gerencie contatos ilimitados. Pague apenas pelos emails enviados, não pelo armazenamento de contatos. Propriedade total dos dados com importação/exportação CSV.

### Infraestrutura Empresarial
Construído por engenheiros da AWS e Google Cloud. 99,99% de tempo de atividade com conformidade SOC2 e GDPR. Preços de startup com confiabilidade de nível empresarial.

### Automação Inteligente
- **Gerenciamento de Lista de Espera**: Colete emails, envie códigos de convite, converta a lista de espera em clientes automaticamente
- **Formulários de Assinatura**: Formulários de inscrição incorporáveis com double opt-in, incorpore em qualquer lugar em 30 segundos
- **Automação de IA**: Fluxos de trabalho inteligentes acionados pelo comportamento do usuário - séries de boas-vindas, reengajamento, campanhas de reconquista

### Zero Bloqueio de Fornecedor (Vendor Lock-in)
Use APIs REST padrão. Mude de provedor a qualquer momento sem alterações de código. Funciona com qualquer linguagem de programação ou framework.

## Quem deve usar o LiteStartup?

O LiteStartup é ideal para:

- **Startups em estágio inicial** construindo sua primeira base de clientes
- **Empresas SaaS** que precisam de email transacional confiável
- **Equipes de crescimento** executando campanhas de email marketing
- **Equipes de produto** gerenciando listas de espera e acesso antecipado
- **Desenvolvedores** que desejam uma integração de API simples sem complexidade
- **Empresas** procurando soluções de email acessíveis sem bloqueio de fornecedor

## Como o LiteStartup Funciona

### 1. Cadastre-se
Crie uma conta gratuita e comece imediatamente com 10.000 emails gratuitos por mês.

### 2. Obtenha Credenciais de API
Recupere sua chave de API do painel em segundos.

### 3. Integre
Use a API REST simples para enviar emails do seu aplicativo. Funciona com qualquer linguagem de programação.

### 4. Envie Emails
Comece a enviar emails transacionais, campanhas de marketing ou fluxos de trabalho automatizados.

### 5. Rastreie e Otimize
Monitore a entrega, aberturas, cliques e use sugestões de IA para melhorar o desempenho.

## LiteStartup vs. Plataformas de Email Tradicionais

| Recurso | LiteStartup | Plataformas Tradicionais |
|---------|-------------|----------------------|
| Workmail (Email Empresarial) | ✓ Incluído | ✗ Serviço separado |
| Assistente de Conteúdo de IA | ✓ Sim | ✗ Não |
| Modelo de Preços | Por email enviado | Por contato |
| Tempo de Configuração | 5 minutos | 30+ minutos |
| Integração de API | ✓ API REST Simples | ✓ SDKs Complexos |
| Bloqueio de Fornecedor | ✗ Nenhum | ✓ Sim |
| Nível Gratuito | 10K emails/mês | Limitado |
| SLA de Tempo de Atividade | 99,99% | 99,9% |

## Começando

Pronto para começar a enviar emails? Aqui está o que fazer a seguir:

1. **[Guia de Início](01-getting-started.md)** - Cadastre-se e envie seu primeiro email em 5 minutos
2. **[Referência da API](02-api-reference.md)** - Documentação completa da API e endpoints
3. **[Guia de Recursos](03-features.md)** - Explore todos os recursos em detalhes
4. **[Exemplos de Código](04-examples.md)** - Exemplos de implementação em várias linguagens
5. **[Preços e Planos](05-pricing.md)** - Entenda os preços e faturamento

## Exemplo de Início Rápido

Envie seu primeiro email em apenas algumas linhas de código:

```bash
curl -X POST https://api.litestartup.com/emails/send \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "to": "user@example.com",
    "from": "hello@yourdomain.com",
    "subject": "Welcome to LiteStartup!",
    "html": "<h1>Hello!</h1><p>Welcome to our platform.</p>",
    "text": "Hello! Welcome to our platform."
  }'
```

## Principais Benefícios

✓ **Economize Dinheiro** - Pague apenas pelos emails enviados, não por contato
✓ **Economize Tempo** - A IA gera conteúdo, a configuração leva 5 minutos
✓ **Confiabilidade Empresarial** - 99,99% de tempo de atividade, compatível com SOC2 e GDPR
✓ **Sem Bloqueio** - API REST padrão, mude a qualquer momento
✓ **Construído para Startups** - Preços acessíveis, recursos amigáveis para startups
✓ **Fácil Integração** - Funciona com qualquer linguagem ou framework

## Suporte e Recursos

- **Documentação**: Guias completos e referência da API
- **Exemplos de Código**: Exemplos prontos para uso em várias linguagens
- **Status da API**: Status em tempo real da nossa infraestrutura
- **Comunidade**: Conecte-se com outros usuários do LiteStartup

## Próximos Passos

- Comece com o [Guia de Início](01-getting-started.md)
- Explore a [Referência da API](02-api-reference.md)
- Revise [Exemplos de Código](04-examples.md) para sua linguagem de programação
- Verifique [Preços e Planos](05-pricing.md) para encontrar o plano certo

---

**Pronto para enviar seu primeiro email?** Comece com o [Guia de Início](01-getting-started.md)!

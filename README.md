# HORUS Barber SaaS

SaaS multi-tenant para gestão de barbearias construído com **Next.js 14 + Supabase + Stripe + WhatsApp API**.

## Módulos implementados

- Multi-tenant com isolamento por `tenant_id` e base para RLS.
- Painel moderno com KPIs e gráfico de faturamento.
- Página pública por barbearia em `/barbearia/[slug]` para agendamento.
- Estrutura para agendamentos, CRM, comandas, estoque, fidelidade, assinatura e relatórios.
- Webhook Stripe para sincronizar assinatura SaaS.
- Endpoint para envio de notificação WhatsApp.
- Schema SQL completo com tabelas principais + extras (QR check-in, avaliações, notificações internas, multi-unidades).

## Setup

1. Instale dependências:

```bash
npm install
```

2. Configure variáveis de ambiente:

```bash
cp .env.example .env.local
```

3. Rode local:

```bash
npm run dev
```

4. Aplique o schema no Supabase:

- Execute `supabase/schema.sql` no SQL editor.

## Arquitetura de produção

- **Frontend/Backend BFF:** Next.js 14 (App Router + API Routes) hospedado na Vercel.
- **Banco/Auth/Storage:** Supabase.
- **Pagamentos:** Stripe (ou trocar para Mercado Pago no mesmo padrão de webhook).
- **Mensageria:** endpoint genérico para provedores de WhatsApp Cloud API.
- **Segurança:** RLS + JWT claims com `tenant_id` e `role`.

## Próximos passos

- Implementar telas CRUD por módulo com React Query + Supabase.
- Aplicar políticas RLS para todas as tabelas.
- Adicionar jobs (lembrete de agendamento, aniversário, campanhas).
- Integrar upload de logo e assets no Supabase Storage.
- Evoluir observabilidade (Sentry, Logflare, métricas de API).

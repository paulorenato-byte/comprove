# COMPROVE REC: diagnóstico do funil (01/11/2026)

Fontes: `rec_eventos`, `rec_diagnosticos`, `rec_li_leads`, `rec_ig_leads`, `rec_vendas` (Supabase do Rito), de 20/10 a 31/10/2026, mais a análise de especialista de 27/10.

## Vendas

**Zero.** As 14 linhas de `rec_vendas` são eventos de teste da Hotmart (20/10).

## Funil do site

| Etapa | Sessões | Conversão |
|---|---|---|
| Visita ao diagnóstico | 676 | |
| Começou o diagnóstico | 23 | 3,4% das visitas |
| Chegou ao resultado | 20 | 87% de quem começou |
| Foi para a página de vendas | 9 | 45% de quem teve resultado |
| Abriu o checkout | 2 | |
| Comprou | 0 | |
| Visita direta à página de vendas | 511 | 4 assistiram ao trecho de aula |

**O vazamento principal é a entrada do diagnóstico (3,4%).** Quem começa termina. O formulário pede contato antes das perguntas e abre com as perguntas mais difíceis (clientes por mês e ticket).

## De onde vêm os diagnósticos reais (sem testes)

| Origem | Sessões no site | Diagnósticos |
|---|---|---|
| E-mail 1 | 247 | 9 |
| E-mail 2 | 175 | 3 |
| Meta Ads | 184 | 1 |
| LinkedIn (DM e prospecção) | 16 | 4 |
| Sem origem | | 4 |

**O e-mail é o canal que traz diagnóstico.** Meta Ads frio quase não traz: 184 sessões e 1 diagnóstico. Pela análise de 27/10, parte dos diagnósticos do e-mail é de escritórios grandes (16 pessoas ou mais), que são perfil de DUO, não de REC.

## Prospecção ativa

| Canal | Enviados | Respostas | Situação em 01/11 |
|---|---|---|---|
| LinkedIn | ~50 mensagens (semana de 19/10) | 12 (24%) | Último convite em 28/10; **162 leads na fila sem convite** |
| Instagram | 155 DMs | **0** | Última DM em 30/10; **171 na fila sem DM** |
| WhatsApp automático após o diagnóstico | 3 mensagens-modelo para cada um | 0 respostas escritas | Uma falha por bloqueio da Meta a mensagem de marketing |

## Conclusões para o roadmap

1. **Inverter o diagnóstico** (etapa 3): perguntas leves primeiro, contato só no fim para liberar a nota.
2. **Disparos sem parar** (etapa 2): o LinkedIn responde (24%), mas a fila parou. Instagram fica para o teste com a nova promessa (etapa 8).
3. **Nova promessa** (etapa 4): o diagnóstico qualifica, mas não vende. Venda acima de R$ 1 mil para advogado fecha em conversa.
4. **Separar público**: escritório grande vai para a conversa de DUO.
5. **Meta Ads só em remarketing** (etapa 6).
6. **Corrigir o título do site**: a prévia do link mostra "Lovable App" (dado de 27/10; conferir antes de corrigir).

# Duas rotinas para o BSC da 3Motion (para o Cowork criar)

As duas precisam dos conectores Supabase e Google Drive, por isso devem ser criadas pelo Cowork ou pela tela de rotinas do claude.ai. Uma tarefa criada pelo Claude Code fica sem conectores.

Banco: Supabase `dutantiolnlidwxdgdyy`. Cliente da própria 3Motion: `cliente_id = '0f76c2e9-b273-46c0-9adf-666d3afdd50b'`.

---

## Rotina 1: conciliação da prospecção com os OKRs

**O que faz:** toda semana, lança o realizado da prospecção nos OKRs do BSC, para que o rito de segunda leia a porcentagem. O Paulo nunca lança número à mão.

**Quando:** segunda às 16h47 (uma hora antes da leitura do rito, que roda no banco às 17h47). Lança a semana que terminou no domingo.

**Onde gravar:**
- Tabelas: `okrs` → `okr_key_results` → `okr_semanas` (coluna `valor_real`).
- Semana do Rito: `seg_ant` = segunda da semana lida; `mes = to_char(seg_ant,'YYYY-MM')`; `semana = floor((extract(day from seg_ant)+6)/7)`.
- Cada OKR é identificado pelo início do campo `okrs.lista`; cada resultado-chave, por `okr_key_results.ordem`.

```sql
update okr_semanas s set valor_real = <número>
from okr_key_results k join okrs o on o.id = k.okr_id
where s.key_result_id = k.id
  and o.cliente_id = '0f76c2e9-b273-46c0-9adf-666d3afdd50b' and o.status = 'ativo'
  and o.lista like '<início da lista>%' and k.ordem = <ordem>
  and s.mes = '<YYYY-MM>' and s.semana = <n>;
```

**Os 9 OKRs e as etapas (ordem: título):**

| Início de `lista` | Etapas |
|---|---|
| `Escritórios · ELO e DUO \| Prospecção ativa (L` (LinkedIn) | 1 Leads qualificados · 2 Pedido de conexão · 3 Aceites · 4 Convites para reunião · 5 Respostas · 6 Reunião agendada · 7 Reunião feita · 8 Propostas apresentadas · 9 Contrato fechado |
| `Escritórios · ELO e DUO \| Prospecção ativa (E` (e-mail) | 1 Qualificação · 2 Envios · 3 Aberturas · 4 Clique no link · 5 Respostas · 6 Reunião agendada · 7 Reunião feita · 8 Propostas apresentadas · 9 Contrato fechado |
| `COMPROVE REC · LinkedIn` | 1 Leads qualificados · 2 Pedido de conexão · 3 Aceites · 4 Mensagem enviada · 5 Respostas · 6 Diagnóstico feito · 7 Venda do REC |
| `COMPROVE REC · E-mail` | 1 Qualificação · 2 Envios · 3 Aberturas · 4 Clique no link · 5 Respostas · 6 Diagnóstico feito · 7 Venda do REC |
| `COMPROVE REC · Instagram` | 1 Perfis qualificados · 2 DMs enviadas · 3 Respostas · 4 Diagnóstico feito · 5 Venda do REC |
| `Escolas e outros nichos` | igual ao LinkedIn de escritórios |
| `Marketing comercial` | 1 Impressões no perfil do Paulo · 2 Comentários recebidos · 3 Cliques no link (página) · 4 Conversas comerciais originadas do conteúdo · 5 Reuniões originadas do marketing |
| `Audiência · REC` | 1 Seguidores novos no Instagram · 2 Inscritos novos no YouTube · 3 Visualizações no YouTube · 4 Seguidores novos no LinkedIn · 5 Diagnósticos iniciados |
| `Instituições · REC` | 1 Instituições mapeadas · 2 Líderes contatados · 3 Respostas · 4 Reuniões com líderes · 5 Propostas apresentadas · 6 Pacotes vendidos |

**Fontes já no banco (sem navegador):**
- LinkedIn (impressões, comentários, cliques, seguidores): `li_metricas_dia`.
- REC no LinkedIn e no Instagram: `rec_li_leads` e `rec_ig_leads` (datas de convite, aceite, mensagem, DM, resposta).
- Diagnósticos: `rec_diagnosticos`. Vendas: `rec_vendas` (ignorar eventos de teste).
- Funil de escritórios e reuniões: `negocios` (pela `origem`) e `negocio_movimentacoes`.
- Instagram e YouTube (seguidores, inscritos, visualizações): só pelo navegador, numa rotina no computador.

**Regras:** lançar só número com fonte; se uma etapa não tem fonte, deixar `valor_real` nulo e registrar o motivo; nunca alterar `valor_definido` (meta). Registrar o que lançou em `central_diario`.

---

## Rotina 2: construção dos roadmaps do BSC

> **Substituída em 03/11 (Paulo):** a rotina que vale é a chamada diária. Toda noite de domingo a quinta, às 18h37, o banco manda no WhatsApp do Paulo as etapas que vencem no próximo dia útil e as vencidas (função `bsc_etapas_amanha_3motion()`, job `bsc-etapas-amanha-3motion`). Paulo e Claude executam juntos numa conversa. Desde 03/11 cada etapa chega numa mensagem própria (até 4 por dia), com a sugestão de execução escrita pelo Claude com antecedência e guardada na tabela `bsc_etapa_sugestoes` (55 etapas até 30/11). O texto abaixo fica só como referência.

**O que faz:** executa as etapas dos roadmaps que estão com o Claude, para que os 20 objetivos de processo andem sem depender de uma conversa aberta.

**Quando:** dias úteis às 6h17.

**Passo 1, o que fazer hoje:**
```sql
select b.ordem, b.objetivo, c.id, c.ordem_manual, c.descricao, c.prazo, c.responsavel
from roadmap_checkpoints c
join roadmap_items r on r.id = c.roadmap_item_id
join bsc_objetivos b on b.id = r.bsc_objetivo_id
where b.cliente_id = '0f76c2e9-b273-46c0-9adf-666d3afdd50b' and b.concluido_em is null
  and c.status <> 'completo' and c.responsavel ilike '%Claude%'
  and c.prazo <= (now() at time zone 'America/Sao_Paulo')::date + 2
order by c.prazo, b.ordem, c.ordem_manual
limit 2;
```
Só pega a etapa se as etapas anteriores do mesmo roadmap estiverem completas, ou se forem do Paulo e esta não depender delas.

**Passo 2, executar:** produzir a entrega descrita na etapa (documento, lista, proposta, texto, levantamento), lendo antes os documentos do BSC no repositório `comprove/bsc/` e no projeto COMPROVE. Gravar a entrega no Drive (pasta do Método COMPROVE) ou no projeto.

**Passo 3, registrar:**
- Etapa entregue: `update roadmap_checkpoints set status='completo', comprovado_em=now(), descricao = descricao || ' · Entregue em dd/mm: <link>' where id = <id>;`
- Etapa que precisa de decisão do Paulo: não marcar completa; registrar a proposta e marcar `precisa_do_paulo = true` em `central_diario`.
- Etapa que precisa do navegador (LinkedIn, Instagram, Sales Navigator): não executar; registrar como pendente para a rotina no computador.

**Passo 4, avisar:** uma linha no WhatsApp do Paulo (template `notificacao_comprove_rito_v2`), só se entregou algo ou se precisa dele.

**Regras:**
- Nada inventado; número só com fonte.
- Não alterar objetivos, metas nem prazos do BSC (isso é do Paulo).
- Não enviar nada a terceiros (clientes, leads, instituições).
- Textos sem travessão e sem emoji.

# Supabase: proposta para fechar as tabelas sem RLS (02/11/2026)

Projeto `dutantiolnlidwxdgdyy`. Levantamento só de leitura: **nada foi alterado.** Para aplicar, é preciso o aceite do Paulo.

## Como foi medido

- O código de todos os sites publicados pela tabela `site_deploy_files` foi varrido em busca do nome de cada tabela, como em `sb('tabela?...')`, `from('tabela')` ou `/rest/v1/tabela`.
- Também foram conferidas as funções SQL que usam cada tabela. As três que existem (`rito_gerar_convites_semana`, `rito_disparar_convites` e `fn_cassys_espelho_csv`) são `SECURITY DEFINER`. Isso quer dizer que ligar o RLS não afeta essas funções.
- As rotinas agendadas acessam o banco pelo conector MCP, que tem acesso total. O RLS também não afeta as rotinas.
- **Limite:** sites que não passam pela `site_deploy_files` não foram vistos. Exemplos: a página do REC (`rec.metodocomprove.com.br`) e a busca de leads da Laiane.

## Resultado

| Tabela | Quem lê pela chave pública | Proposta |
|---|---|---|
| `leads` | **Todos os 15 sites do Rito** (`assets/app.js`) | Não dá para só ligar o RLS: os sites param de funcionar. É preciso criar regras de acesso por cliente. Fica para uma fase própria. |
| `configuracoes` | Site `bflow-gestao` (lê e altera o valor do check-in TotalPass) | Mesmo caso: ligar o RLS com regras de acesso, ou mudar o site para usar uma função. |
| `leads_exclusao` | Nenhum site | **Ligar o RLS sem regras** (só o conector acessa) |
| `rec_ig_leads`, `rec_li_leads` | Nenhum site | **Ligar o RLS sem regras.** Antes, conferir a página do REC. |
| `rito_convites_agenda`, `rito_triagem` | Nenhum site; as funções são `SECURITY DEFINER` | **Ligar o RLS sem regras** |
| `rotina_docs`, `rotina_diag` | Nenhum site | **Ligar o RLS sem regras** |
| `_v9_fetch`, `_selos` e as tabelas `_bkp_*` | Nenhum site | Exportar para o Drive e remover (frente "Tabelas de backup") |

## Fase 1 (baixo risco, aguarda aceite)

```sql
alter table public.leads_exclusao       enable row level security;
alter table public.rec_ig_leads         enable row level security;
alter table public.rec_li_leads         enable row level security;
alter table public.rito_convites_agenda enable row level security;
alter table public.rito_triagem         enable row level security;
alter table public.rotina_docs          enable row level security;
alter table public.rotina_diag          enable row level security;
```

**Para desfazer:** `alter table ... disable row level security;` (é instantâneo).

## Fase 2 (precisa desenho)

`leads` e `configuracoes` dependem de regras de acesso que façam cada site do Rito enxergar só o próprio `cliente_id`. Hoje a chave pública é uma só para todos os sites, e quem tem essa chave lê os leads de todos os clientes.

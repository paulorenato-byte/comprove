# Supabase: tabelas de backup e temporárias (levantamento 01/11/2026)

Projeto `dutantiolnlidwxdgdyy`. Levantamento só de leitura: **nada foi apagado.**

## Resumo

- **55 tabelas** são backup, comparação ou staging de alguma operação pontual (sem contar `rotina_diag`, que fica). Somadas dão cerca de **8 MB**.
- O problema não é o espaço, é **bagunça e exposição**. 41 delas estão **sem RLS**, então a chave pública dos sites lê e altera essas linhas. Várias são cópias de dados de pessoas: leads do REC (`rec_*_bkp_20261101*`), funil da Boechat e funil do COMPROVE.
- Não existe padrão de nome: há prefixo `_bkp_`, sufixo `_bkp_`, `_cmp_`, `_sync_` e `migracao_`.

## Grupos

| Grupo | Tabelas | Observação |
|---|---|---|
| B Flow (site e funil) | 10 `_bkp_bflow_*` (02/10 a 21/10) | Versões antigas do site, substituídas por deploys posteriores |
| Boechat | 4 `_bkp_boechat_negocios_20261030[a-d]` + `_bkp_boechat_tarefas_20261030d` | Quatro cópias iguais (161 linhas) do mesmo dia |
| Cassys | 6 `_bkp_cassys_*` (03/10 e 05/10) | Inclui 1.498 tarefas de 05/10 |
| Henrique Gaspar | 8 `_bkp_henrique_gaspar_*` / `_bkp_hg_*` (06 e 07/10) | |
| Funil COMPROVE | `_bkp_funil_20261027[b,c]`, `_bkp_funil_comprove_20261028` (2,1 MB) | |
| REC leads (01/11) | `rec_ig_leads_bkp_20261101`, `..._20261101b`, `rec_li_leads_bkp_20261101`, `migracao_leads_20261101`, `tarefas_bkp_migracao_20261101` | De **hoje**: manter até a migração ser confirmada |
| Deploy/sites | `_bkp_site_deploy_files_20261006` (800 kB), `site_deploy_files_bkp_20261029`, `_bkp_cassys_site_files_20261003` | |
| Comparações e sync de 06/10 | `_cmp_hg_cassys_a`, `_cmp_todos_20261006`, `_novo_funil_20261006`, `_sync_dry/_deploy/_verif_20261006` | Resíduo de uma sincronização já concluída |
| Diversos | `_v9_fetch`, `_selos`, `_rec_build`, `_rec_frag`, `_rito_rollout_tarefas_20261003`, `_bkp_fin_funcoes`, `_bkp_rec_diagnostico_20261022`, `_bkp_whatsapp_webhook`, `rotina_docs` (vazia), `rotina_diag` | `rotina_diag` guarda as medições de ferramentas das rotinas: **manter** |

## Proposta de limpeza (aguarda aceite do Paulo)

1. **Fase 1, sem risco:** exportar cada tabela para CSV na pasta de backups do Drive e conferir as linhas exportadas. Só então remover as tabelas de 02/10 a 28/10 dos grupos B Flow, Boechat, Cassys, Henrique Gaspar, Funil, Deploy e Comparações.
2. **Fase 2, depois de 15/11:** fazer o mesmo com os backups do REC de 01/11, desde que a migração de leads esteja confirmada.
3. **Daqui em diante:** todo backup novo vai para um schema separado (`bkp`), fora do alcance da chave pública, com data no nome. Apagar depois de 30 dias, sempre com export para o Drive antes.

# Rotinas agendadas ativas por máquina (17/11/2026)

Levantamento somente de leitura (list_triggers, enabled=true, 8 páginas até has_more=false). Nenhuma tarefa foi alterada, desligada, apagada ou disparada. Contexto: troca das rotinas de navegador do MacBook (Chrome deviceId 3daafe99-453e-4995-83e6-b3cedca08d94) para o iMac (deviceId antigo 279d2be2-84b1-45bf-8b06-551c89152e2c, pode ter mudado), com perfis do Chrome por cliente no iMac.

**Total de tarefas ativas: 20.** Nenhuma tem `bound_device` preenchido (o campo não veio em nenhuma); a dependência de máquina está só no texto do prompt. Uma tem pasta do computador anexada (Pacote de conteúdo v2: `/Users/paulorenatocesar/Claude`, que é do iMac).

Critérios: "MacBook no texto" = o prompt cita a palavra MacBook ou o deviceId 3daafe99; "iMac no texto" = cita iMac ou 279d2be2 (inclusive em frases como "nunca o iMac"); "usa Chrome" = ferramentas do Claude in Chrome (select_browser, list_connected_browsers, javascript_tool, tabs_*) ou a palavra Chrome como ferramenta de trabalho, ou operação de LinkedIn/Instagram no navegador descrita só nos docs; "controle do computador" = remote-devices / computer_* / device_*. Horários em São Paulo salvo indicação.

## Tabela

| id | nome | horário (cron) | última execução (UTC) e status | computador vinculado | MacBook no texto | iMac no texto | cita 3daafe99 | cita 279d2be2 | usa Chrome | controle do computador | grupo |
|---|---|---|---|---|---|---|---|---|---|---|---|
| `trig_01XkDRZnm8Kfjq1Vp1vJ3L2d` | Programar próximos 7 dias da pauta de vídeo (seg 10h07) · Mac | `CRON_TZ=America/Sao_Paulo 7 10 * * 1` | 2026-11-16T13:08Z SUCCEEDED | null | sim | sim | não | não | não (Chrome do MacBook) | não | B |
| `trig_01MzBBKZCbJtVCSAgC2t5CJR` | Revisão diária do Paulo (7h27 seg-sex) · nuvem | `CRON_TZ=America/Sao_Paulo 27 7 * * 1-5` | 2026-11-17T10:27Z SUCCEEDED | null | não | não | não | não | não | não | A |
| `trig_01FRJmv5fiumVjySySr8x8kL` | Status do WhatsApp (07:05) · MacBook | `CRON_TZ=America/Sao_Paulo 5 7,9,12 * * *` | 2026-11-17T12:06Z SUCCEEDED | null | sim | não | não | não | não | sim | B |
| `trig_01VV3ZAFUS47LVQSPH56EBP5` | [Desova] REC LinkedIn 2G 01 · 50 convites/dia (12h13 seg-sex) · MacBook | `CRON_TZ=America/Sao_Paulo 13 12 * * 1-5` | 2026-11-16T18:43Z SUCCEEDED | null | só no nome | não | não | não | sim (implícito: LinkedIn no navegador pela regra M2 do doc de desova, que diz MacBook 3daafe99) | não | B |
| `trig_01KtxKRZesPzgYCnz4K9mwiA` | [Desova] Elo LinkedIn 1G 01 · 25 mensagens/dia (17h53 seg-sex) · MacBook | `CRON_TZ=America/Sao_Paulo 53 17 * * 1-5` | 2026-11-16T20:53Z SUCCEEDED | null | só no nome | não | não | não | sim (palavra Chrome) | não | B |
| `trig_01KLF28fE6K5S3HnbqhKx7xN` | [Desova] Elo LinkedIn 2G 01 · 50 convites/dia (7h57 seg-sex) · MacBook | `CRON_TZ=America/Sao_Paulo 57 7 * * 1-5` | 2026-11-17T10:57Z SUCCEEDED | null | só no nome | não | não | não | sim (palavra Chrome) | não | B |
| `trig_01M3VT3hcaMS6bY6Ppdd5DTC` | [Desova] LinkedIn · sequência dos lotes 31/10 (6h47 e 14h47 seg-sex) · MacBook | `CRON_TZ=America/Sao_Paulo 47 6,14 * * 1-5` | 2026-11-17T09:47Z SUCCEEDED | null | sim | sim | sim | não | sim (palavra Chrome) | não | B |
| `trig_01UfjpuNFXMQvBtkv8v279Y5` | Guardião da pauta (nenhum dia sem post) 18h07 | `CRON_TZ=America/Sao_Paulo 7 18 * * *` | 2026-11-16T21:07Z SUCCEEDED | null | sim | sim | sim | sim | sim (select_browser, list_connected_browsers, tabs_close_mcp) | não | C |
| `trig_01CfF9sPUP32UGFPSN6BdzKo` | [Prospecção] Executor de aprovações por WhatsApp (hora em hora 8h-19h seg-sex) · MacBook | `CRON_TZ=America/Sao_Paulo 11 8-19 * * 1-5` | 2026-11-17T13:11Z SUCCEEDED | null | sim | sim | sim | sim | sim (palavra Chrome) | não | B |
| `trig_0136EFkyZwYWxDzjP6tcMTFa` | [Funil] Follow-up de reunião: alerta de tarefas vencidas (8h47 seg-sex) · nuvem | `CRON_TZ=America/Sao_Paulo 47 8 * * 1-5` | 2026-11-17T11:47Z SUCCEEDED | null | não | não | não | não | não | não | A |
| `trig_01G872AB9QXcD6KkQqfMbvqu` | [Relatório] KPIs da semana da prospecção (sex 21h10) · nuvem | `CRON_TZ=America/Sao_Paulo 10 21 * * 5` | 2026-11-14T00:10Z SUCCEEDED | null | não | não | não | não | não | não | A |
| `trig_01Q9BjapfmdB2ExBbxJLsX4D` | [Relatório] Números do dia da prospecção (21h seg-sex) · nuvem | `CRON_TZ=America/Sao_Paulo 0 21 * * 1-5` | 2026-11-17T00:09Z SUCCEEDED | null | não | não | não | não | não | não | A |
| `trig_0121KyFEwUhdKF2dX79urnLg` | [Respostas] E-mail · Elo e REC (Snov) (9h40, 13h, 16h40 seg-sex) · nuvem | `CRON_TZ=America/Sao_Paulo 40 9,13,16 * * 1-5` | 2026-11-17T12:41Z SUCCEEDED | null | não | não | não | não | não | não | A |
| `trig_019uQDeJ8ZRPCMawiTzixu6i` | [Respostas] Instagram · REC (13h33, 17h33, 20h33 seg-sex) · MacBook | `CRON_TZ=America/Sao_Paulo 33 13,17,20 * * 1-5` | 2026-11-16T23:33Z SUCCEEDED | null | sim | sim | sim | sim | sim (Claude in Chrome, javascript_tool) | não | B |
| `trig_01Vn9qZ1zziQvTUafL7fN1Hb` | [Respostas] LinkedIn · Elo e REC (11h50, 15h50, 18h50 seg-sex) · MacBook | `CRON_TZ=America/Sao_Paulo 50 11,15,18 * * 1-5` | 2026-11-16T21:50Z SUCCEEDED | null | sim | sim | sim | sim | sim (Claude in Chrome) | não | B |
| `trig_01JXiivgUAFrnvEn1Qp6vmkh` | [REC] Instagram · disparo do lote REC IG (10h33 e 19h33 seg-sex) · MacBook | `CRON_TZ=America/Sao_Paulo 33 10,19 * * 1-5` | 2026-11-17T13:33Z SUCCEEDED | null | sim | sim | sim | não | sim (javascript_tool, palavra Chrome) | não | B |
| `trig_01PWC7zVAaoxkcMw9PvjqNvg` | [REC] Instagram · qualificar o lote semanal (21h37 dom-qui) · MacBook | `CRON_TZ=America/Sao_Paulo 37 21 * * 0-4` | 2026-11-17T00:37Z SUCCEEDED | null | sim | sim | sim | não | sim (javascript_tool, palavra Chrome) | não | B |
| `trig_01LE3H2kstStXiDfbE6Nh3HS` | [COMPROVE] Acompanhamento monetização Facebook (8h43 diário) · MacBook | `CRON_TZ=America/Sao_Paulo 43 8 * * *` | 2026-11-17T11:43Z SUCCEEDED | null | sim | sim | sim | não | sim (list_connected_browsers, select_browser) | não | B |
| `trig_01EtbdbAPFSdjpbWQyfz7vHP` | Rito: executar pedidos do Paulo pelo WhatsApp (de hora em hora, :03) | `CRON_TZ=America/Sao_Paulo 3 * * * *` | 2026-11-17T14:03Z SUCCEEDED | null | não | não | não | não | não | não | A |
| `trig_01DNHiKBCoDHm5xbQEzNYh78` | COMPROVE · Pacote de conteúdo (3 dias) v2 | `8 12 2-31/3 * * (UTC = 09:08 BRT)` | 2026-11-17T12:08Z SUCCEEDED (durou 4 s) | null (pasta anexada /Users/paulorenatocesar/Claude) | não | sim | não | não | sim (palavra "Chrome do Paulo", sem deviceId) | sim (get_device_info, device_list_dir, device_request_folder_access) | C |

## (A) Só nuvem, não muda nada (6)

- `trig_01MzBBKZCbJtVCSAgC2t5CJR` Revisão diária do Paulo (7h27 seg-sex) · nuvem: diz "sem Chrome".
- `trig_0136EFkyZwYWxDzjP6tcMTFa` [Funil] Follow-up de reunião: alerta de tarefas vencidas (8h47 seg-sex) · nuvem: só banco, WhatsApp API e Calendly.
- `trig_01G872AB9QXcD6KkQqfMbvqu` [Relatório] KPIs da semana da prospecção (sex 21h10) · nuvem: banco, Artifact, WhatsApp API.
- `trig_01Q9BjapfmdB2ExBbxJLsX4D` [Relatório] Números do dia da prospecção (21h seg-sex) · nuvem: banco, Artifact, WhatsApp API.
- `trig_0121KyFEwUhdKF2dX79urnLg` [Respostas] E-mail · Elo e REC (Snov) (9h40, 13h, 16h40 seg-sex) · nuvem: diz "sem Chrome"; Gmail, Supabase, WhatsApp API.
- `trig_01EtbdbAPFSdjpbWQyfz7vHP` Rito: executar pedidos do Paulo pelo WhatsApp (de hora em hora, :03): Supabase, Drive, Calendar.

## (B) Usam Chrome ou o computador e estão presas ou apontam para o MacBook (12)

- `trig_01XkDRZnm8Kfjq1Vp1vJ3L2d` Programar próximos 7 dias da pauta de vídeo (seg 10h07) · Mac: LinkedIn pelo "Chrome do MacBook"; cita iMac para mount do Drive e pasta de status.
- `trig_01FRJmv5fiumVjySySr8x8kL` Status do WhatsApp (07:05) · MacBook: app WhatsApp do MacBook via remote-devices; pasta /Users/paulorenatocesar/Documents/COMPROVE Status.
- `trig_01VV3ZAFUS47LVQSPH56EBP5` [Desova] REC LinkedIn 2G 01 · 50 convites/dia (12h13 seg-sex) · MacBook: MacBook só no nome; prompt não cita ferramenta nem máquina.
- `trig_01KtxKRZesPzgYCnz4K9mwiA` [Desova] Elo LinkedIn 1G 01 · 25 mensagens/dia (17h53 seg-sex) · MacBook: MacBook só no nome; cita "o Instagram volta a usar o Chrome".
- `trig_01KLF28fE6K5S3HnbqhKx7xN` [Desova] Elo LinkedIn 2G 01 · 50 convites/dia (7h57 seg-sex) · MacBook: MacBook só no nome; cita "o Elo 1G usa o Chrome".
- `trig_01M3VT3hcaMS6bY6Ppdd5DTC` [Desova] LinkedIn · sequência dos lotes 31/10 (6h47 e 14h47 seg-sex) · MacBook: "CHROME: M2 (MacBook 3daafe99, nunca o iMac)".
- `trig_01CfF9sPUP32UGFPSN6BdzKo` [Prospecção] Executor de aprovações por WhatsApp (hora em hora 8h-19h seg-sex) · MacBook: "Chrome do MacBook, deviceId 3daafe99-..., nunca o iMac 279d2be2-...".
- `trig_019uQDeJ8ZRPCMawiTzixu6i` [Respostas] Instagram · REC (13h33, 17h33, 20h33 seg-sex) · MacBook: "Chrome do MacBook (deviceId 3daafe99-...; nunca o iMac 279d2be2)".
- `trig_01Vn9qZ1zziQvTUafL7fN1Hb` [Respostas] LinkedIn · Elo e REC (11h50, 15h50, 18h50 seg-sex) · MacBook: "Chrome do MacBook (deviceId 3daafe99-...; nunca o iMac 279d2be2)".
- `trig_01JXiivgUAFrnvEn1Qp6vmkh` [REC] Instagram · disparo do lote REC IG (10h33 e 19h33 seg-sex) · MacBook: "CHROME: M2 (MacBook 3daafe99, nunca o iMac)".
- `trig_01PWC7zVAaoxkcMw9PvjqNvg` [REC] Instagram · qualificar o lote semanal (21h37 dom-qui) · MacBook: "Chrome conforme M2 (MacBook 3daafe99, nunca o iMac)".
- `trig_01LE3H2kstStXiDfbE6Nh3HS` [COMPROVE] Acompanhamento monetização Facebook (8h43 diário) · MacBook: select_browser deviceId 3daafe99-... (Chrome do MacBook Air, login do Facebook).

## (C) Usam Chrome ou o computador e já apontam para o iMac (2)

- `trig_01UfjpuNFXMQvBtkv8v279Y5` Guardião da pauta (nenhum dia sem post) 18h07: Chrome do iMac 279d2be2 para Meta/TikTok; MacBook 3daafe99 só para LinkedIn se o iMac estiver logado como outra pessoa; pasta COMPROVE-Redes no iMac.
- `trig_01DNHiKBCoDHm5xbQEzNYh78` COMPROVE · Pacote de conteúdo (3 dias) v2: pipeline restaurado do backup no iMac; pasta COMPROVE Status do iMac; adendo vencido em 03/11.

## (D) Outros casos (0)

Nenhuma.

## Observações para a troca

- Várias rotinas do grupo B dizem expressamente "nunca o iMac 279d2be2". Ao migrar, essa proibição precisa ser invertida no prompt, e também no doc `claude/rotinas-desova-lotes-e-instagram-2026-10-31.md` (regra M2 "MacBook 3daafe99, nunca o iMac"), que vale como parte do prompt das rotinas [Desova], [REC] Instagram disparo e qualificar e da sequência do LinkedIn.
- As três [Desova] de convites/mensagens (REC 2G, Elo 1G, Elo 2G) só citam o MacBook no nome; a máquina vem da regra M2 do doc acima.
- Status do WhatsApp usa controle do computador (app WhatsApp e pasta `/Users/paulorenatocesar/Documents/COMPROVE Status` do MacBook), não o Chrome. No iMac a pasta usada até agora é `~/Claude/COMPROVE Status` (segundo a rotina de pauta de vídeo e o Pacote v2).
- Programar pauta de vídeo (Mac) é misto: LinkedIn pelo "Chrome do MacBook", mas o mount do Drive e a pasta de status citados são do iMac.
- Guardião da pauta já usa o Chrome do iMac (279d2be2) para Meta e TikTok, mas ainda cai no MacBook 3daafe99 para o LinkedIn quando o iMac estiver logado como outra pessoa. Se o deviceId do iMac mudou, este prompt precisa do novo id.
- Pacote de conteúdo v2 depende do iMac pela pasta anexada; o adendo do topo venceu em 03/11 e a última execução durou 4 segundos (vale conferir se está rodando de fato).
- Monetização Facebook diz que o iMac "está em uso com cliente"; com os perfis por cliente no iMac, escolher o perfil do Chrome do Paulo será necessário.

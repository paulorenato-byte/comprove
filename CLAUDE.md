# Repositório comprove (3Motion / Método COMPROVE)

## Comando "VAI <OBJETIVO> <n>" (etapas do BSC da 3Motion)

Toda noite, de domingo a quinta, às 18h37, o Paulo recebe no WhatsApp as etapas do BSC que vencem no próximo dia útil. Cada mensagem termina com um comando, por exemplo `VAI INSTITUICOES 3`. Quando o Paulo disser esse comando numa conversa, execute aquela etapa com ele.

1. Ler a etapa no Rito (Supabase `dutantiolnlidwxdgdyy`), trocando `<APELIDO>` e `<n>`:

```sql
select b.objetivo, o.resumo, c.id, c.ordem_manual, c.descricao, c.prazo, c.responsavel, c.status, s.tarefa, s.sugestao
from bsc_objetivo_resumo o
join bsc_objetivos b on b.id = o.objetivo_id
join roadmap_items r on r.bsc_objetivo_id = b.id
join roadmap_checkpoints c on c.roadmap_item_id = r.id
left join bsc_etapa_sugestoes s on s.checkpoint_id = c.id
where o.apelido = '<APELIDO>' and c.ordem_manual = <n>;
```

2. Executar seguindo a sugestão: fazer o que é do Claude e preparar o que é do Paulo para ele só decidir ou enviar.
3. Ao terminar, marcar a etapa no Rito: `update roadmap_checkpoints set status='completo', comprovado_em=now(), descricao = descricao || ' · Entregue em dd/mm: <onde está>' where id = '<id>';`
4. Registrar em `central_diario` (agente 'code') o que foi feito.

**Comandos que chegaram pelo WhatsApp:** o Paulo também pode mandar `VAI <OBJETIVO> <n>` por texto ou áudio. A função `whatsapp-webhook` não interpreta esses comandos; o banco marca a mensagem com `projeto='bsc'`, responde ao Paulo que recebeu e deixa na fila. No começo de cada conversa com o Paulo, ler `select * from bsc_fila_comandos order by criado_em;` e executar o que estiver lá. Depois de executar: `update whatsapp_inbound set processada=true, processada_em=now(), resposta='[executado] <resumo>' where id='<inbound_id>';` e avisar o Paulo com `select li_enviar_whatsapp('bsc_comando_feito', '<mensagem de uma linha, até 790 caracteres, sem emoji, sem travessão e sem ponto e vírgula>', 1);`.

Apelidos: RITO, REC, INSTITUICOES, PAUTA, PACOTE, METAS, GOOGLE, WEBINAR, DEPARTAMENTOS, CLIENTE, MKT, BENCHMARKING, ESTEIRA, EVENTOS, IMPRENSA, SITE, YOUTUBE, MARCAS, APRESENTACAO, AFILIADOS.

## Onde está o BSC

- Rito: cliente Método COMPROVE, `cliente_id = '0f76c2e9-b273-46c0-9adf-666d3afdd50b'`.
- Revisão e decisões: `bsc/bsc-3motion-revisao.md`. Entregas das etapas: pasta `bsc/`.
- Rotinas no banco (pg_cron): `rito-leitura-3motion-seg` (segunda 17h47) e `bsc-etapas-amanha-3motion` (domingo a quinta 18h37).

## Regras de trabalho com o Paulo

- Abrir cada resposta com as linhas "▸ Modelo" e "▸ Nuvem".
- Responder em português. Medir antes de afirmar. Nada inventado.
- Pedir OK antes de ações irreversíveis. Objetivos e metas do BSC são decisões do Paulo.

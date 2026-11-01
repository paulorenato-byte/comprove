# Central de Frentes

O ponto de encontro entre **Paulo**, **Claude Code**, **Cowork** e as **rotinas agendadas**. Criada em 01/11/2026.

## Divisão de papéis

| Quem | Papel |
|---|---|
| Claude Code | Estratégia, análise e ordens de serviço. Mexe em banco, sites e rotinas na nuvem. |
| Cowork | Executa no computador do Paulo: pastas, abas do Chrome, apps. |
| Rotinas | Trabalho recorrente. A revisão diária lê a central e manda o resumo ao Paulo. |
| Paulo | Decide. A central existe para ele saber exatamente o que depende dele. |

Nenhum agente lembra da conversa anterior. **A memória é o banco.**

## Onde mora (Supabase `dutantiolnlidwxdgdyy`)

- **`central_frentes`**: o mapa. Uma linha por projeto ou subprojeto (`area`: cliente, comprove, pessoal ou infra). Os campos mais importantes são **`bola_com`** (quem precisa agir agora) e **`proximo_passo`**. São dezenas de linhas, não milhares: a frente aponta para as tarefas do Rito, não as copia.
- **`central_diario`**: a memória. Toda sessão grava uma linha ao terminar. `precisa_do_paulo` + `pedido_ao_paulo` indicam o que espera por ele, e `resolvido_em` fecha o pedido.
- **`central_hoje`** (visão): o que o Paulo precisa ver hoje. Junta os pedidos dos agentes, as frentes com a bola com ele, os prazos, as frentes paradas há 5 dias ou mais, as tarefas do Rito fora do funil (janela de 7 dias), as fichas de reunião aguardando aceite e as conversas abertas no WhatsApp.

RLS ligada e sem policies: só os conectores (service role) leem. A chave pública dos sites não enxerga essas tabelas.
Migrações: `central_frentes_diario_v1`, `central_hoje_filtra_clientes_inativos`.

## Arquivos

- [`COLAR-NO-COWORK.md`](COLAR-NO-COWORK.md): **texto único** para colar no Cowork (revisão diária + regra permanente + inventário). Os três arquivos abaixo são as partes separadas.
- [`PROTOCOLO-COWORK.md`](PROTOCOLO-COWORK.md): regra permanente para colar nas instruções do Cowork.
- [`COMANDO-INVENTARIO-COWORK.md`](COMANDO-INVENTARIO-COWORK.md): comando único para o Cowork cadastrar as frentes dele.
- [`REVISAO-DIARIA-PROMPT.md`](REVISAO-DIARIA-PROMPT.md): texto da rotina de revisão diária (dias úteis, 7h27).
- [`COMANDO-ROTINA-REVISAO-COWORK.md`](COMANDO-ROTINA-REVISAO-COWORK.md): comando para o Cowork recriar a revisão diária com conectores.
- [`inventario/`](inventario/): levantamentos para a limpeza geral.

## Consultas úteis

```sql
-- o que espera o Paulo
select ordem, tipo, cliente, frente, detalhe from central_hoje order by ordem, desde;
-- mapa das frentes abertas
select area, titulo, estado, bola_com, proximo_passo from central_frentes
 where estado not in ('concluida','abandonada') order by prioridade, area, titulo;
-- o que aconteceu nas últimas 48 h
select d.quando, d.agente, f.titulo, d.fez from central_diario d
 left join central_frentes f on f.id = d.frente_id
 where d.quando > now() - interval '48 hours' order by d.quando desc;
```

# Comando único: recriar a revisão diária com conectores (Cowork)

> **Para o Paulo:** cole o bloco abaixo numa conversa do Cowork. A sessão do Claude Code criou a rotina, mas não conseguiu gravar os conectores. O Cowork recria a rotina com Supabase, Gmail e Google Agenda e desliga a versão sem conectores.

---

```text
Tarefa única: recriar a tarefa agendada da Revisão Diária com conectores. Não precisa do computador nem do Chrome.

1. Leia a tarefa agendada criada pelo Claude Code: get_trigger com trigger_id "trig_01AEQDXysNABHzfxvejj1gBD". Guarde o prompt EXATO (derived_state.prompt) e o cron ("CRON_TZ=America/Sao_Paulo 27 7 * * 1-5").

2. Crie uma tarefa agendada NOVA (create_trigger) com:
   - name: "COMPROVE · Revisão diária do Paulo (7h27, seg a sex) · nuvem"
   - cron_expression: o mesmo do passo 1
   - create_new_session_on_fire: true
   - prompt: o mesmo do passo 1, sem mudar uma vírgula
   - connectors: ["Supabase", "Gmail", "Google_Calendar"]. Se o parâmetro connectors for recusado, crie sem ele.
   - initiation: human_request
   NÃO use requires_local_device: esta rotina é de nuvem.

3. CONFIRA o resultado: o campo mcp_connections da nova tarefa precisa conter Supabase, Gmail e Google_Calendar, e a resposta não pode trazer o aviso "stores no MCP connectors". Se faltar algum, não siga adiante: me diga exatamente o que voltou.

4. Só depois de confirmar o passo 3, desligue a antiga: update_trigger com trigger_id "trig_01AEQDXysNABHzfxvejj1gBD" e enabled=false. Não apague.

5. Teste agora: fire_trigger na NOVA tarefa. Espere uns 5 minutos e confira no Supabase (project_id dutantiolnlidwxdgdyy):
   select id, quando, left(fez, 300) fez, falta from central_diario where agente='rotina' order by quando desc limit 1;
   Tem de existir uma linha "Revisão diária" de agora, e o Paulo tem de ter recebido o WhatsApp.

6. Registre no diário:
   insert into central_diario (agente, sessao, frente_id, fez, falta, precisa_do_paulo)
   select 'cowork', 'Recriar revisão diária', id, 'Revisão diária recriada com conectores: <id novo>. Antiga trig_01AEQDXysNABHzfxvejj1gBD desligada. Teste: <resultado>', '<se algo falhou>', false
   from central_frentes where titulo like 'Central de frentes%';

7. Me responda com: id da nova tarefa, conectores gravados, resultado do teste.
```

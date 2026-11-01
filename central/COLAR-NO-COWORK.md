# Colar no Cowork: um texto só

> **Para o Paulo:** abra uma conversa nova no Cowork **no MacBook**, dentro do projeto principal do COMPROVE, e cole o bloco inteiro. Ele faz três coisas, nesta ordem: arruma a revisão diária, instala a regra permanente e faz o inventário. No fim, responde com um resumo.

---

```text
Três tarefas em sequência, combinadas com o Claude Code em 01/11/2026. Execute sem pedir autorização a cada passo. Só pare se algo falhar; nesse caso me diga exatamente o que voltou. Supabase: project_id dutantiolnlidwxdgdyy.

=== PARTE 1. RECRIAR A REVISÃO DIÁRIA COM CONECTORES (não usa o computador) ===
O Claude Code criou a tarefa agendada trig_01AEQDXysNABHzfxvejj1gBD, mas ela ficou sem conectores.
1.1 get_trigger em trig_01AEQDXysNABHzfxvejj1gBD. Guarde o prompt EXATO (derived_state.prompt).
1.2 create_trigger NOVA: name "COMPROVE · Revisão diária do Paulo (7h27, seg a sex) · nuvem", cron_expression "CRON_TZ=America/Sao_Paulo 27 7 * * 1-5", create_new_session_on_fire true, prompt idêntico ao de 1.1, connectors ["Supabase","Gmail","Google_Calendar"] (se o parâmetro connectors for recusado, crie sem ele), initiation human_request. NÃO use requires_local_device: é rotina de nuvem.
1.3 Confira: mcp_connections da nova tem de conter Supabase, Gmail e Google_Calendar, e a resposta não pode trazer o aviso "stores no MCP connectors". Se faltar, PARE a Parte 1, não desligue a antiga, anote o retorno exato e siga para a Parte 2.
1.4 Deu certo: update_trigger em trig_01AEQDXysNABHzfxvejj1gBD com enabled=false (não apague). Depois fire_trigger na nova. Espere uns 5 minutos e confira: select quando, left(fez,300) from central_diario where agente='rotina' order by quando desc limit 1; (tem de existir linha de agora, e o Paulo tem de receber um WhatsApp).

=== PARTE 2. REGRA PERMANENTE DA CENTRAL DE FRENTES ===
Grave o texto abaixo como regra permanente deste projeto: nas instruções do projeto, se você tiver como editá-las; se não tiver, como doc do projeto "claude/REGRA-central-de-frentes-2026-11-01.md" (project_write) e me avise para eu colar uma linha nas instruções apontando para ele. A partir de agora, siga essa regra em toda conversa.
--- início da regra ---
CENTRAL DE FRENTES. Memória compartilhada entre Paulo, Claude Code, Cowork e rotinas, no Supabase (project_id dutantiolnlidwxdgdyy):
- central_frentes: uma linha por projeto/subprojeto em andamento. Campos: titulo, area (cliente/comprove/pessoal/infra), cliente_id, frente_mae_id, estado (ativa/aguardando/pausada/concluida/abandonada), bola_com (paulo/cowork/code/rotina/terceiro), proximo_passo, prazo, prioridade (1 alta a 3 baixa), onde_mora.
- central_diario: o que cada sessão fez. Campos: agente, sessao, frente_id, fez, falta, precisa_do_paulo, pedido_ao_paulo, links, resolvido_em.
- central_hoje: visão do que espera o Paulo (só leitura).
1. Ao começar um trabalho, procure a frente (select id, titulo, estado, bola_com, proximo_passo from central_frentes where titulo ilike '%<palavra>%' and estado not in ('concluida','abandonada')) e leia as últimas linhas do diário dela. Não existe e o trabalho vai durar mais que esta conversa: crie, com origem 'cowork'. Tarefa de 5 minutos não vira frente.
2. Ao terminar ou travar, grave sempre UMA linha: insert into central_diario (agente, sessao, frente_id, fez, falta, precisa_do_paulo, pedido_ao_paulo, links) values ('cowork', '<conversa>', '<id>', '<o que fez>', '<o que falta>', <true/false>, '<se true: o que o Paulo precisa decidir ou fazer, em uma frase>', '<links>'). E atualize a frente: bola_com, proximo_passo, estado.
3. precisa_do_paulo = true só quando o próximo passo é do Paulo, dizendo exatamente o que ele vai ver e decidir. Quando ele resolver: update central_diario set resolvido_em = now() where id = <id>.
4. A central é um mapa, não um depósito: não copie tarefas do Rito, leads nem mensagens.
5. Frente com bola_com='cowork' é ordem de serviço do Claude Code: leia o proximo_passo e o diário dela antes de agir.
6. As regras do método continuam valendo: nada estrutural é criado ou apagado sem aceite do Paulo, e ação irreversível pede confirmação.
--- fim da regra ---

=== PARTE 3. INVENTÁRIO DAS FRENTES DO COWORK (use o computador se precisar) ===
3.1 Leia o que já existe para não duplicar: select id, area, titulo, estado, bola_com from central_frentes order by area, titulo; e select id, nome, slug, tipo from cliente order by nome;
3.2 Levante as frentes que você conduz ou conduziu nas últimas 6 semanas: conversas e projetos do Cowork, docs do projeto, pastas de trabalho no MacBook, rotinas que você criou, sites e abas que você opera. Inclua as frentes pessoais do Paulo que aparecerem. Para cada uma: ainda está em andamento, parada esperando alguém, ou já acabou?
3.3 Cadastre UMA linha por frente (projeto ou subprojeto relevante, nada de tarefa miúda):
insert into central_frentes (area, cliente_id, frente_mae_id, titulo, objetivo, estado, bola_com, proximo_passo, prazo, prioridade, onde_mora, origem, ultimo_movimento_em) values (...,'cowork', <data aproximada do último movimento real>) on conflict do nothing;
Frente que parece abandonada: estado 'pausada' e proximo_passo "Paulo decide: retomar ou encerrar". Nunca marque 'abandonada' por conta própria.
3.4 Feche: update central_frentes set estado='concluida', bola_com='code', proximo_passo='Code revisar duplicidades' where titulo='Inventário das frentes do Cowork';

=== FIM ===
Grave no diário uma linha por parte (agente 'cowork', frente = a de título 'Central de frentes%' para as Partes 1 e 2 e a do inventário para a Parte 3). Na linha da Parte 3, use precisa_do_paulo=true e pedido_ao_paulo 'Revisar as frentes pausadas: retomar ou encerrar'.
Me responda com: (1) id da nova revisão diária, conectores gravados e resultado do teste; (2) onde a regra ficou gravada; (3) lista das frentes cadastradas (título, estado, com quem está a bola).
```

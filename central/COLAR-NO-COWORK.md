# Colar no Cowork: um texto só, para todos os projetos

> **Para o Paulo:** abra uma **conversa nova** do Cowork **no MacBook**, dentro do projeto COMPROVE, e cole o bloco inteiro. Ele faz quatro coisas: descobre quais projetos consegue alcançar, arruma a revisão diária, instala a regra permanente em todos os projetos que alcançar e faz o inventário de todos eles. No fim, diz quais projetos ficaram de fora. Só para esses você usa a versão curta (`COLAR-NOS-OUTROS-PROJETOS.md`).

---

```text
Tarefa combinada com o Claude Code em 01/11/2026: ligar TODOS os meus projetos do Cowork à Central de Frentes. Execute sem pedir autorização a cada passo. Só pare se algo falhar; nesse caso me diga exatamente o que voltou. Supabase: project_id dutantiolnlidwxdgdyy. Não invente: o que não conseguir medir, diga que não conseguiu.

=== PARTE 0. QUAIS PROJETOS VOCÊ ALCANÇA ===
0.1 Liste as suas ferramentas de projeto (por exemplo project_list, project_read, project_write, listagem de conversas) e diga quais existem nesta conversa.
0.2 Liste TODOS os meus projetos do Cowork que você consegue ver (nome e id). Para cada um, teste se consegue LER (os docs ou instruções) e se consegue ESCREVER (um doc). Anote o resultado: lê sim/não, escreve sim/não.
0.3 Se você só enxerga este projeto, diga isso claramente e siga com ele. Os demais eu faço à mão.

=== PARTE 1. RECRIAR A REVISÃO DIÁRIA COM CONECTORES (uma vez só, vale para a conta toda) ===
O Claude Code criou a tarefa agendada trig_01AEQDXysNABHzfxvejj1gBD, mas ela ficou sem conectores.
1.1 get_trigger em trig_01AEQDXysNABHzfxvejj1gBD. Guarde o prompt EXATO (derived_state.prompt).
1.2 create_trigger NOVA: name "COMPROVE · Revisão diária do Paulo (7h27, seg a sex) · nuvem", cron_expression "CRON_TZ=America/Sao_Paulo 27 7 * * 1-5", create_new_session_on_fire true, prompt idêntico ao de 1.1, connectors ["Supabase","Gmail","Google_Calendar"] (se o parâmetro connectors for recusado, crie sem ele), initiation human_request. NÃO use requires_local_device: é rotina de nuvem.
1.3 Confira: mcp_connections da nova tem de conter Supabase, Gmail e Google_Calendar, e a resposta não pode trazer o aviso "stores no MCP connectors". Se faltar, PARE a Parte 1, não desligue a antiga, anote o retorno exato e siga para a Parte 2.
1.4 Deu certo: update_trigger em trig_01AEQDXysNABHzfxvejj1gBD com enabled=false (não apague). Depois fire_trigger na nova. Espere uns 5 minutos e confira: select quando, left(fez,300) from central_diario where agente='rotina' order by quando desc limit 1; (tem de existir linha de agora, e o Paulo tem de receber um WhatsApp).

=== PARTE 2. REGRA PERMANENTE EM CADA PROJETO ===
Para CADA projeto em que você consegue escrever (Parte 0), grave o texto abaixo: nas instruções do projeto, se você tiver como editá-las; se não tiver, como doc do projeto "claude/REGRA-central-de-frentes-2026-11-01.md". Anote, projeto a projeto, onde ficou gravada. A partir de agora, siga essa regra em toda conversa.
--- início da regra ---
CENTRAL DE FRENTES. Memória compartilhada entre Paulo, Claude Code, Cowork e rotinas, no Supabase (project_id dutantiolnlidwxdgdyy). Vale para TODOS os projetos do Paulo, não só o COMPROVE.
- central_frentes: uma linha por projeto/subprojeto em andamento. Campos: titulo, area (cliente/comprove/pessoal/infra), cliente_id, frente_mae_id, estado (ativa/aguardando/pausada/concluida/abandonada), bola_com (paulo/cowork/code/rotina/terceiro), proximo_passo, prazo, prioridade (1 alta a 3 baixa), onde_mora.
- central_diario: o que cada sessão fez. Campos: agente, sessao, frente_id, fez, falta, precisa_do_paulo, pedido_ao_paulo, links, resolvido_em.
- central_hoje: visão do que espera o Paulo (só leitura).
1. Ao começar um trabalho, procure a frente (select id, titulo, estado, bola_com, proximo_passo from central_frentes where titulo ilike '%<palavra>%' and estado not in ('concluida','abandonada')) e leia as últimas linhas do diário dela. Não existe e o trabalho vai durar mais que esta conversa: crie, com origem 'cowork'. Tarefa de 5 minutos não vira frente.
2. Ao terminar ou travar, grave sempre UMA linha: insert into central_diario (agente, sessao, frente_id, fez, falta, precisa_do_paulo, pedido_ao_paulo, links) values ('cowork', '<projeto · conversa>', '<id>', '<o que fez>', '<o que falta>', <true/false>, '<se true: o que o Paulo precisa decidir ou fazer, em uma frase>', '<links>'). E atualize a frente: bola_com, proximo_passo, estado.
3. precisa_do_paulo = true só quando o próximo passo é do Paulo, dizendo exatamente o que ele vai ver e decidir. Quando ele resolver: update central_diario set resolvido_em = now() where id = <id>.
4. A central é um mapa, não um depósito: não copie tarefas, leads, lançamentos nem mensagens para lá.
5. Frente com bola_com='cowork' é ordem de serviço do Claude Code: leia o proximo_passo e o diário dela antes de agir.
6. Nada estrutural é criado ou apagado sem aceite do Paulo, e ação irreversível pede confirmação.
--- fim da regra ---

=== PARTE 3. INVENTÁRIO DE TODOS OS PROJETOS QUE VOCÊ LÊ ===
3.1 Para não duplicar, leia o que já existe: select id, area, titulo, estado, bola_com from central_frentes order by area, titulo; e select id, nome, slug, tipo from cliente order by nome;
3.2 Para CADA projeto que você consegue ler (Parte 0), levante as frentes das últimas 6 semanas: docs, instruções, conversas, pastas de trabalho no MacBook ligadas a ele e rotinas que você criou. Para cada frente: ainda está em andamento, parada esperando alguém, ou já acabou?
3.3 Área: 'pessoal' para assuntos pessoais e familiares do Paulo (casa, saúde, finanças pessoais, estudos, viagens etc.), 'cliente' se for de um cliente cadastrado (use o cliente_id), 'comprove' para o negócio COMPROVE/3Motion, 'infra' para ferramentas e sistemas. Na dúvida entre pessoal e outra área, use 'pessoal'.
3.4 Cadastre UMA linha por frente (projeto ou subprojeto relevante, nada de tarefa miúda), com o nome do projeto do Cowork no começo do título quando ajudar a reconhecer (ex.: "Casa · reforma da cozinha"), e o nome do projeto do Cowork em onde_mora:
insert into central_frentes (area, cliente_id, frente_mae_id, titulo, objetivo, estado, bola_com, proximo_passo, prazo, prioridade, onde_mora, origem, ultimo_movimento_em) values (..., 'cowork', <data aproximada do último movimento real>) on conflict do nothing;
Frente que parece abandonada: estado 'pausada' e proximo_passo "Paulo decide: retomar ou encerrar". Nunca marque 'abandonada' por conta própria.
3.5 Feche: update central_frentes set estado='concluida', bola_com='code', proximo_passo='Code revisar duplicidades' where titulo='Inventário das frentes do Cowork';

=== FIM ===
Grave no diário uma linha por parte (agente 'cowork'; frente de título 'Central de frentes%' para as Partes 0, 1 e 2; frente 'Inventário das frentes do Cowork' para a Parte 3). Na linha da Parte 3, use precisa_do_paulo=true e pedido_ao_paulo 'Revisar as frentes pausadas: retomar ou encerrar'. Na linha da Parte 0, liste os projetos que você NÃO alcançou.
Me responda com: (0) projetos alcançados e NÃO alcançados; (1) id da nova revisão diária, conectores gravados e resultado do teste; (2) onde a regra ficou gravada em cada projeto; (3) frentes cadastradas por projeto (título, área, estado, com quem está a bola).
```

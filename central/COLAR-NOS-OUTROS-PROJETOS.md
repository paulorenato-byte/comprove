# Colar nos OUTROS projetos do Cowork (versão curta)

> **Para o Paulo:** o texto completo (`COLAR-NO-COWORK.md`) vai **uma vez só**, no projeto COMPROVE. Ele já arruma a revisão diária, que vale para a conta inteira. Em **cada um dos outros projetos** do Cowork, cole este texto curto numa conversa nova. Ele só instala a regra e faz o inventário daquele projeto.

---

```text
Duas tarefas, combinadas com o Claude Code em 01/11/2026. Execute sem pedir autorização a cada passo. Supabase: project_id dutantiolnlidwxdgdyy. A revisão diária já foi resolvida em outro projeto: não mexa em tarefas agendadas.

=== PARTE A. REGRA PERMANENTE DA CENTRAL DE FRENTES (neste projeto) ===
Grave o texto abaixo como regra permanente DESTE projeto: nas instruções do projeto, se você tiver como editá-las; se não tiver, como doc do projeto "claude/REGRA-central-de-frentes-2026-11-01.md" e me avise para eu colar uma linha nas instruções apontando para ele. A partir de agora, siga essa regra em toda conversa deste projeto.
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

=== PARTE B. INVENTÁRIO DAS FRENTES DESTE PROJETO ===
B.1 Para não duplicar, leia o que já existe: select id, area, titulo, estado, bola_com from central_frentes order by area, titulo; e, se o projeto for de cliente, select id, nome, slug from cliente order by nome;
B.2 Levante as frentes deste projeto nas últimas 6 semanas: conversas, docs do projeto, pastas e rotinas ligadas a ele. Para cada uma: ainda está em andamento, parada esperando alguém, ou já acabou?
B.3 Área: 'pessoal' para assuntos pessoais e familiares do Paulo (casa, saúde, finanças pessoais, estudos, viagens etc.), 'cliente' se for de um cliente cadastrado (use o cliente_id), 'comprove' para o negócio COMPROVE/3Motion, 'infra' para ferramentas e sistemas. Na dúvida entre pessoal e outra área, use 'pessoal'.
B.4 Cadastre UMA linha por frente (projeto ou subprojeto relevante, nada de tarefa miúda), começando o título pelo nome do projeto quando ajudar a reconhecer (ex.: "Casa · reforma da cozinha"):
insert into central_frentes (area, cliente_id, frente_mae_id, titulo, objetivo, estado, bola_com, proximo_passo, prazo, prioridade, onde_mora, origem, ultimo_movimento_em) values (..., 'cowork', <data aproximada do último movimento real>) on conflict do nothing;
Frente que parece abandonada: estado 'pausada' e proximo_passo "Paulo decide: retomar ou encerrar". Nunca marque 'abandonada' por conta própria.
B.5 Grave no diário: insert into central_diario (agente, sessao, fez, precisa_do_paulo, pedido_ao_paulo) values ('cowork', '<nome do projeto> · inventário 01/11', '<n> frentes cadastradas: <lista curta>', true, 'Revisar as frentes pausadas do projeto <nome>: retomar ou encerrar');

Me responda com: onde a regra ficou gravada e a lista das frentes cadastradas (título, área, estado, com quem está a bola).
```

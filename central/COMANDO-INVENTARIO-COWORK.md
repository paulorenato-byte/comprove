# Comando único: inventário das frentes do Cowork

> **Para o Paulo:** cole o bloco abaixo **uma vez** numa conversa nova do Cowork, de preferência no computador onde ficam as pastas de trabalho. Depois que ele terminar, me avise aqui no Code: eu leio o resultado, limpo duplicidades e monto a primeira revisão.

---

```text
Tarefa única: inventário das minhas frentes de trabalho para a Central de Frentes (Supabase, project_id dutantiolnlidwxdgdyy, tabela public.central_frentes). Não execute nenhuma frente agora, só mapeie e cadastre.

1. Leia o que já existe para não duplicar:
   select id, area, titulo, estado, bola_com from central_frentes order by area, titulo;
   e os clientes: select id, nome, slug, tipo from cliente order by nome;

2. Levante as frentes que você (Cowork) conduz ou conduziu nas últimas 6 semanas: conversas e projetos do Cowork, instruções de projeto, pastas de trabalho que você usa, rotinas que você criou, abas e sites que você opera. Para cada uma, pergunte: ainda está em andamento, parada esperando alguém, ou já acabou?

3. Cadastre UMA linha por frente (projeto ou subprojeto relevante; não cadastre tarefas miúdas, leads, mensagens nem itens que já moram no Rito):
   insert into central_frentes (area, cliente_id, titulo, objetivo, estado, bola_com, proximo_passo, prazo, prioridade, onde_mora, origem, ultimo_movimento_em)
   values ('<cliente|comprove|pessoal|infra>', <id do cliente ou null>, '<título curto>', '<o que é "pronto">', '<ativa|aguardando|pausada|concluida|abandonada>', '<paulo|cowork|code|rotina|terceiro>', '<próximo passo concreto>', <data ou null>, <1|2|3>, '<onde mora: pasta, projeto do Cowork, site, aba>', 'cowork', '<data do último movimento real, aproximada>')
   on conflict do nothing;
   Para subprojeto, preencha frente_mae_id com o id da frente-mãe.
   Frente que você acha que foi abandonada: cadastre com estado 'pausada' e no proximo_passo escreva "Paulo decide: retomar ou encerrar". Não marque 'abandonada' por conta própria.

4. Ao final, grave uma linha no diário:
   insert into central_diario (agente, sessao, fez, falta, precisa_do_paulo, pedido_ao_paulo)
   values ('cowork', 'Inventário de frentes 01/11', '<n> frentes cadastradas: <lista curta>', '<o que não consegui mapear>', true, 'Revisar as frentes marcadas como pausadas e decidir retomar ou encerrar');
   e marque a frente do inventário como feita:
   update central_frentes set estado='concluida', bola_com='code', proximo_passo='Code revisar duplicidades e montar a 1ª revisão' where titulo = 'Inventário das frentes do Cowork';

5. Me responda com a lista do que cadastrou (título, estado, com quem está a bola).

Depois disso, adote a regra permanente da Central de Frentes (o Paulo vai colar nas instruções do projeto).
```

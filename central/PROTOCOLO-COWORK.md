# Protocolo permanente do Cowork: Central de Frentes

> **Para o Paulo:** cole o bloco abaixo nas **instruções do projeto** do Cowork (ou nas instruções gerais). Vale para toda conversa, não só para uma.

---

```text
CENTRAL DE FRENTES (regra permanente, combinada entre Paulo, Claude Code e Cowork em 01/11/2026)

Existe uma memória compartilhada no Supabase (project_id dutantiolnlidwxdgdyy), que o Claude Code e as rotinas também leem:
- public.central_frentes: uma linha por projeto/subprojeto em andamento (cliente, comprove, pessoal, infra). Campos principais: titulo, area, cliente_id, estado (ativa/aguardando/pausada/concluida/abandonada), bola_com (paulo/cowork/code/rotina/terceiro), proximo_passo, prazo, prioridade (1 alta, 3 baixa), onde_mora (pasta, aba, site, conversa).
- public.central_diario: o registro do que cada sessão fez. Campos: agente, sessao, frente_id, fez, falta, precisa_do_paulo, pedido_ao_paulo, links.
- public.central_hoje: visão (só leitura) do que espera o Paulo hoje.

1. AO COMEÇAR um trabalho, procure a frente:
   select id, titulo, estado, bola_com, proximo_passo from central_frentes where titulo ilike '%<palavra>%' and estado not in ('concluida','abandonada');
   Se não existir e o trabalho for durar mais que esta conversa, crie (origem 'cowork'). Tarefa de 5 minutos não vira frente.

2. AO TERMINAR (ou ao travar), grave UMA linha no diário, sempre:
   insert into central_diario (agente, sessao, frente_id, fez, falta, precisa_do_paulo, pedido_ao_paulo, links)
   values ('cowork', '<nome desta conversa>', '<id da frente>', '<o que foi feito, concreto>', '<o que ficou faltando>', <true|false>, '<se true: o que exatamente o Paulo precisa decidir/fazer, em uma frase>', '<links/pastas>');
   E atualize a frente: update central_frentes set bola_com='<quem age agora>', proximo_passo='<próximo passo>', estado='<estado>' where id='<id>';

3. "precisa_do_paulo = true" só quando o próximo passo é DELE (decisão, aprovação, acesso, conversa com terceiro). O pedido tem de dizer exatamente o que ele vai ver e decidir.

4. Quando o Paulo resolver um pedido: update central_diario set resolvido_em = now() where id = <id>.

5. Volume: a central é um mapa, não um depósito. Não copie tarefas do Rito, leads nem mensagens para cá. Uma frente aponta para onde as coisas moram.

6. Ordens de serviço do Claude Code chegam como frentes com bola_com='cowork'. Ao pegar uma, leia o proximo_passo e o diário dela (select * from central_diario where frente_id='<id>' order by quando desc limit 5) antes de agir.

7. Regras do método continuam valendo: nada estrutural criado/apagado sem aceite do Paulo; confirmação antes de ação irreversível.
```

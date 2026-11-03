# Prompt único para o Cowork, projeto COMPROVE (03/11/2026)

> **Para o Paulo:** abra uma conversa nova no projeto COMPROVE, no MacBook, e cole o bloco inteiro.

```text
CENTRAL DE FRENTES: contexto completo e execução do que falta. Pedido do Paulo, 03/11/2026. Execute tudo nesta conversa, sem pedir autorização a cada passo.

=== 1. A INTENÇÃO (por que isto existe) ===
O Paulo tem muitos projetos e subprojetos: a COMPROVE/3Motion, cada cliente e os assuntos pessoais. Ele perde o fio entre eles: um projeto avança e pede uma ação dele enquanto ele está em outro. A organização combinada é esta:
- Claude Code = estratégia, análise e direção. Mexe em banco, sites e rotinas na nuvem.
- Cowork (você) = execução. Tem as pastas, o Chrome e o MacBook.
- Uma SECRETÁRIA: a revisão diária que diz ao Paulo o que depende dele hoje, o que andou sem ele e o que está parado.
- Nenhum agente lembra da conversa anterior. A memória comum fica no Supabase (project_id dutantiolnlidwxdgdyy):
  - central_frentes: o mapa, uma linha por projeto ou subprojeto, com bola_com (quem precisa agir) e proximo_passo;
  - central_diario: o registro do que cada sessão fez, com precisa_do_paulo e pedido_ao_paulo;
  - central_hoje: a visão do que espera o Paulo.

=== 2. O QUE JÁ FOI FEITO (não refaça) ===
- As tabelas e a visão acima foram criadas, e a chave pública dos sites não lê nenhuma delas.
- A revisão diária roda de segunda a sexta, às 7h27, como tarefa agendada trig_01MzBBKZCbJtVCSAgC2t5CJR, com os conectores Supabase, Gmail e Google Calendar. O teste de 01/11 chegou no WhatsApp. Em 02/11 ela falhou porque a conta ficou sem crédito, não por defeito.
- Existem 36 frentes: as 17 do COMPROVE (inventário feito por você em 01/11), Cassys, Henrique Gaspar, Mello, B.Flow, Reis, Boechat, Kuraray, Coelho & Morello, Sandra, Financeiro, as da limpeza e os inativos (Ares, Mazzolin, FSRO, Trevisan e Simone & Bassetto, que estão pausados).
- 24 tarefas agendadas antigas foram apagadas pelo Code, com backup do texto no repositório.
- 7 tabelas expostas foram fechadas (RLS): leads_exclusao, rec_ig_leads, rec_li_leads, rito_convites_agenda, rito_triagem, rotina_diag e rotina_docs.
- O doc claude/REGRA-central-de-frentes-2026-11-01.md existe neste projeto.

=== 3. O QUE NÃO FOI FEITO (é a sua tarefa agora) ===
(a) A regra que faz o Cowork registrar o que faz NÃO vale fora deste projeto, e nem aqui está nas instruções. Por isso o trabalho feito nos outros projetos não chega à central. Este é o buraco principal.
(b) Os projetos ativos fora do COMPROVE não foram inventariados por dentro. As frentes de cliente mostram só o que o Rito registra. Pessoal, Dia a dia e casa, Karina Ribeiro e COMPROVE SCHOOL não têm nada.
(c) Duas tarefas agendadas não foram apagadas, porque o sistema bloqueou o Code.
(d) Os projetos duplicados não foram examinados.
Ficam com o Code, e NÃO são para você fazer: a tabela leads (RLS por cliente), as 55 tabelas de backup, os sites do Netlify, os 27 aceites de reunião pendentes e a triagem das tarefas atrasadas.

=== 4. REGRA DE HONESTIDADE (vale acima de tudo) ===
Só marque FEITO depois de conferir o resultado e com prova: o que leu de volta, a resposta da ferramenta ou o screenshot descrito. Se não conseguiu, se não tem certeza ou se o sistema negou, marque NÃO FEITO com o motivo exato. Nunca escreva "deve ter funcionado". Antes deste prompt, o Paulo recebeu "está tudo certo" quando não estava, e isso não pode se repetir.

=== 5. EXECUÇÃO ===
TEXTO DA REGRA (é este texto que você vai instalar):
--- início ---
CENTRAL DE FRENTES (regra do Paulo, 03/11/2026, vale para todos os projetos). Memória compartilhada no Supabase (project_id dutantiolnlidwxdgdyy). Ao começar um trabalho que vai durar mais que a conversa, procure a frente: select id, titulo, bola_com, proximo_passo from central_frentes where titulo ilike '%<palavra>%'; se não existir, crie (origem 'cowork'). Ao terminar ou travar, grave UMA linha: insert into central_diario (agente, sessao, frente_id, fez, falta, precisa_do_paulo, pedido_ao_paulo) values ('cowork', '<projeto · conversa>', '<id>', '<o que fez>', '<o que falta>', <true|false>, '<o que o Paulo precisa decidir>'), e atualize bola_com e proximo_passo da frente. Não copie tarefas, leads nem mensagens para lá. Detalhes no doc claude/REGRA-central-de-frentes-2026-11-01.md do projeto COMPROVE.
--- fim ---

As ferramentas de projeto desta conversa só enxergam o COMPROVE (isso já foi medido). Para as configurações e para os outros projetos, use o CONTROLE DO COMPUTADOR no MacBook: o app do Claude, ou claude.ai no Chrome. Carregue antes a habilidade de computer use.

PASSO A, INSTALAR A REGRA
A1. Nas configurações da conta do Claude, no campo de instruções gerais (preferências pessoais), acrescente o TEXTO DA REGRA no fim, sem apagar nada. Salve, reabra e LEIA DE VOLTA o campo.
A2. Nas instruções do projeto COMPROVE, faça o mesmo: acrescente, salve e leia de volta.
A3. TESTE: abra uma conversa nova no projeto Kuraray e pergunte "Qual é a regra da central de frentes?". Anote a resposta literal.
  - Se ele não souber, instale o TEXTO DA REGRA nas instruções de cada projeto ativo do PASSO B, lendo de volta em cada um.
  - Feche a conversa de teste.

PASSO B, INVENTÁRIO DOS PROJETOS ATIVOS (só leitura nos projetos)
Projetos: Comprove REC (MacBook), Kuraray, Boechat, Cassys, Henrique Gaspar, Casa B Flow, Sandra Maria Lopes Linquevis, Pessoal (o de 11/out), Mello Advogados, Karina Ribeiro + COMPROVE, Financeiro, Dia a dia e casa, Coelho & Morello e COMPROVE SCHOOL.
B1. Leia o que já existe: select id, area, cliente_id, titulo, estado, bola_com, proximo_passo from central_frentes order by area, titulo; e select id, nome, slug from cliente;
B2. Em cada projeto, leia as instruções, a lista de documentos e os títulos e datas das últimas 10 conversas. Abra uma conversa só quando o título não bastar.
B3. Para cada assunto em andamento nas últimas 6 semanas:
  - se já existe frente, atualize só o proximo_passo, e só com fato novo;
  - se não existe, crie: insert into central_frentes (area, cliente_id, titulo, objetivo, estado, bola_com, proximo_passo, prioridade, onde_mora, origem, ultimo_movimento_em) values (..., 'cowork', <data real>).
  area: 'pessoal' para casa, família, saúde e finanças pessoais; 'cliente' com o cliente_id; 'comprove' para o negócio. Uma linha por assunto, nunca por tarefa miúda. Assunto parado vira estado 'pausada', com proximo_passo "Paulo decide: retomar ou encerrar".

PASSO C, APAGAR 2 TAREFAS AGENDADAS (o Paulo autorizou; o backup já existe)
C1. Confira com get_trigger que o nome bate e que enabled=false. Depois, delete_trigger em trig_016FyAK7yfr77heNSwEUSKk4 (Dental campo 15/10) e em trig_01Pz5Ga9ju3BiCA1ZpxFTrw3 (COMPROVE Sexta 16/10).
C2. Confira de novo com get_trigger: tem de voltar "não encontrada". Se o sistema negar, marque NÃO FEITO com a mensagem exata.

PASSO D, PROJETOS DUPLICADOS (examinar, NÃO arquivar)
Pessoal (o de 28/set), COMPROVE ERRADO, Branding COMPROVE e Marketing, Kuraray (o de 16/set) e Rito — Modelo Estratégico Tático Operacional. Para cada um, liste os documentos e as últimas conversas e diga se há algo que não existe em outro projeto.

PASSO E, REGISTRO E RELATÓRIO
E1. Grave no central_diario uma linha por passo (agente 'cowork', sessao 'Prompt único 03/11', frente de título 'Central de frentes%'). Na linha do PASSO D, use precisa_do_paulo=true e pedido_ao_paulo 'Decidir quais projetos duplicados arquivar'.
E2. Termine SÓ com esta tabela:
| Item | FEITO ou NÃO FEITO | Prova ou motivo |
uma linha para cada: A1 instruções gerais | A2 projeto COMPROVE | A3 teste no Kuraray (resposta literal) | A3 regra por projeto (quais, se foi preciso) | B inventário (projetos lidos, frentes criadas, frentes atualizadas, projetos que não abriram) | C Dental | C Sexta 16/10 | D duplicados (o que cada um tem) | E1 diário.
Depois da tabela, no máximo 3 linhas com o que ainda depende do Paulo.
```

# Prompt único para o Cowork, projeto COMPROVE (03/11/2026)

> **Para o Paulo:** abra uma **conversa nova no projeto COMPROVE, no MacBook**, e cole o bloco inteiro. Ele faz tudo o que falta na Central de Frentes e termina com uma tabela de FEITO ou NÃO FEITO, com a prova de cada item.

---

```text
Tarefa completa da CENTRAL DE FRENTES. O pedido é do Paulo, em 03/11/2026. Execute tudo nesta conversa, sem me pedir autorização a cada passo.

REGRA DE HONESTIDADE (vale acima de todo o resto): só marque um item como FEITO se você tiver conferido o resultado depois de agir e puder mostrar a prova (o que leu de volta, a resposta da ferramenta, um screenshot descrito). Se não conseguiu, se tentou e não sabe se funcionou, ou se o sistema negou, marque NÃO FEITO e escreva o motivo exato. Nunca escreva "deve ter funcionado". O Paulo prefere um NÃO FEITO honesto a um FEITO duvidoso.

CONTEXTO
- Supabase: project_id dutantiolnlidwxdgdyy. Tabelas: central_frentes (o mapa de projetos), central_diario (a memória do que cada sessão fez) e a visão central_hoje.
- Já existem 36 frentes, entre elas COMPROVE (17), Cassys, Henrique Gaspar, Mello, B.Flow, Reis, Boechat, Kuraray, Coelho & Morello, Sandra e Financeiro. Os inativos (Ares, Mazzolin, FSRO, Trevisan, Simone & Bassetto) já estão marcados como pausados.
- A revisão diária (trig_01MzBBKZCbJtVCSAgC2t5CJR, 7h27, de segunda a sexta) já funciona e lê essas tabelas.
- O que falta: (1) a regra da central valer em TODOS os projetos do Cowork, não só no COMPROVE; (2) o inventário dos outros projetos ativos; (3) apagar 2 tarefas agendadas; (4) examinar os projetos duplicados.
- Esta conversa só enxerga o projeto COMPROVE pelas ferramentas de projeto (isso já foi medido). Para mexer nos outros projetos e nas configurações, use o CONTROLE DO COMPUTADOR no MacBook: o app do Claude no Mac, ou claude.ai no Chrome. Carregue antes a habilidade de computer use, se ela existir.

TEXTO DA REGRA (é este texto que deve ser instalado):
--- início ---
CENTRAL DE FRENTES (regra do Paulo, 03/11/2026, vale para todos os projetos). Memória compartilhada no Supabase (project_id dutantiolnlidwxdgdyy). Ao começar um trabalho que vai durar mais que a conversa, procure a frente: select id, titulo, bola_com, proximo_passo from central_frentes where titulo ilike '%<palavra>%'; se não existir, crie (origem 'cowork'). Ao terminar ou travar, grave UMA linha: insert into central_diario (agente, sessao, frente_id, fez, falta, precisa_do_paulo, pedido_ao_paulo) values ('cowork', '<projeto · conversa>', '<id>', '<o que fez>', '<o que falta>', <true|false>, '<o que o Paulo precisa decidir>'), e atualize bola_com e proximo_passo da frente. Não copie tarefas, leads nem mensagens para lá. Detalhes no doc claude/REGRA-central-de-frentes-2026-11-01.md do projeto COMPROVE.
--- fim ---

PARTE 1. INSTALAR A REGRA EM TODOS OS PROJETOS
1.1 Com o controle do computador, abra as configurações da conta do Claude, no campo de instruções gerais (preferências pessoais, que valem para todas as conversas), e acrescente o TEXTO DA REGRA no fim, sem apagar o que já existe. Salve. Feche, reabra e LEIA DE VOLTA o campo para confirmar que o texto ficou gravado.
1.2 Abra as instruções do projeto COMPROVE e acrescente o TEXTO DA REGRA no fim, sem apagar nada. Salve e leia de volta.
1.3 TESTE: abra uma conversa nova em OUTRO projeto (Kuraray) e pergunte exatamente "Qual é a regra da central de frentes?". Anote a resposta. Se ele responder com o conteúdo da regra, as instruções gerais valem para todos os projetos. Se não souber responder, repita o passo 1.2 nas instruções de cada projeto ativo da PARTE 2, com leitura de volta em cada um. Feche a conversa de teste.

PARTE 2. INVENTÁRIO DOS PROJETOS ATIVOS (só leitura nos projetos)
Projetos ativos: Comprove REC (MacBook), Kuraray, Boechat, Cassys, Henrique Gaspar, Casa B Flow, Sandra Maria Lopes Linquevis, Pessoal (o de 11/out), Mello Advogados, Karina Ribeiro + COMPROVE, Financeiro, Dia a dia e casa, Coelho & Morello e COMPROVE SCHOOL.
2.1 Leia o que já existe para não duplicar: select id, area, cliente_id, titulo, estado, bola_com, proximo_passo from central_frentes order by area, titulo; e select id, nome, slug from cliente;
2.2 Para cada projeto, com o controle do computador, abra o projeto e leia: as instruções (resumo), a lista de documentos e arquivos, e os títulos e datas das últimas 10 conversas. Abra uma conversa só quando o título não bastar para entender o assunto. Não escreva nada nos projetos além da regra da PARTE 1.
2.3 Para cada assunto em andamento nas últimas 6 semanas: se já existir uma frente para ele, atualize só o proximo_passo, e só com fato novo; se não existir, crie a frente (insert into central_frentes (area, cliente_id, titulo, objetivo, estado, bola_com, proximo_passo, prioridade, onde_mora, origem, ultimo_movimento_em) values (..., 'cowork', <data real do último movimento>)). area: 'pessoal' para casa, família, saúde e finanças pessoais; 'cliente' para clientes (use o cliente_id); 'comprove' para o negócio. Uma linha por assunto relevante, nunca por tarefa miúda. Assunto que parece parado: estado 'pausada' e proximo_passo "Paulo decide: retomar ou encerrar". Nunca marque nada como 'abandonada'.

PARTE 3. APAGAR 2 TAREFAS AGENDADAS (o Paulo autorizou em 03/11; o backup do texto delas já está salvo no repositório)
3.1 delete_trigger em trig_016FyAK7yfr77heNSwEUSKk4 (Dental campo, 15/10) e em trig_01Pz5Ga9ju3BiCA1ZpxFTrw3 (COMPROVE Sexta 16/10). Antes, confira com get_trigger que o nome bate e que enabled=false.
3.2 Confira depois com get_trigger: tem de voltar "não encontrada". Se o sistema negar a exclusão, marque NÃO FEITO com a mensagem exata da negativa.

PARTE 4. PROJETOS DUPLICADOS (examinar, NÃO arquivar)
Para cada um: Pessoal (o de 28/set), COMPROVE ERRADO, Branding COMPROVE e Marketing, Kuraray (o de 16/set) e Rito — Modelo Estratégico Tático Operacional. Liste os documentos e arquivos e as últimas conversas, e diga se há algo que não existe em nenhum outro projeto. Não arquive nada: o Paulo decide depois de ler o seu relatório.

PARTE 5. REGISTRO E RELATÓRIO FINAL
5.1 Grave no diário uma linha por parte (agente 'cowork', sessao 'Prompt único 03/11', frente de título 'Central de frentes%'). Na linha da PARTE 4, use precisa_do_paulo=true e pedido_ao_paulo 'Decidir quais projetos duplicados arquivar'.
5.2 Termine com esta tabela e nada mais:
| Item | FEITO ou NÃO FEITO | Prova ou motivo |
com uma linha para cada um destes: 1.1 regra nas instruções gerais | 1.2 regra no projeto COMPROVE | 1.3 teste no Kuraray (resposta literal) | 1.3 regra nos projetos, se foi necessário (quais) | 2 inventário (projetos lidos, frentes criadas e atualizadas, projetos que não conseguiu abrir) | 3.1 Dental apagada | 3.1 Sexta 16/10 apagada | 4 duplicados (o que cada um tem) | 5.1 diário gravado.
Depois da tabela, liste em no máximo 3 linhas o que ainda depende do Paulo.
```

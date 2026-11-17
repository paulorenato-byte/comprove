# Revisão da prospecção COMPROVE (REC e Elo), com base em números · 17/11/2026

Fonte única: Supabase `dutantiolnlidwxdgdyy`, lido em 17/11/2026. Cada número cita a consulta (Q1 a Q9) do apêndice.
O que não está no banco aparece como **sem dado**. Não estimei nada.

## 1. Funil por canal e lote

### REC · LinkedIn (`rec_li_leads`, Q1)

| Lote | Fichas | Convites | Aceites | Msg1 | FU1 | Respostas | Positiva | Negativa | Outra* | Cortesia |
|---|---|---|---|---|---|---|---|---|---|---|
| Pré-lote out · 1º grau | 12 | – | 4 | 4 | 3 | 4 | 1 | 1 | 1 | 1 |
| Pré-lote out · 2º grau/Sales Nav | 147 | 13 | 13 | 11 | 1 | 8 | 1 | 1 | 1 | 5 |
| **REC 1G 01** (msg1 em 05/11) | 46 | – | 45 | 45 | 14 | 1 | 0 | 1 | 0 | 0 |
| **REC 2G 01** (convites de 02 a 13/11) | 165 | 165 | 98 | 90 | 14 | 21 | 2 | 2 | 3 | 14 |

\* "Outra" é o status `respondeu_outra`: pergunta sobre o convite, telefone passado e conversa paralela. Positiva soma `respondeu_interesse` e `reuniao_convidada`. Cortesia é quem respondeu com status ainda em `msg1_enviada` ou `fu1_enviado`.
FU2 enviados: 0 em todos os lotes. REC 2G 01 tem 15 `sem_aceite`.
Ficaram 137 fichas qualificadas em outubro que nunca foram abordadas (status `qualificado`, Q1b).

### REC · Instagram (`rec_ig_leads`, lote pela etiqueta `[LOTE REC IG nn]` da observação, Q2)

| Lote | Fichas | DMs | FU1 | Respostas | Negativa | Diagnóstico | Na fila |
|---|---|---|---|---|---|---|---|
| IG 00 (23 a 30/10) | 146 | 146 | 19 | 0 | 0 | 0 | 0 |
| IG 01 (03 a 17/11) | 96 | 20 | 0 | 1 | 1 | 0 | 72 |
| IG 02 | 75 | 0 | 0 | 0 | 0 | 0 | 75 |
| IG 03 | 4 | 0 | 0 | 0 | 0 | 0 | 4 |
| Sem etiqueta (pulados) | 115 | 9 | 0 | 0 | 0 | 0 | 0 |

Total: 175 DMs, 1 resposta (negativa), 0 diagnósticos. No site, a origem `ig-prosp` teve 8 visitas e `ig-dm` 3, e nenhuma delas começou o diagnóstico (Q4).

### REC · E-mail (Snov.io)

Números lidos pelo Cowork no painel do Snov.io em 17/11 e passados pelo Paulo:

| Campanha | Período | Contatados | E-mails | Respostas | "Tenho interesse" | Diagnósticos (Q3) |
|---|---|---|---|---|---|---|
| Turma Fundadora · Diagnóstico (3201865) | 20/10 a 02/11 | 3.244 | 7.535 | 9 | 0 | 12 (E1: 9, E2: 3) |
| Base webinar 29/07 (3202265) | out | 44 | 45 | 0 | 0 | 0 |
| Retorno A, B, C e D | desde 03/11 | 371 | 371 | 1 | 0 | 0 |

- Em outubro, 0,12% dos e-mails tiveram resposta (9 de 7.535). Por pessoa contatada, foram 0,37% em diagnóstico (12 de 3.244), 1 reunião (LRA) e 0 vendas.
- Em novembro foram 371 e-mails, 1 resposta e 0 diagnósticos. Os 361 cliques (96 a 99%) são de robô, o que bate com o padrão de Q5.
- Aberturas e cliques não servem como sinal: o E2 marca aberturas igual a entregues (2.292). Só a resposta e o diagnóstico são confiáveis.
- No Snov não há campanha do Elo. Os e-mails do Elo saem da caixa do Paulo.
- Diagnósticos vindos do e-mail: E1 deu 9 (1 deles de ex-cliente) e E2 deu 3, todos entre 21 e 29/10, somando **12 de 24** (Q3).
- Negócios no funil: 4. Desses, 3 responderam, 1 chegou a reunião (LRA, aberta) e 2 foram perdidos (Q6).
- **Retorno A/B/C (03/11):** foram 875 "visitas" à página entre 11h e 15h31 do mesmo dia, todas com sessão única e nenhum evento depois (Q5). É o padrão de robô de segurança de e-mail, então não conta como clique de gente. Depois de 03/11 o e-mail gerou **0 diagnósticos** e 0 checkouts (Q3, Q4).

### REC · do diagnóstico à venda (`rec_diagnosticos`, `rec_vendas`, Q3 e Q7)

- Diagnósticos reais: 24, tirando os de status `teste`. Por origem: e-mail 12, `li-dm` 6, `li-prosp` 4, Meta Ads 1 e sem origem 1.
- **Vendas reais do REC: 0.** O `rec_vendas` só tem os 14 eventos `TESTE_*` de 20/10.
- Os 6 diagnósticos de novembro estão todos com `cad_passo = 0`, e 5 deles não têm `cad_parada`. **A cadência pós-diagnóstico não andou em novembro.**
- 9 dos 24 informaram ticket médio de R$ 30 mil ou mais.
- Meta Ads: 196 sessões no diagnóstico, 5 começaram e 1 terminou (Q4).

### Elo (`negocios` e `tarefas`, cliente 0f76c2e9…, origem `Prospecção ativa (…)`, Q6, Q8 e Q9)

| Canal | Negócios desde 01/10 | Passo 1 feito | Msg principal | Com resposta | Perdidos | Prospect ou mais | Reunião ou mais |
|---|---|---|---|---|---|---|---|
| LinkedIn | 293 | 211 convites | 127 | 23 | 22 | 11 | **0** |
| ↳ lote 2G 01 Elo | 108 | 108 | 43 | 7 | 1 neg. | 6 | 0 |
| E-mail | 242 | 232 e-mail 1 | – | 9 | 13 | 5 | **1** (GBSA, lote 08/10) |
| Instagram | 20 | 12 DM1 | – | 1 | 5 | 0 | 0 |

- 2G 01 Elo: 55 aceites marcados no histórico (Q8). Ainda estão pendentes 61 tarefas "Conferir aceite" e 43 "Follow-up D+3" (Q9).
- 1G 01 Elo: 121 fichas paradas. Nenhuma mensagem principal saiu desde 03/11, porque o ambiente negou o envio pela 8ª vez (central_diario id 189).
- Reuniões e aceites abertos desde outubro, em todo o funil (Q7b): GBSA (e-mail Elo), LRA (e-mail REC), Trivicta com aceite verbal de R$ 30 mil (indicação) e Braz & Santos com aceite verbal (LinkedIn, negócio de 03/09, anterior a outubro).

## 2. Onde o funil perde mais

1. **Diagnóstico → venda: 24 → 0.** Em novembro a cadência nem começou (6 de 6 no passo 0). É a maior perda, porque ali o lead já levantou a mão.
2. **Instagram: 175 DMs → 1 resposta negativa → 0 diagnósticos.** Ainda há 151 fichas qualificadas esperando envio, o que é esforço noturno sem retorno.
3. **LinkedIn REC, do aceite à resposta útil: 98 aceites (2G 01) → 2 positivas (2%).** 14 das 21 respostas são cortesia. O aceite funciona (98 de 165, 59%), o que não converte é a conversa.
4. **Execução, não estratégia:** FU1 saiu para só 14 de 90 (2G 01) e 14 de 45 (1G 01), e FU2 para 0. No Elo, 61 aceites estão por conferir, 43 FU estão vencidos e 121 fichas estão paradas no 1G 01. Boa parte do funil "não converteu" porque a etapa simplesmente não aconteceu.
5. **Qualificação além da capacidade:** 137 fichas de LinkedIn de outubro e 151 de Instagram estão qualificadas e nunca foram abordadas.
6. **LinkedIn Elo: 293 negócios → 0 reuniões desde outubro.** Desde outubro, todas as reuniões que vieram de prospecção saíram do e-mail (2 de 2).

## 3. Recomendação

### Manter
- **E-mail, REC e Elo.** É o único canal com reunião desde outubro (2 de 2) e deu metade dos diagnósticos (12 de 24). No Snov, porém, foram 7.535 e-mails para 9 respostas e 0 vendas. **Só vale renovar o Snov.io (prazo de 18/11) se o e-mail passar a pedir diagnóstico ou conversa.** Como está hoje, no Retorno A a D (371 e-mails, 1 resposta, 0 diagnósticos), não vale.
- **LinkedIn REC, 1º e 2º grau, para gerar diagnóstico.** O 2G 01 teve 59% de aceite e deu 4 diagnósticos `li-prosp`. O 1G 01 teve só 1 resposta, mas houve 3 diagnósticos `li-dm` entre 06 e 09/11, logo depois da msg1 de 05/11. Isso é proximidade de data, não prova de origem. Manter, desde que os FU saiam.

### Cortar
- **Prospecção REC por Instagram,** inclusive a qualificação noturna dos lotes IG 02 e IG 03. Número: 175 DMs, 1 resposta (negativa), 0 diagnósticos.
- **Qualificar fichas novas** de LinkedIn e Instagram enquanto houver fila. Número: 137 e 151 fichas paradas.
- **Link do e-mail para a página de vendas** (Retorno A/B/C). Número: 0 diagnósticos depois de 03/11, contra 12 quando o link levava ao diagnóstico (E1 e E2).

### Testar
1. **Destravar a cadência pós-diagnóstico e fazer contato pessoal do Paulo** com os 9 diagnósticos de ticket ≥ R$ 30 mil, oferecendo uma conversa (Elo), não o curso. Número: 24 diagnósticos e 0 vendas, com 6 de 6 de novembro no passo 0.
2. **E-mail de retorno com link para o diagnóstico** em vez da página de vendas, em teste A/B sobre o mesmo público. Número: 12 contra 0 diagnósticos.
3. **Duas semanas só de execução no LinkedIn:** zerar FU1 e FU2 vencidos e conferir os aceites do Elo antes de abrir lote novo. Medir as positivas por cada 100 aceites. Número de partida: 2 em 98 no REC 2G 01.

## 4. O REC (atualização de 17/11, depois dos números do Snov)

Conclusão do Paulo: o REC é um produto que se vende em reunião, não por compra direta. Os números confirmam:
- Compra direta: 7.535 e-mails, 175 mensagens no Instagram, 196 sessões vindas do Meta Ads e 24 diagnósticos, com **0 vendas**. Houve 4 eventos de checkout em todo o período (Q4).
- O pouco que andou passou por conversa: a LRA saiu de um e-mail do REC, virou reunião e está aberta (Q7b).

Proposta para o comando diário do Cowork, com o REC dentro da nova estrutura:
1. **Parar a aquisição de compra direta** do REC: Instagram, Retorno A a D com link para a página de vendas e anúncio levando ao checkout.
2. **O diagnóstico vira a porta de entrada de uma conversa,** não da página de vendas. O resultado do diagnóstico oferece agendar uma conversa, e a cadência pós-diagnóstico chama para a conversa.
3. **Separar pela régua do ticket médio:** quem informou ticket de R$ 30 mil ou mais conversa sobre o Elo; os demais conversam sobre o REC. Primeira lista para testar: os 24 diagnósticos que já existem (9 de um lado e 15 do outro).
4. **Prospecção de LinkedIn e e-mail com um único pedido:** fazer o diagnóstico ou agendar a conversa.
5. **Medir por semana:** conversas agendadas, conversas feitas e vendas. Abertura e clique deixam de contar.

O estudo de 03/11 (`claude/ESTUDO-retroativo-estrategias-rec-2026-11-03.md`, no projeto do Cowork) não pôde ser lido daqui. Só se conhece o resumo do central_diario, id 56: escada com evento de entrada "Planejamento Comercial do Escritório" (R$ 797, 870 ou 997), 13 estratégias e teste de 30 dias. Ficaram para o Paulo decidir o preço do REC, a Laiane e o Vini na conversa de venda, a garantia de 15 dias e o formulário de aplicação no DUO e no Elo. A fusão do estudo com estes números ficou registrada como frente com a bola no Cowork.

## Apêndice · consultas

- **Q1** `rec_li_leads` agrupado por lote (etiqueta `[LOTE REC … ficha` em `observacao`; sem etiqueta = pré-lote pela `fonte`): `count(convite_em)`, `count(aceite_em)`, `count(msg1_em)`, `count(fu1_em)`, `count(fu2_em)`, `count(respondido_em)` e contagem por `status`.
- **Q1b** `select fonte, count(*) from rec_li_leads where status='qualificado' group by 1` → 25 + 8 + 54 + 25 + 25 = 137.
- **Q2** `rec_ig_leads` agrupado por `substring(observacao from '\[LOTE (REC IG [0-9]+)')`: `count(dm_enviada_em)`, `count(fu1_em)`, `count(respondido_em)`, `diagnostico_feito`, `status`.
- **Q3** `rec_diagnosticos where status<>'teste'`: `origem`, `criado_em`, `ticket_medio`, `cad_passo`, `cad_parada`, `comprou`.
- **Q4** `rec_eventos where criado_em>='2026-10-01'` agrupado por `origem, pagina, evento`, com `count(distinct sessao)`.
- **Q5** `rec_eventos where origem in ('e1','e2','snov-retorno-a','snov-retorno-b','snov-retorno-c') and evento='visita'` agrupado por dia, com `min` e `max` de hora.
- **Q6** `negocios where cliente_id='0f76c2e9-…' and criado_em>='2026-10-01'` agrupado por `origem`: total, `status='perdido'`, `historico ~* '\[RESPOSTA'`, `estagio<>'suspect'` e estágio em reunião, proposta ou aceite verbal.
- **Q7** `rec_vendas` agrupado por `evento, status`: só há eventos `TESTE_*`. **Q7b** `negocios` do mesmo cliente com estágio em reunião ou aceite verbal.
- **Q8** `negocios` de origem `Prospecção ativa%`, com lote extraído de `historico` (`Lote …`) e marcadores `[CONVITE ENVIADO`, `[ACEIT`, `[RESPOSTA`.
- **Q9** `tarefas join negocios` do mesmo cliente: negócios distintos com tarefa completa ou pendente por passo (convite LI, msg principal LI, e-mail 1, DM1 IG, conferir aceite, FU D+3).

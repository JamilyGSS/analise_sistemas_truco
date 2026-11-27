# Truco Paulista de Duas Duplas — Regras de Negócio

## Integrantes

- Giovana Ferreira Waterkemper — RA 143844
- Jamily Gonçalves de Sales Souza — RA 143048

## Glossário

| Termo | Definição |
|---|---|
| **Partida** | Jogo completo, até uma dupla chegar a 12 pontos. |
| **Mão** | Disputa em até 3 rodadas, com valor em pontos. |
| **Rodada** | Cada jogador joga uma carta e as 4 são comparadas. |
| **Vira** | Carta virada que define as manilhas. |
| **Manilha** | Carta mais forte da mão. |
| **Correr** | Recusar um aumento e entregar a mão. |
| **Valor vigente** | Pontos que a mão vale naquele momento. |

---

## RN-01 — Jogadores e duplas

**Regra:**
- A partida tem 4 jogadores identificados, em 2 duplas de 2 jogadores distintos.
- Cada jogador pertence a uma única dupla, e os parceiros ficam frente a frente.
- Só se inicia a partida com os 4 jogadores presentes e as duas duplas formadas.
- 🔶 As duplas não mudam depois de iniciada a partida.

**Origem:** UC-001, UC-002

---

## RN-02 — Partida, mão e rodada

**Regra:**
- A partida é uma sequência de mãos e termina quando uma dupla chega a 12 pontos (RN-14).
- O placar inicial é 0 × 0.
- A mão tem no máximo 3 rodadas.
- A ordem de jogo segue o sentido horário e alterna as duplas.

**Origem:** UC-001, UC-012, UC-014

---

## RN-03 — Baralho

**Regra:**
- São 40 cartas: A, 2, 3, 4, 5, 6, 7, Q, J, K em 4 naipes (♦ Ouros, ♠ Espadas, ♥ Copas, ♣ Paus).
- Não há 8, 9, 10 nem coringas.

**Origem:** UC-003

---

## RN-04 — Força das cartas comuns

**Regra:**
- Da menor para a maior: **4, 5, 6, 7, Q, J, K, A, 2, 3**.
- O naipe não conta entre cartas comuns, e cartas de mesmo valor empatam.

**Origem:** UC-010

---

## RN-05 — Vira e manilha

**Regra:**
- O Vira é uma carta do baralho restante, revelada depois da distribuição, que não pertence a nenhum jogador.
- A manilha é o valor seguinte ao do Vira na ordem cíclica de RN-04.
- Vira e manilhas são definidos de novo a cada mão.

| Vira | 4 | 5 | 6 | 7 | Q | J | K | A | 2 | 3 |
|---|---|---|---|---|---|---|---|---|---|---|
| **Manilha** | 5 | 6 | 7 | Q | J | K | A | 2 | 3 | 4 |

**Origem:** UC-015

---

## RN-06 — Hierarquia da mão

**Regra:**
- As 4 cartas da manilha vencem qualquer carta comum.
- Entre as manilhas, a força é **♦ < ♠ < ♥ < ♣**. O 4 de Paus ("zap") só é o mais forte quando o Vira é 3.
- Depois das manilhas vêm as comuns de RN-04, sem o valor da manilha.
- Uma carta coberta vale zero (RN-20).
- Exemplo: com Vira 7 a manilha é Q, e a ordem fica ♣Q > ♥Q > ♠Q > ♦Q > 3 > 2 > A > K > J > 7 > 6 > 5 > 4.

**Origem:** UC-010, UC-015

---

## RN-07 — Distribuição

**Regra:**
- A cada mão usa-se um baralho completo, embaralhado de novo.
- Cada jogador recebe 3 cartas. As 12 cartas e o Vira são 13 cartas distintas.
- As cartas são privadas, e o placar acumulado é preservado.
- Se a distribuição falhar, nenhuma jogada é aceita até a correção.

**Origem:** UC-003

---

## RN-08 — Distribuidor e ordem

**Regra:**
- 🔶 O distribuidor da 1ª mão é sorteado e depois passa ao jogador seguinte no sentido horário.
- 🔶 O 1º a jogar é o seguinte ao distribuidor.
- 🔶 O vencedor de uma rodada inicia a próxima. Se a rodada empatou, inicia a próxima quem iniciou a empatada.

**Origem:** UC-019

---

## RN-09 — Preparação da mão

**Regra:** a preparação segue esta ordem:
1. Definir distribuidor e ordem.
2. Distribuir as cartas.
3. Revelar o Vira e definir as manilhas.
4. Verificar Mão de Onze ou Mão de Ferro (RN-21, RN-23).
5. Iniciar a 1ª rodada.

**Origem:** UC-019, UC-003, UC-015, UC-017, UC-018

---

## RN-10 — Jogada válida

**Regra:**
- A jogada é válida quando a partida está em andamento, é a vez do jogador, a carta está na mão dele e não há pedido de aposta ou decisão pendente.
- A carta jogada sai da mão e não pode ser usada de novo.
- Cada jogador joga uma carta por rodada.

**Origem:** UC-005

---

## RN-11 — Vencedor da rodada

**Regra:**
- Vence a carta mais forte segundo RN-06.
- Se as mais fortes são de duplas diferentes e iguais, a rodada **empata**.
- Se as mais fortes são da mesma dupla, a dupla vence, e o vencedor individual é quem jogou primeiro entre elas.

**Origem:** UC-010

---

## RN-12 — Resultado da mão

**Regra:** duas vitórias de rodada encerram a mão. Tabela (A e B são as duplas; E é empate; os casos de B são simétricos):

| 1ª | 2ª | 3ª | Vence a mão |
|---|---|---|---|
| A | A | — | A |
| A | E | — | A |
| E | A | — | A |
| A | B | A / B | A / B |
| A | B | E | A (venceu a 1ª) |
| E | E | A / B | A / B |
| E | E | E | ninguém (RN-13) |

**Origem:** UC-011

---

## RN-13 — Mão empatada

**Regra:**
- 🔶 Se as 3 rodadas empatam, ninguém pontua, o placar não muda e começa nova mão com o próximo distribuidor.
- Vale também na Mão de Onze e na Mão de Ferro.

**Origem:** UC-010, UC-011

---

## RN-14 — Pontuação

**Regra:**
- A mão começa valendo 1, e os valores possíveis são 1, 3, 6, 9 e 12.
- O vencedor recebe o valor vigente, o perdedor nada, e o placar nunca diminui.
- 🔶 O placar de cada dupla é limitado a 12 (11 + 3 aparece como 12).
- A dupla que chega a 12 vence a partida.
- O fim é verificado antes de preparar nova mão, e depois dele nenhuma jogada é aceita.
- Consultar o placar não o altera.

**Origem:** UC-012, UC-013, UC-014

---

## RN-15 — Quando pedir truco ou aumento

**Regra:**
- 🔶 Só se pode pedir na vez do jogador, antes de jogar a carta, com a mão em andamento e sem decisão de aposta pendente.
- Não é permitido na Mão de Onze nem na Mão de Ferro.
- O pedido pode ser feito em qualquer rodada.

**Origem:** UC-006, UC-017, UC-018

---

## RN-16 — Sequência e alternância

**Regra:**
- Os pedidos seguem 1 → **Truco (3)** → **Seis (6)** → **Nove (9)** → **Doze (12)**, sem pular etapas.
- O pedido de um jogador vale para a dupla.
- 🔶 Só a dupla que não fez o último pedido pode pedir o seguinte.

**Origem:** UC-009

---

## RN-17 — Respostas ao pedido

**Regra:**
- 🔶 Qualquer integrante da dupla adversária responde por ela, e enquanto o pedido está pendente ninguém joga carta.
- **Aceitar:** o valor vigente passa ao valor pedido e o jogo continua.
- **Aumentar:** aceita o pedido atual e propõe o seguinte, e a dupla que pediu primeiro responde.
- **Correr:** encerra a mão (RN-18).

**Origem:** UC-007, UC-008, UC-009

---

## RN-18 — Pontos ao correr

**Regra:** quem pediu vence a mão e recebe o valor vigente antes do pedido recusado.

| Pedido recusado | Truco (3) | Seis (6) | Nove (9) | Doze (12) |
|---|---|---|---|---|
| **Pontos de quem pediu** | 1 | 3 | 6 | 9 |

**Origem:** UC-008, UC-009

---

## RN-19 — Limites do pedido

**Regra:**
- O valor máximo é 12, e com a mão valendo 12 não há aumento.
- Um pedido ou uma aceitação registrados não podem ser desfeitos.
- O valor vigente vale para a mão inteira.
- Pedido inválido é rejeitado com o motivo, e sequência errada informa o aumento permitido.

**Origem:** UC-006, UC-009

---

## RN-20 — Carta coberta

**Regra:**
- Só pode ser jogada na 2ª e na 3ª rodada, nunca na 1ª nem na Mão de Ferro.
- Fica virada na mesa e vale zero na comparação: perde para qualquer carta aberta e empata com outra coberta.
- 🔶 Seu valor nunca é revelado, nem ao parceiro nem no histórico.
- Se não for possível ocultá-la, a jogada é cancelada.

**Origem:** UC-016

---

## RN-21 — Mão de Onze: condição e decisão

**Regra:**
- É Mão de Onze quando, no início da mão, **exatamente uma** dupla tem 11 pontos e a outra tem 10 ou menos. Com 11 × 11 vale RN-23.
- Antes de jogar, só os dois integrantes da dupla de 11 podem ver as cartas um do outro.
- A dupla decide **jogar** ou **correr**, e a decisão precisa ser confirmada.

**Origem:** UC-017, UC-004

---

## RN-22 — Mão de Onze: resultado

**Regra:**
- Se joga, a mão vale **3**. 🔶 Nenhuma dupla pode pedir truco nem aumento.
- Se corre, a mão termina sem jogadas e a adversária recebe **1** ponto. Se com isso ela passar de 10 a 11, a próxima mão é de Ferro.
- Se perde a mão, a adversária recebe 3.
- 🔶 Se as 3 rodadas empatam, a dupla continua com 11 e a próxima mão é Onze de novo.

**Origem:** UC-017

---

## RN-23 — Mão de Ferro: regras

**Regra:**
- É Mão de Ferro quando as duas duplas têm 11 pontos no início da mão.
- O jogo é no escuro. 🔶 Ninguém vê as próprias cartas nem as do parceiro, escolhe uma posição da mão, e a carta é aberta na mesa ao ser jogada.
- O Vira e as manilhas valem normalmente.
- Não há carta coberta, truco, aumento, correr nem sinais.

**Origem:** UC-018, UC-005, UC-016

---

## RN-24 — Mão de Ferro: resultado

**Regra:**
- 🔶 A mão vale 1 ponto, e quem a vence vence a partida (11 + 1).
- Se as 3 rodadas empatam, o placar fica 11 × 11 e joga-se nova Mão de Ferro, com redistribuição e outro distribuidor.

**Origem:** UC-018

---

## RN-25 — Visibilidade

**Regra:**
- A mão de um jogador é visível só para ele.
- Cartas jogadas abertas, o Vira e as manilhas são públicos. Cartas cobertas nunca mostram o valor.
- Exceções: a dupla de 11 se vê (RN-21), e na Mão de Ferro nem o dono vê as cartas.
- Cartas que sobrarem ao fim da mão continuam ocultas.
- Jogador não identificado não vê cartas privadas.
- O histórico e as mensagens não revelam cartas privadas nem cobertas.

**Origem:** UC-004, UC-005, UC-016, UC-023

---

## RN-26 — Sinais ao parceiro

**Regra:**
- São visuais, predefinidos e sem texto livre (mínimo: "Tenho manilha", "Tenho um 3", "Peça truco", "Estou fraco").
- Chegam só ao parceiro e não alteram cartas, rodada, valor ou placar.
- 🔶 Não aparecem no histórico, são configuráveis (padrão: habilitados) e ficam indisponíveis na Mão de Ferro.
- O sistema não verifica se o sinal é verdadeiro.
- Com o parceiro desconectado, o sinal não é entregue e o remetente é avisado.

**Origem:** UC-020

---

## RN-27 — Desconexão e reconexão

**Regra:**
- Desconectar não é desistir: o jogador mantém posição, cartas e dupla, e o sistema registra o estado o tempo todo.
- A reconexão exige identificação válida e partida ativa.
- Ao voltar, o jogador recebe só as informações a que tem direito, sem repetir jogadas já registradas, e fora da vez apenas acompanha.
- 🔶 Se for a vez do desconectado, a partida aguarda, sem jogada automática (com tempo máximo configurável).
- Partida encerrada ou estado irrecuperável impedem a reconexão.

**Origem:** UC-021, UC-019

---

## RN-28 — Histórico

**Regra:**
- O sistema registra: início, duplas, distribuidor, distribuição (sem revelar cartas), Vira e manilhas, jogadas (cobertas sem valor), pedidos e respostas, resultados de rodada e mão, pontos, Onze e Ferro, desconexões e fim da partida.
- Cada registro traz ordem, jogador, dupla, mão, rodada e descrição.
- Nada é editado ou apagado.
- Os mais recentes aparecem primeiro, e a consulta não altera a partida.
- Ele se atualiza durante o jogo e fica completo depois do fim.
- Sem eventos, informa que não há ações além do início.

**Origem:** UC-023

---

## RN-29 — Ajuda contextual

**Regra:**
- Mostra um resumo curto das regras do estado atual (rodada, valor da mão, Vira, manilhas, Onze ou Ferro), com acesso à explicação completa.
- Sem condição especial, mostra as regras gerais. Com condição especial, destaca-a.
- Sem estado disponível, oferece as regras gerais.
- Consultar não altera a partida nem bloqueia a mesa.

**Origem:** UC-022

---

## RN-30 — Invariantes

**Regra:** são sempre verdadeiros:
- As 12 cartas e o Vira são 13 cartas diferentes.
- Ninguém tem mais de 3 cartas nem joga mais de 3 vezes por mão.
- Carta jogada não volta nem é jogada de novo.
- O valor da mão é 1, 3, 6, 9 ou 12 (3 na Mão de Onze).
- Há no máximo uma decisão pendente.
- O placar é não decrescente e no máximo 12.
- Mão decidida ou partida encerrada não aceitam jogadas.
- Estado inconsistente nunca produz vencedor.
- Há no máximo 4 cartas na mesa por rodada.

**Origem:** todos os casos de uso

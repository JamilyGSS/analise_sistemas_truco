# Truco Paulista de Duas Duplas — Requisitos Funcionais

## Integrantes

- Giovana Ferreira Waterkemper — RA 143844
- Jamily Gonçalves de Sales Souza — RA 143048

## RF-01 — Iniciar partida

**O sistema deve:**
- Permitir que um jogador solicite o início de uma nova partida.
- Verificar se há 4 jogadores (senão, informar que são necessários quatro e aguardar).
- Verificar se as duplas foram definidas (senão, pedir a formação).
- Criar a partida com placar 0 × 0, registrar o estado inicial e iniciar a preparação da 1ª mão.
- Informar se a criação falhar.

**Casos de uso:** UC-001 · **Regras:** RN-01, RN-02

---

## RF-02 — Formar duplas

**O sistema deve:**
- Apresentar os 4 participantes e permitir escolher os integrantes das duas duplas.
- Validar dois jogadores distintos por dupla (jogador repetido e dupla incompleta pedem nova seleção).
- Registrar as duplas, mostrar a composição final e posicionar os parceiros frente a frente.
- Informar se não for possível salvar.

**Casos de uso:** UC-002 · **Regras:** RN-01

---

## RF-03 — Alternar distribuidor e ordem

**O sistema deve:**
- Sortear o distribuidor da 1ª mão e passar ao seguinte a cada mão.
- Definir e informar a ordem de jogo.
- Preservar a posição de jogador desconectado.
- Impedir a distribuição se a ordem for inválida.

**Casos de uso:** UC-019 · **Regras:** RN-08, RN-09

---

## RF-04 — Distribuir cartas

**O sistema deve:**
- Preparar o baralho de 40 cartas e embaralhar.
- Dar 3 cartas a cada jogador, registrá-las e mantê-las privadas.
- Preservar o placar em nova mão.
- Se falhar, informar e impedir jogadas até a correção.

**Casos de uso:** UC-003 · **Regras:** RN-03, RN-07

---

## RF-05 — Revelar Vira e definir manilhas

**O sistema deve:**
- Revelar o Vira depois da distribuição.
- Definir as 4 manilhas e aplicar a ordem de naipes ♦ < ♠ < ♥ < ♣.
- Impedir jogadas enquanto o Vira estiver ausente ou inválido.

**Casos de uso:** UC-015 · **Regras:** RN-05, RN-06

---

## RF-06 — Detectar mão especial

**O sistema deve:**
- Depois do Vira, verificar o placar.
- Acionar a Mão de Onze (exatamente uma dupla com 11) ou a Mão de Ferro (11 × 11).

**Casos de uso:** UC-017, UC-018 · **Regras:** RN-09, RN-21, RN-23

---

## RF-07 — Visualizar cartas

**O sistema deve:**
- Identificar o jogador e mostrar suas cartas (cartas já jogadas aparecem como usadas, sem reuso).
- Manter ocultas as cartas dos demais, salvo exceções.
- Impedir a consulta de jogador não identificado e pedir identificação.

**Casos de uso:** UC-004 · **Regras:** RN-25

---

## RF-08 — Jogar carta

**O sistema deve:**
- Indicar a vez e permitir escolher a carta.
- Validar a jogada (se inválida, informar e permitir nova escolha).
- Registrar a carta, tirá-la da mão e mostrá-la na mesa conforme a visibilidade.
- Passar a vez, ou acionar o vencedor da rodada ao completar as 4 cartas.

**Casos de uso:** UC-005 · **Regras:** RN-10

---

## RF-09 — Jogar carta coberta

**O sistema deve:**
- Oferecer a opção só na 2ª e 3ª rodada e fora da Mão de Ferro (senão, informar que não está disponível).
- Registrar a carta sem revelar o valor e marcá-la como usada.
- Cancelar a jogada se a ocultação falhar.

**Casos de uso:** UC-016 · **Regras:** RN-20

---

## RF-10 — Jogar no escuro (Mão de Ferro)

**O sistema deve:**
- Fazer o jogador escolher a posição da carta sem vê-la.
- Abrir a carta na mesa ao ser jogada.

**Casos de uso:** UC-005, UC-016 · **Regras:** RN-23

---

## RF-11 — Pedir truco e aumentar

**O sistema deve:**
- Permitir o pedido na vez do jogador e verificar se é permitido (senão, informar o motivo).
- Identificar o próximo valor (3, 6, 9 ou 12) e registrar o pedido.
- Avisar a dupla adversária e aguardar a resposta.

**Casos de uso:** UC-006, UC-009 · **Regras:** RN-15, RN-16

---

## RF-12 — Responder ao pedido

**O sistema deve:**
- Mostrar o pedido pendente e permitir **aceitar**, **aumentar** ou **correr**.
- Ao aceitar, atualizar o valor e retomar a partida.
- Ao correr, encerrar a mão, dar os pontos de RN-18 e atualizar o placar.
- Informar se não houver pedido válido ou se a resposta não for permitida.

**Casos de uso:** UC-007, UC-008, UC-009 · **Regras:** RN-17, RN-18

---

## RF-13 — Controlar a sequência de apostas

**O sistema deve:**
- Rejeitar sequência inválida informando o aumento permitido.
- Impedir aumentos com a mão em 12.
- Controlar qual dupla pode pedir o próximo aumento.

**Casos de uso:** UC-009 · **Regras:** RN-16, RN-19

---

## RF-14 — Bloquear apostas em mãos especiais

**O sistema deve:**
- Desabilitar pedidos e aumentos na Mão de Onze e na Mão de Ferro.
- Rejeitar a tentativa com aviso de que não é permitido.

**Casos de uso:** UC-017, UC-018 · **Regras:** RN-15, RN-22, RN-23

---

## RF-15 — Determinar o vencedor da rodada

**O sistema deve:**
- Recuperar as cartas e aplicar a hierarquia (Vira e manilhas).
- Identificar a carta e a dupla vencedoras, ou o empate, e registrar o resultado.
- Tratar cartas cobertas como zero, sem revelá-las.
- Informar estado inconsistente sem decidir o vencedor.

**Casos de uso:** UC-010 · **Regras:** RN-06, RN-11, RN-30

---

## RF-16 — Determinar o vencedor da mão

**O sistema deve:**
- Aplicar a tabela de resultado (empates incluídos) e encerrar a mão assim que decidida.
- Iniciar a próxima rodada se a mão não estiver decidida (o vencedor da anterior começa).
- Definir o valor pelos pedidos aceitos.
- Tratar mão empatada sem pontuar.
- Manter a mão pendente se o resultado for inconclusivo.

**Casos de uso:** UC-011 · **Regras:** RN-08, RN-12, RN-13

---

## RF-17 — Atualizar a pontuação

**O sistema deve:**
- Somar o valor da mão à dupla vencedora e manter a outra.
- Limitar o placar a 12 e mostrar o placar novo.
- Acionar o encerramento aos 12 pontos, ou preparar a próxima mão.
- Se falhar, preservar o último placar confirmado.

**Casos de uso:** UC-012 · **Regras:** RN-14

---

## RF-18 — Consultar o placar

**O sistema deve:**
- Mostrar os pontos das duas duplas a qualquer momento (0 × 0 no início), sem alterá-los.
- Informar se não for possível recuperá-lo.

**Casos de uso:** UC-013 · **Regras:** RN-14

---

## RF-19 — Encerrar a partida

**O sistema deve:**
- Registrar a dupla vencedora, impedir novas jogadas e mostrar o placar final.
- Oferecer nova partida.
- Se falhar o registro, manter o estado consistente.

**Casos de uso:** UC-014 · **Regras:** RN-14

---

## RF-20 — Gerenciar a Mão de Onze

**O sistema deve:**
- Informar a dupla e deixar os parceiros verem as cartas um do outro, sem expor aos adversários.
- Registrar a decisão de jogar ou correr, com confirmação.
- Aplicar o resultado: mão valendo 3 sem truco, ou 1 ponto aos adversários se correr.

**Casos de uso:** UC-017 · **Regras:** RN-21, RN-22

---

## RF-21 — Gerenciar a Mão de Ferro

**O sistema deve:**
- Informar o empate em 11 e distribuir com as cartas ocultas dos donos.
- Desabilitar truco e aumentos.
- Determinar o resultado e declarar vencedora da partida a dupla que vencer a mão.
- Impedir jogadas se a preparação falhar.

**Casos de uso:** UC-018 · **Regras:** RN-23, RN-24

---

## RF-22 — Enviar sinais ao parceiro

**O sistema deve:**
- Mostrar os sinais predefinidos e validar a escolha.
- Entregar o sinal só ao parceiro, sem alterar cartas, valor ou placar, e sem registrá-lo no histórico.
- Permitir habilitar ou desabilitar os sinais.
- Informar sinal indisponível, parceiro desconectado ou falha de envio.

**Casos de uso:** UC-020 · **Regras:** RN-26

---

## RF-23 — Reconectar jogador

**O sistema deve:**
- Detectar a desconexão e preservar posição e cartas.
- Validar a identificação e verificar se a partida está ativa.
- Recuperar e restaurar o estado autorizado sem repetir jogadas, respeitando a vez.
- Confirmar a reconexão e avisar os demais jogadores.

**Casos de uso:** UC-021, UC-019 · **Regras:** RN-27

---

## RF-24 — Consultar regras da jogada

**O sistema deve:**
- Abrir a ajuda na tela da partida sem alterar o estado.
- Mostrar o resumo contextual (rodada, valor, Vira, manilhas, Onze ou Ferro) e a explicação completa sob pedido.
- Mostrar as regras gerais quando não houver regra especial ou o estado estiver indisponível.
- Permitir fechar a ajuda e voltar à partida.

**Casos de uso:** UC-022 · **Regras:** RN-29

---

## RF-25 — Consultar o histórico

**O sistema deve:**
- Abrir o histórico e mostrar os eventos em ordem cronológica, com jogador, dupla, mão e rodada (mais recentes primeiro).
- Atualizá-lo durante o jogo e mantê-lo completo após o fim.
- Informar quando estiver vazio.
- Permitir tentar de novo se falhar ao carregar.

**Casos de uso:** UC-023 · **Regras:** RN-28

---

## RF-26 — Registrar eventos e estado

**O sistema deve:**
- Gravar cada ação relevante no histórico, sem cartas privadas nem cobertas.
- Persistir o estado da partida para permitir a reconexão.

**Casos de uso:** UC-023, UC-021 · **Regras:** RN-25, RN-27, RN-28

---

## RF-27 — Ambientar a mesa

**O sistema deve:**
- Mostrar a tela principal como uma mesa de truco, com área central para a rodada, as duas duplas identificadas e destaque ao jogador da vez.
- Usar cartas com aparência de baralho físico (proporção, cantos arredondados, naipes legíveis, frente e verso coerentes).

**Casos de uso:** Diretrizes de interface · **Regras:** RN-03

---

## RF-28 — Organizar a mesa e as informações

**O sistema deve:**
- Posicionar os parceiros frente a frente.
- Deixar a mão do jogador em primeiro plano e as dos demais ocultas.
- Manter placar, valor da mão, duplas, Vira e manilhas sempre visíveis, sem competir com as cartas.

**Casos de uso:** Diretrizes de interface · **Regras:** RN-25

---

## RF-29 — Dar feedback e abrigar o apoio

**O sistema deve:**
- Destacar a vez, a ação realizada, o pedido de truco pendente e o fim de rodada e de mão, com animações breves.
- Manter regras e histórico em painéis recolhíveis que não bloqueiem a mesa nem uma jogada.

**Casos de uso:** Diretrizes de interface, UC-022, UC-023 · **Regras:** RN-28, RN-29

---

## RF-30 — Garantir consistência e imersão sutil

**O sistema deve:**
- Usar padrões visuais consistentes e contraste adequado em botões, estados de cartas e mensagens.
- Oferecer sons e animações que possam ser reduzidos ou desativados e que nunca escondam informação importante.

**Casos de uso:** Diretrizes de interface · **Regras:** —

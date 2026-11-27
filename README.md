# Truco Paulista em Duplas 

Este repositório reúne a modelagem e a documentação de um jogo de **Truco Paulista** jogado em **duas duplas** (4 jogadores): os casos de uso, as regras de negócio e os requisitos funcionais e não funcionais.

## Sobre o projeto

O objetivo é aplicar conceitos de **Engenharia de Software** na modelagem de um jogo de cartas com regras dinâmicas, controle de turnos, manilhas definidas pelo Vira, apostas e pontuação. A modelagem parte de **23 casos de uso** (UC-001 a UC-023), e as regras e os requisitos derivam deles e apontam de volta para eles.

### Regras do jogo adotadas

- **Baralho:** 40 cartas (A, 2, 3, 4, 5, 6, 7, Q, J, K em 4 naipes), sem 8, 9 e 10.
- **Força das cartas comuns:** 4 < 5 < 6 < 7 < Q < J < K < A < 2 < 3.
- **Vira e manilhas:** o Vira é revelado a cada mão e as manilhas são as 4 cartas do valor seguinte ao dele (por exemplo, Vira 7 → manilha Q).
- **Hierarquia dos naipes nas manilhas:** Paus > Copas > Espadas > Ouros.
- **Estrutura do jogo:** a **partida** é jogada em **mãos**, e cada mão tem até 3 **rodadas**. Vence a mão a dupla que ganhar 2 rodadas, com regras de empate. A partida termina aos **12 pontos**.
- **Apostas:** Truco (3), Seis (6), Nove (9) e Doze (12), em sequência, com alternância entre as duplas. Quem corre entrega a mão e a dupla adversária recebe o valor vigente antes do pedido (1, 3, 6 ou 9 pontos).
- **Cartas cobertas:** podem ser jogadas na 2ª e na 3ª rodada, e valem zero na comparação.
- **Mão de Onze:** quando uma dupla tem 11 pontos, ela vê as cartas do parceiro e decide jogar (a mão vale 3) ou correr (1 ponto para a adversária). Não há truco.
- **Mão de Ferro:** quando as duas duplas têm 11 pontos, as cartas são jogadas no escuro, sem truco, e quem vencer a mão vence a partida.
- **Duplas:** os parceiros ficam frente a frente, o distribuidor gira a cada mão e os turnos seguem o sentido horário.

## Principais funcionalidades

- **Modelagem UML:** diagrama de casos de uso.
- **Casos de uso:** 23 casos de uso, de iniciar a partida até consultar regras e histórico.
- **Regras de negócio:** 30 regras (RN-01 a RN-30), cada uma ligada aos casos de uso de origem.
- **Requisitos funcionais:** 30 requisitos (RF-01 a RF-30), ligados aos casos de uso e às regras.
- **Requisitos não funcionais:** 30 requisitos (RNF-01 a RNF-30), com metas verificáveis de desempenho, confiabilidade, segurança, usabilidade, acessibilidade e manutenção.

## Integrantes da dupla

- **Giovana Ferreira Waterkemper** — ra143844
- **Jamily Gonçalves de Sales Souza** — ra143048

# Truco Paulista de Duas Duplas — Requisitos Não Funcionais

## Integrantes

- Giovana Ferreira Waterkemper — RA 143844
- Jamily Gonçalves de Sales Souza — RA 143048

## RNF-01 — Tempo de resposta

**Categoria:** Desempenho

**Requisito:** Validar e registrar uma jogada, pedido ou resposta e atualizar a tela em até 300 ms para 95% das ações.

**Verificação:** Medição

---

## RNF-02 — Preparação da mão

**Categoria:** Desempenho

**Requisito:** Embaralhar, distribuir 12 cartas e revelar o Vira em até 1 s.

**Verificação:** Medição

---

## RNF-03 — Animações

**Categoria:** Desempenho

**Requisito:** Animações de até 500 ms cada, sem bloquear a entrada do jogador.

**Verificação:** Inspeção

---

## RNF-04 — Detecção e restauração

**Categoria:** Desempenho

**Requisito:** Detectar a desconexão em até 10 s e restaurar o estado de quem reconecta em até 5 s.

**Verificação:** Medição

---

## RNF-05 — Abertura do histórico

**Categoria:** Desempenho

**Requisito:** Abrir o histórico com até 500 eventos em até 1 s.

**Verificação:** Medição

---

## RNF-06 — Atomicidade

**Categoria:** Confiabilidade

**Requisito:** Jogada, pedido, resposta e atualização de placar são atômicos: aplicam-se por inteiro ou não se aplicam.

**Verificação:** Teste

---

## RNF-07 — Estado após falha

**Categoria:** Confiabilidade

**Requisito:** Em qualquer falha (exceções E1), o estado confirmado anterior é mantido, sem estado parcial.

**Verificação:** Teste

---

## RNF-08 — Comandos repetidos e simultâneos

**Categoria:** Confiabilidade

**Requisito:** Comandos repetidos (clique duplo, reenvio) não duplicam jogadas, e ações simultâneas na mesma partida são serializadas: só a primeira vale.

**Verificação:** Teste

---

## RNF-09 — Persistência

**Categoria:** Confiabilidade

**Requisito:** O estado da partida é persistido a cada mudança para ser recuperado após falha ou reinício.

**Verificação:** Teste

---

## RNF-10 — Disponibilidade

**Categoria:** Confiabilidade

**Requisito:** Disponibilidade de 99% durante a operação.

**Verificação:** Medição

---

## RNF-11 — Invariantes

**Categoria:** Integridade

**Requisito:** Os invariantes de RN-30 valem em todos os estados alcançáveis e são verificados por testes.

**Verificação:** Teste

---

## RNF-12 — Embaralhamento

**Categoria:** Integridade

**Requisito:** O embaralhamento é uniforme (Fisher–Yates) com fonte aleatória segura, e as cartas futuras são imprevisíveis para o cliente.

**Verificação:** Inspeção e teste estatístico

---

## RNF-13 — Motor de regras

**Categoria:** Integridade

**Requisito:** Toda regra é validada pelo motor de regras (nunca só pela interface), e o motor é determinístico: mesmo estado e entrada, mesmo resultado.

**Verificação:** Teste

---

## RNF-14 — Privacidade das cartas

**Categoria:** Segurança

**Requisito:** O cliente nunca recebe cartas privadas de outro jogador, o valor de cartas cobertas nem o baralho restante.

**Verificação:** Inspeção e teste

---

## RNF-15 — Identificação e canal seguro

**Categoria:** Segurança

**Requisito:** Cada ação é ligada a um jogador identificado por sessão, em canal criptografado (TLS), e jogadas forjadas, repetidas ou fora de turno são rejeitadas mesmo contornando a interface.

**Verificação:** Teste

---

## RNF-16 — Logs e sinais

**Categoria:** Segurança

**Requisito:** Logs técnicos não gravam cartas privadas nem dados pessoais desnecessários, e sinais trafegam apenas para o parceiro.

**Verificação:** Inspeção

---

## RNF-17 — Poucas interações

**Categoria:** Usabilidade

**Requisito:** Jogar uma carta exige no máximo 2 interações, e pedir truco, aceitar ou correr exigem 1 ou 2.

**Verificação:** Teste de usabilidade

---

## RNF-18 — Destaque da vez

**Categoria:** Usabilidade

**Requisito:** O destaque da vez e do pedido pendente é percebido em até 1 s, sem depender só de cor.

**Verificação:** Inspeção

---

## RNF-19 — Idioma e mensagens

**Categoria:** Usabilidade

**Requisito:** Mensagens e rótulos em português do Brasil, claros e sem jargão técnico, em arquivo de textos externalizado.

**Verificação:** Inspeção

---

## RNF-20 — Decisões irreversíveis

**Categoria:** Usabilidade

**Requisito:** Decisões irreversíveis (aceitar, correr, correr da Mão de Onze) mostram as consequências em pontos.

**Verificação:** Inspeção

---

## RNF-21 — Contraste

**Categoria:** Acessibilidade

**Requisito:** Contraste de texto e símbolos de pelo menos 4,5:1 (WCAG 2.1 AA).

**Verificação:** Medição

---

## RNF-22 — Naipes e valores

**Categoria:** Acessibilidade

**Requisito:** Naipes e valores se distinguem por forma e letra, não só por cor.

**Verificação:** Inspeção

---

## RNF-23 — Toque e teclado

**Categoria:** Acessibilidade

**Requisito:** Alvos de toque de pelo menos 44 × 44 px e todas as funções utilizáveis pelo teclado.

**Verificação:** Medição e teste

---

## RNF-24 — Movimento e som

**Categoria:** Acessibilidade

**Requisito:** Respeita a preferência por menos movimento, permite desativar animações, e o som é opcional e nunca a única forma de aviso.

**Verificação:** Teste

---

## RNF-25 — Leitores de tela

**Categoria:** Acessibilidade

**Requisito:** Avisos importantes (vez, pedido de truco, fim de mão) são anunciados a leitores de tela (aria-live).

**Verificação:** Teste

---

## RNF-26 — Navegadores e telas

**Categoria:** Compatibilidade

**Requisito:** Funciona nas versões atuais de Chrome, Firefox, Safari e Edge, com layout responsivo a partir de 360 px, em retrato e paisagem.

**Verificação:** Teste

---

## RNF-27 — Separação e configuração

**Categoria:** Manutenibilidade

**Requisito:** O motor de regras é separado da interface e testável sem tela, e as regras que variam por região (empate de 3 rodadas, coberta, valor do Ferro) ficam em configuração central.

**Verificação:** Inspeção

---

## RNF-28 — Cobertura de testes

**Categoria:** Manutenibilidade

**Requisito:** O motor de regras tem cobertura de testes automatizados de pelo menos 90% das linhas.

**Verificação:** Medição

---

## RNF-29 — Rastreabilidade e auditoria

**Categoria:** Manutenibilidade

**Requisito:** O histórico só recebe acréscimos, erros tratados geram registro técnico com o identificador da partida, e cada requisito é rastreável a um caso de uso, a regras e a um cenário de aceitação.

**Verificação:** Inspeção

---

## RNF-30 — Partidas simultâneas

**Categoria:** Escalabilidade

**Requisito:** Partidas simultâneas são independentes entre si e o sistema suporta pelo menos 100 delas sem violar RNF-01.

**Verificação:** Teste de carga

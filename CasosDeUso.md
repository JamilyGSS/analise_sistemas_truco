## Integrantes
Giovana Ferreira Waterkemper- ra143844  
Jamily Gonçalves de Sales Souza - ra143048

## Truco Paulista de Duas Duplas - Casos de Uso
### UC-001 — Iniciar partida
**Objetivo:** Permitir que os jogadores iniciem uma nova partida de Truco Paulista entre duas duplas.
  
**Ator principal:** Jogador. Atores secundários: Sistema.
  
**Pré-condições:**  
- O sistema deve estar disponível.  
- Os quatro jogadores devem estar definidos para a partida.
  
**Pós-condições:**
- A partida é criada e fica pronta para ser iniciada.  
- O estado inicial da partida é registrado.
  
**Gatilho:** Um jogador solicita o início de uma nova partida.
  
**Fluxo principal:**  
- Jogador solicita iniciar uma partida.
- Sistema verifica se existem quatro jogadores disponíveis.
- Sistema verifica se as duplas foram definidas.
- Sistema cria a partida.
- Sistema inicializa o placar das duas duplas em zero.
- Sistema inicia a preparação para a primeira mão.
  
**Fluxos alternativos:**  
**A1. (Jogadores insuficientes)** → Sistema informa que são necessários quatro jogadores e aguarda a definição dos participantes.  
**A2. (Duplas não definidas)** → Sistema solicita que as duplas sejam formadas antes de continuar.
  
**Exceções:**  
**E1. (Falha ao criar partida)** → Sistema informa que não foi possível iniciar a partida.
  
### UC-002 — Formar duplas

**Objetivo:** Permitir a definição dos quatro jogadores em duas duplas adversárias.

**Ator principal:** Jogador. Atores secundários: Sistema.

**Pré-condições:**

- O sistema deve estar disponível.
- Os quatro participantes devem estar identificados.

**Pós-condições:**

- As duas duplas ficam registradas para a partida.
- Cada jogador fica associado à sua respectiva dupla.

**Gatilho:** Um jogador solicita a formação das duplas.

**Fluxo principal:**

- Jogador acessa a configuração das duplas.
- Sistema apresenta os quatro participantes disponíveis.
- Jogador seleciona os integrantes da primeira dupla.
- Jogador seleciona os integrantes da segunda dupla.
- Sistema verifica se cada dupla possui dois jogadores distintos.
- Sistema registra as duplas.
- Sistema apresenta a composição final das equipes.

**Fluxos alternativos:**  
**A1. (Jogador repetido)** → Sistema informa que um mesmo jogador não pode pertencer às duas duplas e solicita uma nova seleção.\
**A2. (Dupla incompleta)** → Sistema solicita que todos os integrantes sejam definidos.

**Exceções:**  
**E1. (Falha ao registrar duplas)** → Sistema informa que não foi possível salvar a configuração.

### UC-003 — Distribuir cartas

**Objetivo:** Distribuir três cartas para cada jogador no início de cada mão.

**Ator principal:** Sistema. Atores secundários: Jogador.

**Pré-condições:**

- Uma partida deve estar em andamento.
- Os quatro jogadores devem estar definidos.
- Deve ser possível preparar um novo baralho para a mão.

**Pós-condições:**

- Cada jogador recebe três cartas.
- As cartas são mantidas em sigilo para os demais jogadores.
- A mão fica preparada para a revelação do Vira.

**Gatilho:** O sistema inicia uma nova mão.

**Fluxo principal:**

- Sistema prepara o baralho conforme as regras do Truco Paulista.
- Sistema embaralha as cartas.
- Sistema distribui três cartas para cada um dos quatro jogadores.
- Sistema registra as cartas recebidas por cada jogador.
- Sistema mantém as cartas privadas de cada participante.
- Sistema disponibiliza as cartas para consulta pelos respectivos jogadores.

**Fluxos alternativos:**  
**A1. (Nova mão após encerramento da anterior)** → Sistema inicia uma nova distribuição, preservando o placar acumulado.

**Exceções:**  
**E1. (Falha na distribuição)** → Sistema informa que não foi possível distribuir as cartas e impede o início das jogadas até que a distribuição seja corrigida.

### UC-004 — Visualizar cartas

**Objetivo:** Permitir que o jogador visualize suas próprias cartas durante a mão.

**Ator principal:** Jogador. Atores secundários: Sistema.

**Pré-condições:**

- O jogador deve estar participando de uma partida.
- As cartas devem ter sido distribuídas.

**Pós-condições:**

- O jogador consegue consultar suas cartas.
- As cartas dos demais participantes permanecem ocultas, salvo nas situações previstas pelas regras.

**Gatilho:** O jogador acessa sua mão de cartas.

**Fluxo principal:**

- Jogador solicita a visualização das cartas.
- Sistema identifica o jogador.
- Sistema verifica quais cartas pertencem ao participante.
- Sistema apresenta as cartas disponíveis para consulta.

**Fluxos alternativos:**  
**A1. (Mão de Onze)** → Quando aplicável, o sistema permite visualizar as cartas do parceiro conforme o UC-017.  
**A2. (Carta já jogada)** → Sistema apresenta a carta conforme o estado da rodada, sem permitir que ela seja utilizada novamente.

**Exceções:**  
**E1. (Jogador não identificado)** → Sistema impede a consulta das cartas privadas e solicita a identificação do participante.

### UC-005 — Jogar carta

**Objetivo:** Permitir que o jogador escolha e jogue uma carta durante uma rodada da mão.

**Ator principal:** Jogador. Atores secundários: Sistema.

**Pré-condições:**

- A partida deve estar em andamento.
- O jogador deve possuir cartas disponíveis.
- Deve ser a vez do jogador, conforme a ordem de jogo.

**Pós-condições:**

- A carta selecionada é registrada na rodada.
- A carta deixa de estar disponível na mão do jogador.
- O sistema atualiza o estado da rodada.

**Gatilho:** Chega a vez do jogador jogar uma carta.

**Fluxo principal:**

- Sistema indica que é a vez do jogador.
- Jogador seleciona uma carta de sua mão.
- Sistema verifica se a jogada é válida.
- Sistema registra a carta jogada.
- Sistema apresenta a carta aos participantes, respeitando as regras de visibilidade.
- Sistema verifica se todos os jogadores da rodada já jogaram.
- Se a rodada estiver concluída, sistema executa o UC-010.
- Caso contrário, sistema passa a vez ao próximo jogador.

**Fluxos alternativos:**  
**A1. (Carta coberta)** → Jogador escolhe jogar uma carta fechada, quando permitido, conforme o UC-016.  
**A2. (Mão de Ferro)** → Sistema exige que as cartas sejam jogadas no escuro, conforme o UC-018.  
**A3. (Jogada inválida)** → Sistema informa que a carta não pode ser jogada e permite uma nova seleção.

**Exceções:**  
**E1. (Falha ao registrar jogada)** → Sistema informa que a jogada não foi registrada e mantém o estado anterior da rodada.

### UC-006 — Pedir truco

**Objetivo:** Permitir que um jogador solicite o aumento do valor da mão durante a partida.

**Ator principal:** Jogador. Atores secundários: Sistema e jogadores adversários.

**Pré-condições:**

- A partida deve estar em andamento.
- A mão deve permitir o pedido de truco.
- Não pode existir uma decisão de aposta pendente.

**Pós-condições:**

- O pedido de truco fica registrado.
- A partida aguarda a resposta dos adversários.
- O valor da mão é atualizado conforme a decisão tomada.

**Gatilho:** Um jogador solicita truco durante uma mão.

**Fluxo principal:**

- Jogador solicita truco.
- Sistema verifica se o pedido é permitido.
- Sistema registra o pedido.
- Sistema informa os adversários sobre o aumento proposto.
- Sistema aguarda a resposta dos adversários.

**Fluxos alternativos:**  
**A1. (Pedido não permitido)** → Sistema informa que o truco não pode ser solicitado naquele momento.  
**A2. (Aumento de aposta)** → Caso a mão já esteja valendo mais pontos, o sistema permite solicitar o próximo aumento, conforme o UC-009.

**Exceções:**  
**E1. (Falha ao registrar pedido)** → Sistema informa que não foi possível registrar o pedido e mantém o valor anterior da mão.

### UC-007 — Aceitar truco

**Objetivo:** Permitir que a dupla adversária aceite o aumento do valor da mão solicitado por um jogador.

**Ator principal:** Jogador adversário. Atores secundários: Sistema.

**Pré-condições:**

- Deve existir um pedido de truco pendente.
- O jogador deve estar autorizado a responder ao pedido.

**Pós-condições:**

- O pedido é aceito.
- O valor da mão passa a ser o valor correspondente à aposta aceita.
- A partida continua normalmente.

**Gatilho:** Um jogador seleciona a opção de aceitar o truco.

**Fluxo principal:**

- Sistema apresenta o pedido de truco pendente.
- Jogador seleciona a opção de aceitar.
- Sistema registra a decisão.
- Sistema atualiza o valor da mão para três pontos ou para o valor correspondente ao aumento solicitado.
- Sistema retoma a partida.

**Fluxos alternativos:**  
**A1. (Aceitação de aumento posterior)** → Sistema aplica o valor correspondente à nova aposta aceita.

**Exceções:**  
**E1. (Pedido inexistente ou expirado)** → Sistema informa que não há pedido válido para aceitar.

### UC-008 — Correr do truco

**Objetivo:** Permitir que uma dupla recuse o aumento do valor da mão e desista dela.

**Ator principal:** Jogador adversário. Atores secundários: Sistema.

**Pré-condições:**

- Deve existir um pedido de truco pendente.
- A mão deve permitir a desistência.

**Pós-condições:**

- A mão é encerrada.
- A dupla que pediu o aumento recebe os pontos previstos pelas regras.
- O placar é atualizado.

**Gatilho:** Um jogador escolhe correr do truco.

**Fluxo principal:**

- Sistema apresenta o pedido de truco pendente.
- Jogador seleciona a opção de correr.
- Sistema registra a desistência.
- Sistema encerra a mão.
- Sistema atribui à dupla vencedora a pontuação correspondente à situação.
- Sistema atualiza o placar conforme o UC-012.
- Sistema verifica se a partida deve ser encerrada.

**Fluxos alternativos:**  
**A1. (Desistência após aumento)** → Sistema atribui os pontos correspondentes ao valor vigente antes do aumento recusado, conforme as regras do jogo.

**Exceções:**  
**E1. (Resposta inválida)** → Sistema informa que não existe pedido pendente ou que a resposta não é permitida.

### UC-009 — Aumentar aposta

**Objetivo:** Permitir que um jogador aumente o valor da mão de acordo com a sequência de apostas do Truco Paulista.

**Ator principal:** Jogador. Atores secundários: Sistema e jogadores adversários.

**Pré-condições:**

- A mão deve estar em andamento.
- Deve existir uma aposta que permita um novo aumento.
- O pedido deve respeitar a sequência de valores permitidos.

**Pós-condições:**

- O novo pedido de aumento fica registrado.
- Os adversários são notificados.
- A partida aguarda a resposta ao aumento.

**Gatilho:** Um jogador solicita aumentar o valor da mão.

**Fluxo principal:**

- Jogador solicita o próximo aumento.
- Sistema verifica o valor atual da mão.
- Sistema identifica o próximo valor permitido: seis, nove ou doze pontos.
- Sistema registra o pedido.
- Sistema informa os adversários.
- Sistema aguarda a aceitação, o próximo aumento permitido ou a desistência.

**Fluxos alternativos:**  
**A1. (Aumento aceito)** → Sistema atualiza o valor da mão e retoma a partida.  
**A2. (Aumento recusado)** → Sistema encerra a mão e atribui os pontos previstos pelas regras.  
**A3. (Valor máximo atingido)** → Sistema impede novos aumentos quando a mão já estiver valendo doze pontos.

**Exceções:**  
**E1. (Sequência inválida)** → Sistema rejeita o pedido e informa qual aumento é permitido.

### UC-010 — Determinar vencedor da rodada

**Objetivo:** Identificar qual jogador ou dupla venceu a rodada, comparando as cartas jogadas conforme a hierarquia do Truco Paulista.

**Ator principal:** Sistema. Atores secundários: Jogadores.

**Pré-condições:**

- A rodada deve estar em andamento.
- Todos os jogadores devem ter realizado suas jogadas, ou a rodada deve ter sido concluída conforme as regras.

**Pós-condições:**

- O resultado da rodada fica registrado.
- A partida conhece a dupla vencedora da rodada ou a ocorrência de empate.

**Gatilho:** A rodada é concluída.

**Fluxo principal:**

- Sistema recupera as cartas jogadas na rodada.
- Sistema verifica a hierarquia das cartas, considerando o Vira e as manilhas.
- Sistema compara as cartas válidas.
- Sistema identifica a carta vencedora.
- Sistema determina a dupla vencedora da rodada ou registra o empate.
- Sistema registra o resultado.
- Sistema verifica se a mão já pode ser decidida.

**Fluxos alternativos:**  
**A1. (Empate entre as duplas)** → Sistema aplica as regras de empate do Truco Paulista para determinar o resultado da mão.  
**A2. (Cartas cobertas)** → Sistema considera apenas as informações permitidas pelas regras, sem revelar indevidamente o valor das cartas fechadas.

**Exceções:**  
**E1. (Estado inconsistente da rodada)** → Sistema informa a inconsistência e impede a definição incorreta do vencedor.

### UC-011 — Determinar vencedor da mão

**Objetivo:** Definir a dupla vencedora da mão considerando os resultados das rodadas.

**Ator principal:** Sistema. Atores secundários: Jogadores.

**Pré-condições:**

- A mão deve estar em andamento.
- Pelo menos uma rodada deve ter sido concluída.

**Pós-condições:**

- A dupla vencedora da mão fica registrada.
- O valor de pontos conquistados é determinado.
- A partida fica pronta para atualizar o placar.

**Gatilho:** Uma rodada termina e o sistema verifica se já existe uma dupla vencedora da mão.

**Fluxo principal:**

- Sistema consulta os resultados das rodadas concluídas.
- Sistema aplica as regras de vitória e empate do Truco Paulista.
- Sistema verifica se uma dupla já garantiu a vitória da mão.
- Sistema identifica a dupla vencedora.
- Sistema determina o valor da mão conforme os pedidos de truco aceitos.
- Sistema registra o resultado.
- Sistema solicita a atualização da pontuação conforme o UC-012.

**Fluxos alternativos:**  
**A1. (Mão ainda não decidida)** → Sistema inicia a próxima rodada, caso ainda existam rodadas necessárias.  
**A2. (Mão de Onze)** → Sistema aplica as condições especiais do UC-017.  
**A3. (Mão de Ferro)** → Sistema aplica as condições especiais do UC-018.  
**A4. (Desistência por truco)** → Sistema considera a desistência e a pontuação definida no UC-008.

**Exceções:**  
**E1. (Resultado inconclusivo)** → Sistema mantém a mão pendente até que seja possível determinar o resultado conforme as regras.

### UC-012 — Atualizar pontuação

**Objetivo:** Registrar os pontos conquistados por cada dupla ao final de uma mão.

**Ator principal:** Sistema. Atores secundários: Jogadores.

**Pré-condições:**

- A mão deve ter sido concluída.
- O resultado da mão deve estar definido.

**Pós-condições:**

- O placar é atualizado.
- A pontuação de ambas as duplas fica registrada.
- O sistema verifica se alguma dupla atingiu a pontuação necessária para vencer a partida.

**Gatilho:** O sistema identifica o vencedor de uma mão.

**Fluxo principal:**

- Sistema identifica a dupla vencedora.
- Sistema consulta o valor da mão.
- Sistema adiciona os pontos correspondentes ao placar da dupla vencedora.
- Sistema mantém inalterada a pontuação da dupla perdedora.
- Sistema apresenta o placar atualizado.
- Sistema verifica se alguma dupla atingiu doze pontos.
- Se uma dupla atingiu a pontuação necessária, sistema executa o UC-014.
- Caso contrário, sistema prepara a próxima mão.

**Fluxos alternativos:**  
**A1. (Partida ainda não concluída)** → Sistema mantém o placar e inicia uma nova mão.

**Exceções:**  
**E1. (Falha na atualização)** → Sistema informa que não foi possível atualizar o placar e preserva o último resultado confirmado.

### UC-013 — Consultar placar

**Objetivo:** Permitir que os jogadores consultem a pontuação atual das duas duplas.

**Ator principal:** Jogador. Atores secundários: Sistema.

**Pré-condições:**

- Deve existir uma partida criada.

**Pós-condições:**

- O placar atual fica disponível para consulta.
- Nenhuma pontuação é alterada pela consulta.

**Gatilho:** Um jogador solicita a visualização do placar.

**Fluxo principal:**

- Jogador solicita consultar o placar.
- Sistema recupera a pontuação registrada.
- Sistema identifica as duas duplas.
- Sistema apresenta os pontos de cada dupla.
- Sistema disponibiliza o placar para consulta durante a partida.

**Fluxos alternativos:**  
**A1. (Placar ainda zerado)** → Sistema apresenta ambas as duplas com zero pontos.

**Exceções:**  
**E1. (Falha ao recuperar placar)** → Sistema informa que não foi possível consultar a pontuação.

### UC-014 — Encerrar partida

**Objetivo:** Finalizar a partida quando uma das duplas atingir a pontuação necessária para vencer.

**Ator principal:** Sistema. Atores secundários: Jogadores.

**Pré-condições:**

- A partida deve estar em andamento.
- Uma dupla deve ter atingido doze pontos, conforme as regras adotadas.

**Pós-condições:**

- A partida fica encerrada.
- A dupla vencedora é registrada.
- O resultado final fica disponível para consulta.

**Gatilho:** O placar é atualizado e uma dupla atinge doze pontos.

**Fluxo principal:**

- Sistema verifica o placar atualizado.
- Sistema identifica a dupla que atingiu a pontuação necessária.
- Sistema registra o encerramento da partida.
- Sistema impede novas jogadas na partida encerrada.
- Sistema apresenta a dupla vencedora e o placar final.

**Fluxos alternativos:**  
**A1. (Nenhuma dupla atingiu a pontuação necessária)** → Sistema mantém a partida em andamento.

**Exceções:**  
**E1. (Falha ao registrar encerramento)** → Sistema informa que não foi possível concluir o registro e mantém o estado consistente da partida.

### UC-015 — Revelar Vira e definir manilhas

**Objetivo:** Revelar a carta do Vira e determinar automaticamente as manilhas da mão.

**Ator principal:** Sistema. Atores secundários: Jogadores.

**Pré-condições:**

- As cartas devem ter sido distribuídas.
- A mão deve estar preparada para começar.

**Pós-condições:**

- A carta do Vira fica visível aos jogadores.
- As manilhas da mão ficam definidas e registradas.

**Gatilho:** O sistema conclui a distribuição das cartas.

**Fluxo principal:**

- Sistema identifica a carta reservada para o Vira.
- Sistema revela a carta.
- Sistema determina a carta seguinte na sequência de valores.
- Sistema define as quatro cartas daquele valor como manilhas.
- Sistema aplica a ordem de força entre as manilhas conforme a regra do Truco Paulista.
- Sistema disponibiliza as informações necessárias para avaliar as jogadas.

**Fluxos alternativos:**  
**A1. (Manilhas em mão especial)** → Sistema aplica as regras específicas da mão, preservando a hierarquia prevista.

**Exceções:**  
**E1. (Vira inválido ou ausente)** → Sistema impede o início das jogadas até que a carta seja definida corretamente.

### UC-016 — Jogar carta coberta (fechada)

**Objetivo:** Permitir que o jogador jogue uma carta virada para baixo quando essa jogada for permitida pelas regras da partida.

**Ator principal:** Jogador. Atores secundários: Sistema.

**Pré-condições:**

- A partida deve estar em andamento.
- Deve ser a vez do jogador.
- A regra da partida deve permitir jogar carta fechada naquela rodada.
- O jogador deve possuir uma carta disponível.

**Pós-condições:**

- A carta é registrada como fechada.
- O valor da carta permanece oculto aos demais participantes.
- A carta não pode ser jogada novamente.

**Gatilho:** O jogador escolhe a opção de jogar uma carta coberta.

**Fluxo principal:**

- Sistema verifica se a jogada fechada é permitida.
- Jogador seleciona uma carta.
- Jogador escolhe jogá-la coberta.
- Sistema registra a carta sem revelar seu valor aos demais participantes.
- Sistema marca a carta como utilizada.
- Sistema prossegue com a ordem de jogo.

**Fluxos alternativos:**  
**A1. (Carta fechada não permitida)** → Sistema informa que a opção não está disponível naquela rodada.  
**A2. (Mão de Ferro)** → Sistema aplica obrigatoriamente o modo de jogo no escuro, conforme o UC-018.

**Exceções:**  
**E1. (Falha ao ocultar a carta)** → Sistema cancela a jogada e preserva a confidencialidade das cartas.

### UC-017 — Gerenciar Mão de Onze

**Objetivo:** Aplicar as regras especiais quando uma das duplas atinge onze pontos.

**Ator principal:** Jogador integrante da dupla com onze pontos. Atores secundários: Parceiro e sistema.

**Pré-condições:**

- A partida deve estar em andamento.
- Uma das duplas deve possuir onze pontos.
- A mão anterior deve ter sido encerrada.

**Pós-condições:**

- A dupla decide se aceita jogar a mão especial.
- Caso aceite, a mão é disputada valendo três pontos.
- Caso corra, a dupla adversária recebe um ponto, conforme a regra adotada.

**Gatilho:** Uma dupla atinge onze pontos.

**Fluxo principal:**

- Sistema identifica que uma dupla atingiu onze pontos.
- Sistema informa os integrantes da dupla sobre a situação especial.
- Sistema permite que os parceiros consultem as cartas um do outro.
- Os jogadores analisam suas cartas.
- A dupla decide se deseja jogar ou correr.
- Sistema registra a decisão.
- Se a dupla aceitar, sistema inicia a mão valendo três pontos.
- Se a dupla correr, sistema concede um ponto à dupla adversária.
- Sistema atualiza o placar e verifica as condições para encerrar a partida.

**Fluxos alternativos:**  
**A1. (Dupla decide correr)** → Sistema encerra a mão especial sem jogadas e concede um ponto à dupla adversária.  
**A2. (Dupla decide jogar)** → Sistema inicia a mão especial, mantendo o valor de três pontos.

**Exceções:**  
**E1. (Decisão não registrada)** → Sistema solicita que a dupla confirme sua decisão antes de prosseguir.

### UC-018 — Gerenciar Mão de Ferro

**Objetivo:** Aplicar a regra especial da Mão de Ferro quando as duas duplas atingem onze pontos.

**Ator principal:** Sistema. Atores secundários: Jogadores.

**Pré-condições:**

- A partida deve estar em andamento.
- Ambas as duplas devem possuir onze pontos.
- A mão anterior deve ter sido encerrada.

**Pós-condições:**

- A mão especial é iniciada no escuro.
- Os jogadores não podem solicitar truco durante a mão.
- O resultado determina a dupla vencedora da partida, conforme as regras adotadas.

**Gatilho:** O placar chega a onze pontos para cada dupla.

**Fluxo principal:**

- Sistema identifica o empate em onze pontos.
- Sistema informa aos jogadores que a Mão de Ferro será iniciada.
- Sistema prepara e distribui as cartas conforme as regras adotadas.
- Sistema mantém as cartas ocultas conforme o modo de jogo.
- Sistema desabilita os pedidos de truco e os aumentos de aposta.
- Jogadores realizam suas jogadas.
- Sistema determina o resultado da mão.
- Sistema atualiza a pontuação e identifica a dupla vencedora da partida.

**Fluxos alternativos:**  
**A1. (Tentativa de pedir truco)** → Sistema rejeita a solicitação e informa que o pedido não é permitido na Mão de Ferro.

**Exceções:**  
**E1. (Falha na preparação da mão)** → Sistema impede o início das jogadas e informa que não foi possível preparar a Mão de Ferro.

### UC-019 — Alternar distribuidor e ordem

**Objetivo:** Controlar a rotação do distribuidor e a ordem de participação dos jogadores entre as mãos.

**Ator principal:** Sistema. Atores secundários: Jogadores.

**Pré-condições:**

- A partida deve estar em andamento.
- A mão anterior deve ter sido concluída ou a partida deve estar iniciando.

**Pós-condições:**

- O distribuidor da próxima mão fica definido.
- A ordem de jogo é atualizada conforme as regras da partida.

**Gatilho:** Uma nova mão será iniciada.

**Fluxo principal:**

- Sistema identifica o distribuidor atual.
- Sistema determina o próximo distribuidor na sequência dos jogadores.
- Sistema define a ordem de participação para a nova mão.
- Sistema registra a nova configuração.
- Sistema informa aos jogadores quem inicia a distribuição e a ordem de jogo.

**Fluxos alternativos:**  
**A1. (Primeira mão da partida)** → Sistema define o distribuidor inicial conforme o critério adotado para a partida.  
**A2. (Jogador desconectado)** → Sistema preserva a posição do jogador e aplica o procedimento de reconexão previsto no UC-021.

**Exceções:**  
**E1. (Ordem inválida)** → Sistema impede a distribuição até que a ordem de jogo seja corrigida.

### UC-020 — Enviar sinais ao parceiro

**Objetivo:** Permitir que um jogador envie sinais visuais predefinidos ao parceiro durante a partida, quando essa funcionalidade estiver habilitada.

**Ator principal:** Jogador. Atores secundários: Parceiro e sistema.

**Pré-condições:**

- A partida deve estar em andamento.
- O jogador deve estar associado a uma dupla.
- O sistema deve disponibilizar os sinais visuais.

**Pós-condições:**

- O sinal selecionado é enviado ao parceiro.
- A partida continua sem alteração automática das cartas ou da pontuação.

**Gatilho:** O jogador seleciona um sinal visual.

**Fluxo principal:**

- Jogador acessa a opção de sinais.
- Sistema apresenta os sinais disponíveis.
- Jogador seleciona um sinal.
- Sistema verifica se o sinal é permitido.
- Sistema envia o sinal ao parceiro.
- Sistema mantém inalterado o estado das cartas e do placar.

**Fluxos alternativos:**  
**A1. (Sinal indisponível)** → Sistema informa que o sinal selecionado não está disponível.  
**A2. (Parceiro desconectado)** → Sistema informa que o sinal não pôde ser entregue naquele momento.

**Exceções:**  
**E1. (Falha no envio)** → Sistema informa que não foi possível transmitir o sinal.

### UC-021 — Reconectar jogador

**Objetivo:** Permitir que um jogador que perdeu a conexão retorne à partida em andamento, preservando o estado do jogo.

**Ator principal:** Jogador desconectado. Atores secundários: Sistema.

**Pré-condições:**

- A partida deve continuar ativa.
- O jogador deve possuir uma identificação válida.
- O estado da partida deve estar registrado pelo sistema.

**Pós-condições:**

- O jogador recupera o acesso à partida.
- As cartas privadas e as informações permitidas são restauradas para o participante correto.
- A partida continua com o estado previamente registrado.

**Gatilho:** Um jogador solicita retornar à partida após uma desconexão.

**Fluxo principal:**

- Jogador solicita reconexão.
- Sistema identifica o participante.
- Sistema verifica se a partida ainda está ativa.
- Sistema recupera o estado atual da partida.
- Sistema restaura as informações autorizadas para o jogador.
- Sistema permite que o jogador retome sua participação, respeitando a ordem de jogo.
- Sistema confirma a reconexão.

**Fluxos alternativos:**  
**A1. (Jogador reconecta fora de sua vez)** → Sistema permite acompanhar a partida e aguardar sua próxima vez.  
**A2. (Jogador reconecta durante uma rodada)** → Sistema restaura o estado da rodada sem repetir jogadas já registradas.

**Exceções:**  
**E1. (Partida encerrada)** → Sistema informa que a partida não está mais ativa.  
**E2. (Identificação inválida)** → Sistema impede o acesso à partida e solicita uma identificação válida.  
**E3. (Estado indisponível)** → Sistema informa que não foi possível recuperar a partida.

### UC-022 — Consultar regras da jogada

**Objetivo:** Permitir que os jogadores consultem, durante a partida, uma explicação breve das regras aplicáveis à situação atual do jogo, sem precisar sair da mesa.

**Ator principal:** Jogador. Atores secundários: Sistema.

**Pré-condições:**

- Deve existir uma partida em andamento.
- O sistema deve conhecer o estado atual da partida, incluindo a rodada, o valor da mão, o Vira e as condições especiais em vigor.

**Pós-condições:**

- O jogador visualiza as informações sobre as regras pertinentes à situação atual.
- A consulta não altera as cartas, a rodada, o placar ou qualquer outro estado da partida.

**Gatilho:** O jogador seleciona a opção de consultar as regras durante a partida.

**Fluxo principal:**

- Jogador seleciona a área ou o ícone de ajuda/regras na tela da partida.
- Sistema identifica o estado atual do jogo.
- Sistema verifica quais regras são relevantes para a situação, considerando, quando aplicável, a rodada atual, o valor da mão, o Vira, as manilhas e condições especiais, como Mão de Onze ou Mão de Ferro.
- Sistema apresenta um resumo curto e contextualizado das regras aplicáveis.
- Sistema disponibiliza, caso o jogador deseje, acesso à explicação mais detalhada das regras.
- Jogador fecha a área de consulta e retorna à partida sem perder o estado atual do jogo.

**Fluxos alternativos:**  
**A1. (Nenhuma regra especial ativa)** → Sistema apresenta um resumo das regras gerais relevantes para a jogada atual.  
**A2. (Regra especial ativa)** → Sistema destaca a condição especial em vigor e explica brevemente o que muda naquela mão.  
**A3. (Jogador solicita explicação completa)** → Sistema apresenta a descrição detalhada da regra selecionada.

**Exceções:**  
**E1. (Estado da partida indisponível)** → Sistema informa que não foi possível identificar as regras aplicáveis naquele momento e disponibiliza o acesso às regras gerais.

### UC-023 — Consultar histórico de ações da partida

**Objetivo:** Permitir que os jogadores consultem um registro cronológico das principais ações realizadas durante a partida, como cartas jogadas, pedidos de truco, respostas às apostas, resultados das rodadas e atualização do placar.

**Ator principal:** Jogador. Ator secundário: Sistema.

**Pré-condições:**

- Deve existir uma partida criada.
- O sistema deve registrar os eventos relevantes ocorridos durante a partida.

**Pós-condições:**

- O histórico de ações fica disponível para consulta.
- A consulta não altera o andamento da partida nem permite repetir ações já realizadas.

**Gatilho:** O jogador seleciona a opção de histórico durante a partida.

**Fluxo principal:**

- Jogador seleciona a opção de visualizar o histórico.
- Sistema recupera os eventos registrados na partida.
- Sistema organiza os eventos em ordem cronológica, identificando, quando pertinente, o jogador responsável, a equipe, a rodada e a mão.
- Sistema apresenta os acontecimentos mais recentes e permite consultar os anteriores.
- Jogador consulta os registros desejados.
- Jogador fecha o histórico e retorna à mesa, mantendo o estado atual da partida.

**Fluxos alternativos:**  
**A1. (Histórico vazio)** → Sistema informa que ainda não há ações registradas além do início da partida.  
**A2. (Partida em andamento)** → Sistema atualiza a apresentação do histórico conforme novas ações são registradas.  
**A3. (Partida encerrada)** → Sistema permite consultar o histórico completo da partida.

**Exceções:**  
**E1. (Falha ao recuperar histórico)** → Sistema informa que não foi possível carregar os registros e permite tentar novamente.

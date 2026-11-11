# ITTS ACS – Guia do Usuário

O objetivo deste documento é apresentar o módulo **ITTS ACS** e seus componentes.

---

## 1. Introdução

### Introdução

### O que é o ITTS ACS

ACS (*Asset Control & Tracking System*) é o módulo ITTS para controle de acesso e patrimônio em portarias.

### Funcionalidades

As funcionalidades principais do ITTS ACS são:

- Registro de locação de ativos;
- Registro de eventos de acesso;
- Monitoramento em tempo real.

### Requisitos

Os seguintes requisitos são necessários para operação do módulo ACS:

- 1 leitor RFID Identix por ponto de acesso;
- 3 antenas RFID por leitor RFID;
- 1 tablet ou computador com Windows 10 ou superior;
- Porta TCP 1883 liberada no firewall local.

### Leitor RFID

Responsável pela captura das leituras das etiquetas RFID de ativos e pessoas e envio à plataforma ITTS, bem como pela recepção de comandos para operação do GPIO.

### Antena RFID

Responsável por transmitir os dados das etiquetas para o leitor RFID.

#### Portaria com esteira

- Para leitores Identix EZR2500, as antenas 1 e 2 são utilizadas para identificação dos ativos, e as antenas 3 ou 4 para identificação de pessoas.
- Para os demais leitores, as antenas 3 e 4 são utilizadas para identificação dos ativos, e as antenas 1 ou 2 para identificação de pessoas.

As antenas devem ser posicionadas da seguinte forma:

Identix EZR2500

- Antena 1: entrada do ativo;
- Antena 2: saída do ativo;
- Antena 3 ou 4: identificação da pessoa portadora do ativo.

Demais leitores

- Antena 3: entrada do ativo;
- Antena 4: saída do ativo;
- Antena 1 ou 2: identificação da pessoa portadora do ativo.

### Tablet / Computador

Utilizado para monitoramento em tempo real dos pontos de acesso.

### Identificadores e etiquetas RFID

Pessoas e ativos devem ser identificados com etiquetas RFID.  
Cada etiqueta possui:

- EPC: identificador único;
- TID: identificador gravado pelo fabricante.

### Eventos de Acesso

Um evento de acesso é registrado sempre que um ativo é identificado em um ponto de acesso.

---

## 2. Configuração

### Configurando o Leitor RFID

#### Leitores Homologados

- Identix EZR 2500 – FW 2.5.1.6 ou superior;
- Identix DR Max – FW 0.8.70.0 ou superior;
- Identix DR Mini – FW 0.8.70.0 ou superior.

#### Configuração do leitor

Verifique as seguintes configurações para que o leitor possa operar corretamente:

 - Modo de inicialização do Inventário Automático;
 - Modo de leitura Single Target, Sessão 1;
 - Antenas para identificação do ativo podem ser configuradas com potência de 1600 cdBm;
 - Antena para identificação de pessoas pode ser configurada com potência de 1000 cdBm;
 - Saída de dados contendo:
	- FastId;
	- RSSI;
	- Antena.
 - Saída de dados por MQTT.

### Configurando o dispositivo

Para cada ponto de acesso, um dispositivo RFID deve ser configurado na plataforma ITTS.

Adicionando um dispositivo:

1.	Selecione o menu Meus Dispositivos;
2.	Clique no botão Adicionar;
3.	Para o tipo, selecione a opção Leitor Fixo;
4.	Defina as configurações para seu dispositivo;
5.	Clique no botão Salvar.

### Vincular dispositivo ao módulo ACS

O dispositivo deve ser vinculado ao módulo Controle de Acesso de Ativos, com as antenas corretas habilitadas:

1.	Selecione o menu Meus Dispositivos;
2.	Clique no botão Editar para o dispositivo desejado;
3.	Na parte inferior da tela localize Módulos Vinculados;
4.	Clique no botão Adicionar;
5.	Selecione o módulo Controle de Acesso de Ativos;
6.	Selecione as antenas 1, 2, 3 e 4.
7.	Clique no botão Salvar.

### Configurando ativos e pessoas

#### Itens

Tudo que é monitorado pelo ITTS é registrado como um item. Os itens são organizados em grupos. Deverá ser criado um grupo para representar os ativos e outro para representar as pessoas.

Configurando um grupo:

1.	Selecione o menu Meus Itens;
2.	Selecione a aba Grupos;
3.	Clique no botão Adicionar;
4.	Informe o nome do Grupo;
5.	Informe o Módulo ao qual o grupo será vinculado;
6.	Clique no botão Salvar.

> Importante:
Deverá ser criado um grupo para os Ativos e um grupo para as Pessoas.

Configurando campos:

Opcionalmente poderão ser atribuídos novos campos a cada um dos grupos. 
Obrigatoriamente será necessária a criação de um campo Foto para o grupo de Pessoas para que possa ser apresentada a imagem da pessoa identificada:

1.	Selecione o menu Meus Itens;
2.  Selecione a aba Grupos
3.  Edite o grupo que receberá o novo campo;
4.	Em Campos Customizados, clique no botão Adicionar;
5.	Defina as configurações para o campo;
6.	Clique no botão Salvar.

> Importante:
Um campo foto deverá ser criado para uso da identificação visual de cada pessoa.

Adicionando um Item (Pessoa ou Grupo):

1.	Selecione o menu Meus Itens;
2.	Selecione a Aba Itens;
3.	Clique no botão Adicionar;
4.	Selecione módulo para qual o item será registrado;
5.	Selecione o grupo para qual o item será registrado;
6.	Informe a Identificação;
7.	Defina as demais configurações;
8.	Clique no botão Salvar.

Vinculando Identificadores

Um ou mais identificadores podem ser vinculados tanto para uma pessoa quanto para um ativo. 
O registro de identificadores é feito editando-se o item que representa a pessoa ou ativo. No caso do módulo ACS os ativos e pessoas são identificados com etiquetas RFID contendo um número EPC:

1. Selecione o menu Meus Itens;
2. Selecione a aba Itens;
3. Em Ações, selecione Editar para o item desejado;
4. Em Identificadores, selecione o tipo de identificador, neste caso RFID;
5. Clique no botão **Ler etiqueta RFID**
6. Coloque a etiqueta RFID na área de cobertura do leitor RFID; 
7. Confirme se o valor do EPC e Chave de Segurança (TID) foram preenchidos;
8. Clique no botão Adicionar.

> Importante:
Esta etapa exige um leitor RFID configurado como padrão com WebSocket habilitado na plataforma.

### Preferências de Módulos

#### Preferências

O módulo ACS precisa de algumas configurações antes de poder ser utilizado. É necessário indicar quais os grupos configurados para identificação dos ativos e pessoas. 
Acesse o sistema com uma conta de assinante para configurar as preferências do módulo:

1.	Selecione o menu Configurações;
2.	Selecione a aba Preferências de Módulos;
3.	Ajuste as configurações para o módulo ACS;
4.	Clique no botão Salvar.

### Leitor para Locação e Registro

#### Configurando um leitor para operação de locação e registro de identificadores

Um leitor RFID para apoio a operação de registro de identificadores e de locação para identificação de pessoas ou ativos poderá ser utilizado. Este dispositivo é opcional, mas seu uso tornará o processo muito mais rápido.

1.	Selecione o menu Meus Dispositivos;
2.	No grid, para o dispositivo desejado, seleções o menu Ações e escolha Definir como Padrão.

O dispositivo padrão configurado poderá ser visualizado no canto inferior do lado direito, próximo a versão do sistema.

> Importante:
O leitor RFID configurado para ser utilizado para registrar os identificadores deverá estar habilitado para processamento de dados via WebSocket.

### Ponto de Leitura

#### Configurando um ponto de leitura

Configure um ponto de leitura para cada unidade de controle de acesso. 
Para configurar um ponto de leitura:

1.	Selecione a opção Pontos de Leitura no menu;
2.	Clique no botão Adicionar;
3.	Informe um nome para identificar o ponto de leitura;
4.	Selecione o Módulo correspondente ao controle de acesso;
5.	Selecione a operação que será realizada;
6.	Coloque alguma anotação se desejar;
7.	Habilite o monitoramento;
8.	Clique no botão Salvar.
 
Após criar o ponto de leitura é necessário atribuir o dispositivo e configurar quais antenas serão utilizadas:

1.	Edite o ponto de leitura desejado;
2.	Em Dispositivos, selecione a opção Adicionar;
3.	Selecione o dispositivo que será utilizado;
4.	Selecione o local onde o ponto de leitura está configurado;
5.	Marque as antenas habilitadas para a operação;
6.	Clique no botão Salvar.

---

## 3. Locação

### Locação de Ativos

O ativo só será autorizado se houver uma locação ativa vinculada ao portador.

#### Locando um Ativo

O ativo só será autorizado durante o controle do acesso se estiver com uma locação ativa para o portador identificado. Para locar um ativo:

1.	Acesse o módulo ACS;
2.	Selecione a opção Locação;
3.	Selecione a opção Adicionar;
4.	Selecione a pessoa que está locando;
5.	Selecione o ativo que está sendo locado;
6.	Se desejar, indique a data de retorno previsto;
7.	Se desejar, marque a opção notificação para que a pessoa receba notificações do sistema;
8.	Selecione os dias e horários com acesso autorizado tanto para entrada quanto para saída;
9.	Clique Salvar para registrar a locação.

> Importante:
Somente uma locação ativa é permitida por ativo.

#### Alterando Locação

Os dados de locação poderão ser alterados enquanto a devolução não for registrada. 
Para alterar os dados de uma locação:

1.	Acesse o módulo ACS;
2.	Selecione a opção Locação;
3.	Selecione a opção Editar para a locação do ativo desejado;
4.	Altera os dados desejados e clique em Salvar.

#### Devolvendo um Ativo

Para registrar a devolução de um ativo locado:

1.	Acesse o módulo ACS;
2.	Selecione a opção Locação;
3.	Selecione a opção Editar para a locação do ativo desejado;
4.	Clique no botão Registrar Devolução.

---

## 4. Monitoramento

### Monitoramento de Acessos

O sistema permite o monitoramento de um local por janela. Se for necessário monitorar mais de um local basta abrir cada local em uma janela. 

Para monitorar um local:

1.	Acesse o módulo ACS;
2.	Selecione a opção Monitoramento;
3.	No combo, selecione um ponto de leitura que será monitorado.

O monitoramento poderá ser aberto por um usuário de cada vez.

Duante o monitoramento, as seguintes informações serão apresentadas:

- Ativo - Aguardando leitura do EPC;
- Pessoa - Aguardando leitura do EPC;
- Ativo identificado - O ativo registrado no sistema foi identificado durante o acesso;
- Aguardando a identificação da pessoa. Ativo já foi identificado, aguardando a identificação da pessoa portadora do ativo por 15s;
- Acesso negado - Ativo não locado para o usuário ou regras de acesso não foram atendidas;
- Acesso autorizado - Ativo está locado para a pessoa identificada e as regras de acesso foram atendidas.

### Processo Operacional

1.	Verificar se o sinalizador está no estado disponível para novo acesso (Amarelo Constante);
2.	Passar o ativo pelo scanner/esteira (Transição Antenas A e B);
3.	Aguardar a identificação do ativo (Amarelo Intermitente);
4.	Aproximar o crachá do portador na leitora RFID;
5.	Aguarde a sinalização de liberação (Verde Constante) ou retenção (Vermelho Constante).

### Status do Sinalizador - EZR2500

- Amarelo constante: Disponível para novo acesso
- Vermelho / Verde Constante: Ativo identificado, aguardando identificação do portador (15s)
- Verde constante: Portador identificado e validado, acesso liberado
- Vermelho: Portador não identificado ou não autorizado, acesso bloqueado

Durante o processo de inicialização do ponto de leitura ou durante o teste de GPIO as cores dos sinalizadores serão acionadas em sequência e depois retornará para Amarelo Constante indicando que o ponto de acesso está disponível para um novo acesso.

### Status do Sinalizador - Demais dispositivos

- Amarelo constante: Disponível para novo acesso
- Amarelo intermitente: Ativo identificado, aguardando identificação do portador (15s)
- Verde constante: Portador identificado e validado, acesso liberado
- Vermelho: Portador não identificado ou não autorizado, acesso bloqueado

Durante o processo de inicialização do ponto de leitura ou durante o teste de GPIO as cores dos sinalizadores serão acionadas em sequência e depois retornará para Amarelo Constante indicando que o ponto de acesso está disponível para um novo acesso.

> Importante:
Para conexão da sinaleira, utilize a seguinte configuração:

| Cor do fio | Função | Pino GPIO |
|------------|--------|-----------|
| Vermelho   | VCC (3.3V) | 1 |
| Preto      | GND        | 6 |
| Verde      | Sinal (LED verde) | GPIO 17 |
| Roxo       | Sinal (LED vermelho) | GPIO 27 |

Ordem de conexão dos cabos:

[01][02][03][04][05]
[06][07][08][09][10]

06 - Roxo
07 - Vermelho
08 - Preto
09 - Verde

---

## 5. Histórico

### Histórico de Acessos

Todos os acessos realizados são registrados para posterior consulta. 
Para visualizar o histórico de acessos:

1.	Acesse o módulo ACS;
2.	Selecione a opção Histórico;
3.  Seleciona a aba Histórico de Acesso Ativos.

Os eventos registrados serão apresentados. Utilize os filtros para restringir quais eventos serão apresentados.

Os seguintes dados serão apresentados:
 - Registro – Data e hora do acesso;
 - Local – Local onde o acesso foi realizado;
 - Pessoa – Pessoa identificada;
 - Ativo – Ativo identificado;
 - Usuário – Usuário que realizou o monitoramento, se houver. Nos casos em que não houve um profissional monitorando será registrado como evento autônomo;
 - Autorizado – Status de autorização do acesso.
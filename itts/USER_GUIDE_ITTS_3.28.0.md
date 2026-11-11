# ITTS – Guia do Usuário

O objetivo deste documento é apresentar a aplicação **ITTS** e seus componentes.

---

## 1. Introdução

### 1.1. Introdução ao ITTS

#### 1.1.1. ITTS

Identix ITTS é uma Plataforma IoT Empresarial multi-tenant, altamente escalável e modular, projetada para o gerenciamento centralizado, monitoramento e rastreabilidade de dispositivos e ativos conectados.

A plataforma integra recursos avançados de MDM (Mobile Device Management) com capacidades de IoT e RTLS, permitindo o gerenciamento unificado de endpoints e dispositivos de forma totalmente agnóstica a fabricantes, garantindo flexibilidade, interoperabilidade e ampla compatibilidade tecnológica.

Voltada para cenários de rastreabilidade e telemetria, o ITTS oferece suporte nativo a RAIN RFID, além de tecnologias como Wi-Fi, beacons e sensores IoT, possibilitando a coleta, processamento e armazenamento de dados para localização em tempo real, histórico de eventos e análise operacional.

Sua arquitetura modular permite a adaptação a diferentes contextos de negócio, como rastreamento de ativos, controle logístico, inventário inteligente e gestão de telemetria, funcionando como uma base sólida para soluções IoT corporativas orientadas a dados e escalabilidade.

#### 1.1.2. Principais Características

- Broker MQTT de alto desempenho: Arquitetura robusta e escalável para suportar grandes volumes de dados e eventos em tempo real.
- Consumo de eventos flexível: Possibilidade de processamento em tempo real via barramento de mensagens ou integração via API REST.
- Compatibilidade com diversos dispositivos IoT: Suporte para sensores, leitores RFID, gateways BLE, entre outros.
- Formato de mensagens flexível: Suporte a JSON payloads e capacidade de incorporação de parsers para leitura de formatos proprietários.
- Gerenciamento e coleta de dados inteligente: Monitoramento, controle e análise de dispositivos IoT em tempo real.
- Autenticação de dispositivos versátil: Suporte a autenticação por endereço MAC, senha PSK, certificados, entre outros métodos.
- Segurança e escalabilidade: A plataforma foi desenvolvida com foco em segurança avançada e alta escalabilidade, garantindo confiabilidade em qualquer volume de dispositivos conectados.
- Armazenamento híbrido otimizado:
	- Banco de dados SQL (PostgreSQL) para consultas transacionais e análises de curto prazo.
	- Banco de dados time-series (TimeScaleDB) para armazenamento e análise de dados históricos e em tempo real.
- Principais recursos de MDM implementados:
	- Provisionamento e configuração remota: Permite a configuração automatizada de dispositivos em larga escala.
	- Monitoramento e rastreamento: Visualização do status e localização dos dispositivos em tempo real.
	- Gerenciamento de atualizações: Controle e distribuição remota de atualizações de firmware e software.
	- Controle de acesso e segurança: Implementação de políticas de acesso, autenticação multifator e criptografia.
	- Gestão de conectividade: Monitoramento e otimização do uso de redes Wi-Fi, 4G/5G e BLE.
	- Gerenciamento de aplicativos: Controle de instalação, remoção e atualização de aplicativos nos dispositivos.
	- Relatórios e análise de dados: Dashboards e insights operacionais para tomada de decisão estratégica.

Com a Identix ITTS, as empresas podem obter uma gestão eficiente, segura e escalável de seus dispositivos IoT, garantindo maior controle operacional e melhor tomada de decisão baseada em dados confiáveis.

#### 1.1.3. Principais Funcionalidades

- Cadastro de empresas e unidades de negócios;
- Cadastro de departamentos;
- Cadastro de funções;
- Cadastro de colaboradores;
- Cadastro de dispositivos e grupos de dispositivos;
- Cadastro de Aplicativos;
- Cadastro de usuários e controle de acesso;
- Recebimento de dados de leitura, posicionamento e telemetria;
- Rastreabilidade e Localização em tempo real de itens (RTLS);
- Controle de telemetria.

### 1.2. Autenticação

#### 1.2.1. Conectando-se a interface do usuário

Para conectar-se a interface de administração do ITTS, acesse a url https://itts.synergy.com.br no seu navegador. Você será direcionado para a tela de autenticação:
Informe os dados de acesso do usuário, selecione o botão Entrar para realizar o login no sistema. Se seus dados estiverem corretos a Tela Inicial do sistema será apresentada.

Ao acessar o sistema, a tela inicial será apresentada e nela você terá:

- Barra superior - Na barra superior, a direita você tem acesso ao ícone do menu de navegação e a esquerda ao menu da conta;
- Menu de Navegação - Utilizado para acessar as demais telas e funcionalidades do sistema;
- Painel Principal - Neste painel o administrador tem acesso aos atalhos para módulos e funcionalidades do sistema.

### 1.3. Obtendo Ajuda

Um manual atualizado com todas as informações de operação do sistema encontra-se disponível a partir do menu Ajuda. Para ter acesso ao manual, no menu superior clique sobre o nome do usuário e selecione a opção Ajuda.

### 1.4. Usuários

Para que outros usuários possam fazer utilização do sistema será necessário cadastrá-los. Para configuração dos usuários será necessário realizar login como assinante ou usuário com permissão de acesso ao gerenciamento de usuários.

#### 1.4.1. Criando um usuário

1. No Menu de Navegação, selecione a opção Controle de Acesso. A relação de usuários registrados será apresentada.
2. Selecione o botão Adicionar. Os seguintes dados deverão ser informados:
- Nome – Nome do usuário;
- E-mail – E-mail do usuário;
- Usuário – Login exclusivo do usuário;
- Senha – Senha de acesso do usuário;
- Ativo – Indica se o usuário está ativo no sistema.
3. Informe todo os dados e selecione o botão Salvar para salvar as alterações.

> Importante:
Para que um usuário possa ter acesso ao sistema ele deverá estar vinculado a um grupo com permissões de acesso configuradas.

#### 1.4.2. Atualizando um usuário

1. No Menu de Navegação, selecione a opção Controle de Acesso. A relação de usuários registrados será apresentada. 
2. Selecione o botão Ações para o registro desejado e escolha Editar.
3. Altere os dados desejados e selecione o botão Salvar para atualizar o registro.

#### 1.4.3. Excluindo um usuário

1. No Menu de Navegação, selecione a opção Controle de Acesso. A relação de usuários registrados será apresentada. 
2. Selecione o botão Ações para o registro desejado e escolha Excluir.
3. Confirme a exclusão e o registro será excluído.

### 1.5. Grupos e Permissões

Para gerenciar as permissões do usuário no sistema é necessário a configuração de Grupos e Permissões.

#### 1.5.1. Criando um grupo
1. No Menu de Navegação selecione a opção Controle de Acesso e vá para a aba Grupos e Permissões. A relação de Grupos deverá ser apresentada.
2. Selecione o botão Adicionar, os seguintes dados deverão ser informados:
- Empresa – Empresa a qual o grupo pertence;
- Nome – Nome do grupo;
- Descrição – Descrição do grupo;
- Ativo – Representa se o grupo está ativo no sistema.
3. Selecione o botão Salvar para salvar os dados informados.

#### 1.5.2. Adicionando e removendo permissões
Um grupo precisa ter configurado suas permissões de acesso, ou seja, definir quais telas e módulos do sistema poderão ser acessadas e o que será possível fazer em cada uma delas.
Para adicionar uma nova permissão para o grupo desejado:

1. Selecione o botão de Ações e clique na opção Editar. 
2. Na sessão Permissões do Grupo clique no botão Adicionar ou Editar Permissão.
3. Selecione o Módulo desejado e em seguida selecione qual tela o usuário terá acesso na opção Conteúdo, marque quais ações os usuários do grupo poderão realizar e clique em Salvar Permissões.

### 1.6. Dados Recebidos
A seção de dados recebidos permite o monitoramento da recepção de dados na plataforma. É possível verificar se os dados de leitura estão chegando sem problemas até o ITTS. Para que uma leitura seja recebida, é necessário que os dados de identificação já estejam cadastrados previamente para algum item. Para acessar a tela de dados recebidos, basta clicar no card:
As abas disponíveis para o monitoramento são: 
- Leitura;
- Posição;
- Telemetria;
- Sensor.

Cada aba representa um tópico ao qual a plataforma fará a inscrição para receber mensagens. Para cada tópico, deve-se selecionar um dispositivo para a filtragem. Se algum dado for recebido pelo dispositivo selecionado para o tópico, ele será exibido em tela.

## 2. Itens

## 2.1. Itens

## 2.2 Grupos de Itens

Grupos de itens permitem o agrupamentos de itens. 

Os grupos permitem:
- definir a qual módulo os itens pertencem;
- definir os atributos que os itens terão;
- definir as configurações de serialização.

Um grupo pode ter:
- **Nome** - Nome exlusivo
- **Sku** - Identificador da unidade de estoque
- **Subgrupo** - Grupo pai associado
- **Módulo** - Módulo associado
- **Unidade** Comercial - Unidade de medica comercial
- **Ícone** - Imagem ilustrativa
- **Ativo** - Indicador se o registro está ativo para o sistema
- **Preferências de serialização** - Configurações padrão GS1 para geração de EPCs para novos itens ou máscara customizada

### 2.2.1. Configurando um novo Grupo
1. Selecione Adicionar;
2. Informe os dados do grupo;
3. Informe as configurações de serialização;
4. Selecione a opção Salvar.

### 2.2.2. Editando um Grupo
Para o registro desejado:
1. Selecione a opção Editar no menu Ações;
2. Altere os dados desejados e selecione a opção Salvar.

### 2.2.3. Excluindo um Grupo
Para o registro desejado:
1. Selecione a opção Editar no menu Ações;
2. Selecione a opção excluir e confirme.

> **Importante:** 
Um grupo contendo itens já registrados não poderá ser removido. Quando o grupo não for mais necessário para que ele esteja indisponível para o sistema desative-o.

## 3. – Atividade

### 3.1 Modelos de Atividades

Um modelo de atividade determina as configurações para o processamento de uma atividade. 
Ao selecionar os Modelos de Atividades as seguintes informações são apresentadas no grid:

- Nome – Nome do modelo;
- Módulo – Módulo ao qual o modelo está associado;
- Tipo – Tipo de atividade;
- Descrição – Breve descrição;
- Ativo – Indica se o modelo está ativo no sistema.

#### 3.2 Configurando um novo Modelo

1. Selecione Adicionar;
2. Informe os dados do modelo;
3. Informe as configurações de leitura;
4. Informe as configurações de captura;
5. Informe as configurações de movimentação;
6. Informe as regras de processamento;
7. Selecione a opção Salvar.

#### 3.2.1 Configurações de Leitura

- Modo de leitura – Modo de leitura do leitor;
- Modo de pesquisa – Modo de pesquisa do leitor;
- Sessão – Configura o tempo de persistência de leitura das tags;
- População – População estimada de tags;
- Configurações de Antena:
    - Antena – Indica a antena a ser utilizada;
    - Ativo – Indica se a antena está ativa;
    - TX Power – Configura a potência de leitura em dBm da antena;
    - RX Sensitivity – Configura a sensibilidade de recepção da antena para detectar sinais RFID;
    - Max Sensitivity – Indica se será utilizada o valor máximo para sensibilidade;
    - Max Power – Indica se será utilizada a potência máxima para leitura;
    - Direção – Indica se a antena fará leituras para entrada, saída ou não especificado.

> Importante: A antena deve estar habilitada no dispositivo e na configuração do ponto de leitura.

#### 3.2.2 Configurações de Captura

- Tipo de Captura – Indica se a captura será feita via leitor móvel ou ponto de leitura fixo;
- Ponto de Leitura – Indica qual ponto de leitura será usado (se o tipo de captura for “Ponto de Leitura”);
- Tipo de Inicialização – Indica se a inicialização da atividade que faz uso do modelo será automática, manual ou interativa.

#### 3.2.3 Configurações de Movimentação

- Empresa Origem – Indica a empresa que dá origem à movimentação do item;
- Local Origem – Indica o local (relativo à empresa origem) que dá origem à movimentação do item;
- Empresa Destino – Indica a empresa que será o destino à movimentação do item;
- Local Destino – Indica o local (relativo à empresa destino) que será o destino à movimentação do item.

#### 3.2.4 Regras de Processamento

- Aplicar aos EPCs não esperados – Define se aos EPCs externos ao fluxo também serão atribuídos Status e Etapa (relativo à permissão da etapa do fluxo para leitura de EPCs não esperados);
- Novo Status – Indica o status que será atribuído aos itens;
- Nova Etapa – Indica a etapa que será atribuída aos itens;
- Validação de fluxo obrigatória – Define se o modelo fará obrigatoriamente a validação do fluxo selecionado;
- Vincular ao Fluxo – Indica o fluxo ao qual os itens deverão ser vinculados;
- Etapa – Indica a etapa do fluxo à qual os itens deverão ser pertencentes.

### 3.3 - Editando um Modelo

1. Para o registro desejado, selecione a opção Editar no menu Ações;
2. Altere os dados desejados e selecione a opção Salvar.

### 3.4 Excluindo um Modelo

1. Para o registro desejado, selecione a opção Excluir no menu Ações;
2. Confirme a operação de exclusão.

#### Atividade

Permite a configuração de um processo de controle de itens dentro do sistema. Faz uso de um modelo previamente configurado e define os itens que são esperados para o processamento e o comportamento dos dispositivos.
As atividades e suas configurações estão acessíveis a partir do menu Atividades.

Ao selecionar Atividades um grid com as seguintes informações é apresentado:

- Agendamento – Data e hora estimados para processamento da atividade;
- Tipo – Tipo de atividade;
- Pedido – Número do pedido (se existir);
- Local de Origem – Indica o local (relativo à empresa origem) que dá origem à movimentação do item;
- Local de Destino – Indica o local (relativo à empresa destino) que será o destino à movimentação do item;
- Empresa de Origem – Indica a empresa que dá origem à movimentação do item;
- Empresa de Destino – Indica a empresa que será o destino à movimentação do item;
- Módulo – Módulo para qual a atividade foi registrada;
- Status – Indica a situação da atividade no sistema;
- Pendente – A atividade está pendente e pode sofrer alterações;
- Liberado – A atividade foi liberada para execução e não pode ser alterada;
- Em Execução – A atividade está em execução;
- Cancelada – A atividade teve sua execução cancelada;
- Abortada – A atividade teve sua execução abortada;
- Concluída – A atividade teve sua execução concluída.

#### Configurando uma nova Atividade

1. Selecione Adicionar;
2. Informe os dados da atividade;
3. Altere as configurações de movimentação se desejar;
3. Informe os dados dos itens esperados;
4. Selecione a opção Salvar.

Dados da atividade:
- Módulo – Módulo para qual a atividade será registrada;
- Tipo – Tipo de atividade;
- Modelo – Modelo previamente configurado;
- Agendamento – Data e hora estimados para processamento da atividade;
- Pedido – Número do pedido;
- Prioridade – Indica a prioridade de execução da atividade.
- Configurações de movimentação (herdadas do modelo, mas editáveis caso desejar):
- Empresa Origem – Indica a empresa que dá origem à movimentação do item;
- Local Origem – Indica o local (relativo à empresa origem) que dá origem à movimentação do item;
- Empresa Destino – Indica a empresa que será o destino à movimentação do item;
- Local Destino – Indica o local (relativo à empresa destino) que será o destino à movimentação do item.

Dados dos itens esperados:
- Tipo de lista – Indica se o tipo de lista de itens será EPC, SKU ou EAN;
- Identificador – Campo para preenchimento do identificador (correspondente ao tipo selecionado);
- Quantidade – Quantidade de itens esperados para o identificador informado.

#### Editando uma Atividade

Para o registro desejado, caso seu status seja Pendente:
1. Selecione a opção Editar no menu Ações;
2. Altere os dados desejados e selecione a opção Salvar.

#### Liberando uma Atividade

Para o registro desejado, considerando que sua configuração esteja correta:
1. Selecione a opção Liberar no menu Ações;
2. Confirme a operação de liberação.

#### Visualizando uma Atividade

Para o registro desejado (apenas para status diferente de Pendente), selecione a opção Visualizar no menu Ações.
A tela de visualização apresenta um estado do processamento da atividade, trazendo um resumo sobre os itens e demais informações.

#### Cancelando uma Atividade

Para o registro desejado (apenas para status diferente de Pendente), selecione a opção Cancelar no menu Ações;
Confirme a operação de cancelamento.

#### Processando uma Atividade

Para o registro desejado (apenas para status Liberado), selecione a opção Processar no menu Ações (disponível quando configurado para inicialização manual).
A tela de processamento será apresentada.

#### Processamento - Iniciando uma Atividade

1. Na tela de processamento, selecione Iniciar Atividade;
2. Confirme a operação de inicialização.
A tela de processamento apresenta o andamento da atividade, atualizando os dados à medida que são feitas as leituras dos itens conforme configuração.

#### Processamento - Concluindo uma Atividade

1. Na tela de processamento de uma atividade iniciada, selecione a opção Concluir;
2. Confirme a operação de conclusão.

#### Processamento - Reiniciando uma Atividade

1. Na tela de processamento de uma atividade iniciada, selecione a opção Reiniciar dos controles;
2. Confirme a operação de reinício.

#### Processamento - Cancelando uma Atividade

1. Na tela de processamento de uma atividade iniciada, selecione a opção Cancelar;
2. Confirme a operação de cancelamento.

#### Monitoramento de uma atividade automática ou interativa

Atividades automáticas ou interativas são utilizadas em contextos de leituras contínuas (portais). 
Para monitorar as leituras em uma atividade em progresso, selecione a opção Monitorar no menu Ações (disponível quando configurado para inicialização automática ou interativa).
A tela de monitoramento será apresentada.

#### Monitoramento - Configurar Ordem de Produção

1. Na tela de monitoramento de uma atividade interativa, preencha o campo Ordem e selecione a opção "Aplicar";
2. Confirme a operação.

A partir da aplicação de uma ordem, as leituras seguintes serão registrada com o valor configurado.

#### Monitoramento - Sessão de Contagem

1. Na tela de monitoramento de uma atividade interativa, preencha o campo Quantidade e selecione a opção "Aplicar";
2. Confirme a operação.

A partir da aplicação de uma quantidade, uma sessão de contagem é iniciada. Será feita uma relação entre quantidade esperada e itens lidos.
Quando uma sessão de contagem está ativa, não são registradas movimentações para os itens até que a sessão seja concluída.

#### Monitoramento - Reiniciando uma Sessão de Contagem

1. Na tela de monitoramento de uma atividade interativa, com uma sessão de contagem iniciada, selecione a opção "Reiniciar Contagem";
2. Confirme a operação.

A sessão de contagem será reiniciada.

#### Monitoramento - Cancelando uma Sessão de Contagem

1. Na tela de monitoramento de uma atividade interativa, com uma sessão de contagem iniciada, selecione a opção "Cancelar Contagem";
2. Confirme a operação.

A sessão de contagem será cancelada e nenhuma movimentação será registrada.

#### Monitoramento - Concluindo uma Sessão de Contagem

1. Na tela de monitoramento de uma atividade interativa, com uma sessão de contagem iniciada, selecione a opção "Concluir Contagem";
2. Confirme a operação.

A sessão de contagem será concluída e serão registradas as movimentações para os itens lidos.

#### Fluxos

Um fluxo determina qual será o caminho esperado que um item percorrerá durante o processamento de uma atividade.

As seguintes informações são apresentadas no grid:
- Nome – Nome do Fluxo;
- Módulo – Módulo ao qual o fluxo foi registrado;
- Descrição – Breve descritivo do fluxo;
- Ativo – Indica se o fluxo está ativo no sistema.
- 
#### Configurando um novo Fluxo

1. Selecione Adicionar;
2. Informe os dados do fluxo;
3. Selecione a opção Salvar.

Dados do fluxo:
- Módulo – Módulo ao qual o fluxo será associado;
- Nome – Nome do fluxo;
- Descrição – Uma breve descrição;
- Ativo – Indica se o registro ainda está ativo.
- 
#### Editando um Fluxo

1. Para o registro desejado, selecione a opção Editar no menu Ações;
2. Altere os dados desejados e selecione a opção Salvar.

#### Excluindo um Fluxo

1. 1. Para o registro desejado, selecione a opção Excluir no menu Ações;
2. Confirme a operação de exclusão.

#### Etapas de um Fluxo

Uma etapa de um fluxo determina quais serão as características dos itens que serão envolvidos para aquele ponto do fluxo. 
Em um fluxo já cadastrado, é possível visualizar a tabela de etapas.

#### Configurando Etapas de um Fluxo

1. Na edição de um fluxo, selecione Adicionar;
2. Informe os dados da etapa do fluxo;
3. Selecione a opção Salvar.

Dados da etapa do fluxo:
- Atividade – Tipo de atividade ao qual o fluxo será associado;
- Status Esperado – Status esperado dos itens;
- Etapa Esperada – Etapa esperada dos itens;
- Permitir EPCs fora do fluxo – Indica se a etapa permitirá a leitura de itens que não estão associados ao fluxo.

#### Editando uma Etapa de um Fluxo

1. 1. Na edição de um fluxo, para o registro desejado, selecione a opção Editar no menu Ações;
2. Altere os dados desejados e selecione a opção Salvar.

#### Alterando a Ordem de uma Etapa de um Fluxo

Na edição de um fluxo, para o registro desejado, selecione a opção Mover Acima ou a opção Mover Abaixo no menu Ações.

#### Excluindo uma Etapa de Fluxo

1. Na edição de um fluxo, para o registro desejado, selecione a opção Excluir no menu Ações;
2. Confirme a operação de exclusão.

#### Modelos de Etiquetas

Um modelo de etiqueta determina as configurações para uma etiqueta. É possível acessar pela aba "Modelos de Etiqueta" no menu "Configurações".

As seguintes informações são apresentadas no grid:
- Nome – Nome do modelo;
- RFID – Indica se a escrita da etiqueta RFID está ativa;
- Bloquear após impressão - Indica impressão única;
- Usar configuração da impressora – Indica se fará uso das configurações da impressora;
- Impressora padrão – Indica se existe uma impressora padrão para a etiqueta;
- Ativo – Indica se o modelo está ativo no sistema.

#### Configurando um novo Modelo de Etiqueta

1. Selecione Adicionar;
2. Informe o nome;
3. Informe a descrição;
4. Informe as configurações de RFID, bloqueio e uso de configuração da impressora;
5. Informe a impressora padrão, se houver;
6. Informe se o registro estará ativo;
7. Informe o código ZPL.
8. Informe as configurações de dimensões (largura, altura, DPI, velocidade de impressão e opacidade).

Dados do modelo de etiqueta:
- Nome – Nome do modelo;
- Descrição – Uma breve descrição;
- RFID Ativo – Indica se a escrita da etiqueta RFID está ativa;
- Bloquear após impressão - Indica impressão única;
- Usar configuração da impressora – Indica se fará uso das configurações da impressora;
- Impressora padrão – Indica se existe uma impressora padrão para a etiqueta;
- Ativo – Indica se o modelo está ativo no sistema;
- Conteúdo ZPL - Código ZPL para gerar a etiqueta;
- Pré-visualização - Apresenta uma pré-visualização de etiqueta para um código ZPL e parâmetros válidos;
- Largura - Largura da etiqueta;
- Altura - Altura da etiqueta;
- DPI - Resolução da impressão;
- Orientação - Indica a orientação da etiqueta em graus;
- Velocidade da impressão - Velocidade de impressão da etiqueta;
- Opacidade - Intensidade da impressão.

#### Editando um Modelo

1. Para o registro desejado, selecione a opção Editar no menu Ações;
2. Altere os dados desejados e selecione a opção Salvar.

#### Excluindo um Modelo

1. Para o registro desejado, selecione a opção Excluir no menu Ações;
2. Confirme a operação de exclusão.

#### Realizando um Teste de Impressão

1. Para o registro desejado, selecione a opção Editar no menu Ações;
2. No menu de edições, com uma pré-visualização válida (com dimensões de altura, largura e DPI válidos), selecione a opção Teste de Impressão;
3. No menu de Teste de impressão, selecione uma impressora e defina uma quantidade de etiquetas;
4. Selecione a opção Imprimir;

#### Sensores

O ITTS permite o monitoramento de dados coletados por sensores. É possível acessar pela aba "Monitoramento" no menu "Sensores".

Para cada sensor, há um seção com as seguintes informações são apresentadas:
- Nome do dispositivo;
- Local monitorado, se houver;
- Item monitorado, se houver;
- Valores medidos com unidades de medida;
- Tipo do sensor;
- Range de operação, se houver;
- Nível de bateria do dispositivo;
- Configuração de alertas;
- Momento do último evento registrado.

É possível fazer um filtro geral dos sensores, considerando nome ou tipo do sensor.

#### Eventos de Sensores

O ITTS permite visualizar dados de eventos gerados por sensores. É possível acessar pela aba "Eventos" no menu "Sensores".

As seguintes informações são apresentadas no grid:
- Captura – Momento de captura do evento;
- Dispositivo – Dispositivo que registrou o evento;
- Item - Item monitorado, se houver;
- Local - Local monitorado, se houver;
- Sensor – Tipo de sensor;
- Valor - Valor medido;
- Último Status - Último status do evento;
- Status Atual - Status atual do evento;

É possível fazer filtros por dispositivo, item ou local. Os registros são apresentados considerando períodos de tempo sendo, última hora, últimas 24 horas e últimos 7 dias, configurável pela opção "Mais filtros".

#### Identificadores

#### Identificadores - Suspensão de um Epc

Um Epc pode ter sua utilização suspensa no sistema, podendo ser reativado posteriormente.

1. Acessar o item cadastrado detentor do Epc;
2. Para o Epc ativo desejado, selecionar a opção "Suspender";
3. Confirmar ação.

O Epc ficará indisponível no sistema até que seja reativado.

#### Identificadores - Ativação de um Epc

Um Epc pode ser ativado.

1. Acessar o item cadastrado detentor do Epc;
2. Para o Epc ativo desejado, selecionar a opção "Ativar";
3. Confirmar ação.

O Epc ficará disponível para uso no sistema.

#### Identificadores - Descarte de um Epc

Um Epc pode ser descartado.

1. Acessar o item cadastrado detentor do Epc;
2. Para o Epc ativo desejado, selecionar a opção "Descartar";
3. Confirmar ação.

O Epc ficará indisponível permanentemente.

#### Agregações de Itens

Uma agregação de itens permite agrupar um ou mais itens dentro de um item principal, estabelecendo uma relação entre eles. Cada item pode ser identificado por meio de seu identificador (EPC ou SSCC).

As seguintes informações são apresentadas no grid:
- Identificador – Identificador do item principal (container);
- Tipo de identificador – Tipo de identificação do item (EPC ou SSCC);
- Quantidade de itens – Quantidade de itens vinculados à agregação;
- Data de registro – Data e hora em que a agregação foi registrada;
- Data de atualização – Data e hora da última atualização da agregação, quando houver.

#### Configurando uma nova Agregação de Itens

1. Selecione Adicionar;
2. Informe o identificador do item principal (container);
3. Selecione o tipo de identificador (EPC ou SSCC);
4. Informe os identificadores dos itens que serão agregados;
5. Selecione Salvar para registrar a agregação.

Dados da agregação:
- Identificador – Identificador do item principal (container);
- Tipo de identificador – Tipo de identificação do item principal (EPC ou SSCC);
- Itens agregados – Relação dos itens vinculados ao item principal;
- Identificador do item – Identificador do item agregado;
- Tipo de identificador do item – Tipo de identificação do item agregado (EPC ou SSCC);
- Data de registro – Data e hora em que a agregação foi registrada;
- Data de atualização – Data e hora da última atualização da agregação.
 
#### Editando uma Agregação

1. Para o registro desejado, selecione a opção Editar no menu Ações;
2. Altere os dados desejados, incluindo os itens agregados, se necessário;
3. Selecione a opção Salvar.

#### Excluindo uma Agregação

1. Para o registro desejado, selecione a opção Excluir no menu Ações;
2. Confirme a operação de exclusão.

#### Tipos de Agregação

Um tipo de agregação determina uma classificação para as agregações de itens, permitindo organizar e identificar diferentes tipos de agrupamentos no sistema.

As seguintes informações são apresentadas no grid:
- Nome – Nome do tipo de agregação;
- Descrição – Breve descrição do tipo de agregação;
- Ativo – Indica se o tipo de agregação está ativo no sistema.

#### Configurando um novo Tipo de Agregação

1. Selecione Adicionar;
2. Informe o nome do tipo de agregação;
3. Informe a descrição;
4. Informe se o registro estará ativo;
5. Selecione Salvar para registrar o tipo de agregação.

Dados do tipo de agregação:
- Nome – Nome do tipo de agregação;
- Descrição – Uma breve descrição do tipo de agregação;
- Ativo – Indica se o tipo de agregação está ativo no sistema.

#### Editando um Tipo de Agregação

1. Para o registro desejado, selecione a opção Editar no menu Ações;
2. Altere os dados desejados e selecione a opção Salvar.

#### Excluindo um Tipo de Agregação

1. Para o registro desejado, selecione a opção Excluir no menu Ações;
2. Confirme a operação de exclusão.
# ITTS Tracker Manager – Guia do Usuário

Este documento apresenta o **ITTS Tracker Manager**, ferramenta de configuração e monitoramento do ITTS Tracker Service.

---


## Iniciando a interface de administração

Após a instalação, para iniciar o aplicativo procure por ITTS Tracker na caixa de pesquisa do Windows:

## 1. Conexão e Captura

### 1.1. Configurações de Conexão MQTT

Permite realizar as configurações de conexão com a plataforma ITTS para envio de dados por meio do protocolo MQTT. Registre o dispositivo no ITTS e aplique as configurações:

- **MQTT Host** - Endereço host do servidor MQTT;
- **Porta** - Porta de comunicação do host MQTT;
- **Id do Cliente** - Identificador cliente no host MQTT;
- **Usuário** - Usuário para conexão com o host MQTT;
- **Senha** - Senha de acesso ao host MQTT.

Após realizar as configurações clique no botão **Salvar** e em seguida utilize o botão **Testar Conexão** para verificar se os dados de conectividade estão válidos.

### 1.2. Configurações de Conexão com Web API

Permite realizar as configurações de conexão com a Web API da plataforma ITTS para obtenção de dados ou configurações. Atualmente a Web API é necessária para que o Tracker consiga obter os dados de inconsistências do piso e gerar dados de análise. Se o veículo não for realizar esta operação não será necessária sua configuração.

- **Web API Host** - Endereço host da Web API;
- **Habilitar** - Habita ou não a conectividade com a Web API;
- **Usuário** - Usuário para conexão com a Web API, preenchido automaticamente;
- **Senha** - Senha de acesso para conexão com Web API, preenchido automaticamente.

### 1.3. Dispositivo

Determina a identificação e configurações do dispositivo:

- **Identificação** - Permite definir a informação que identificará o veículo na plataforma ITTS. Por padrão o endereço MAC do dispositivo é utilizado como identificador. É possível configurar a leitura de um arquivo MachineInfo.ini para extrair o identificador.

No ITTS um veículo é um item e o valor da identificação deve ser atribuído ao Alias do item, seja ele o MAC ou valor do arquivo MachineInfo.ini.

### 1.4. Captura de Dados

As seguintes configurações para captura de dados estão disponíveis:

- **GPS Windows + Telemetria via BlueLink** - Neste caso os dados de geolocalização serão coletados via API Windows e caso a opção telemetria estiver selecionada serão coletados via dispositivo BlueLink;
- **GPS + Telemetria via BlueLink** - Neste caso os dados de geolocalização e telemetria serão determinados pelo dispositivo BlueLink GPS conectado;
- **Id Bluelink (MachineInfo)** - Se selecionado será pesquisado o dispositivo Bluelink configurado com o identificador do arquivo Machineinfo.ini;
- **Porta COM** - Permite conectar-se ao módulo de GPS por meio da porta serial;
- **Modo Desenvolvedor** - Se estiver utilizando o dispositivo BlueLink para realização de testes de bancada ou depuração, habilite este modo para que a aplicação configure o BlueLink em modo desenvolvedor. O modo desenvolvedor gera alguns tipos de dados aleatoriamente permitindo a realização de testes sem estar conectado a um veículo.
- **Formato de Data e Hora** - Permite configurar o formato de data e hora do payload. O Formato de Data e Hora a ser selecionado vai depender da versão da plataforma ITTS utilizada. A partir da versão 2.0 do ITTS utiliza Unix epoch time.

O dispositivo BlueLink deve ter o nome amigável configurado para "BlueLink-1" ou com o mesmo valor configurado no arquivo MachineInfo. Para configurar o nome do dispositivo, utilizar o aplicativo para Android **BlueLink Admin**. Configure o **Friendly name** com prefixo "1" ou com o valor de seu arquivo MachineInfo.

Quando a conexão com o dispositivo BlueLink é estabelecida, o led de conectividade bluetooth se manterá na cor azul.

### 1.5. Opções de Heartbeat

Permite configurar o tópico para envio dos dados assim como o intervalo de envio. O tópico de heartbeat pode ser obtido no ITTS. Por padrão seguirá a seguinte regra **prefixo/clientid/heartbeat**.

## 2. Localização

### 2.1. Configuração

Permite configurar o tópico de envio de localização assim como o intervalo de envio de acordo com o status do objeto monitorado.

Quando não houver conectividade, uma fila com os dados obtidos é armazenada como buffer. Configure o tamanho da fila com o tamanho desejado

O tópico de geolocation pode ser obtido no ITTS. Por padrão seguirá a seguinte regra **prefixo/clientid/geolocation**.

## 3. Telemetria

### 3.1. Configuração

Permite configurar o tópico de envio de dados de telemetria assim como quais sensores devem ser enviados.

O envio dos dados de telemetria está condicionado ao status do veículo:

- **Em Movimento** - Quando o veículo está em movimento;
- **Estacionado** - Quando o veículo está com o motor ligado, porém sem movimentação;
- **Parado** - Quando o veículo está com o motor desligado.

**Quando o veículo está parado, nenhum dado de telemetria é enviado.**

O tópico de telemetria pode ser obtido no ITTS. Por padrão seguirá a seguinte regra **prefixo/clientid/telemetry**.

> Importante: O payload de dados de telemetria pode não conter valor para todos os sensores em todas as vezes em que é enviado.

## 4. Log ML

### 4.1. Configuração

Permite aplicar configuração de captura de dados para Machine Learning. A captura de dados fará uso dos dados de acelerômetro do dispositivo e dos dados de telemetria via BlueLink.

As seguintes configurações podem ser ajustadas:

- **Processar Dados** - Habilita a coleta dos dados. Dever ser habilitado somente nos veículos que farão a coleta de dados;
- **Caminho do Arquivo** - Pasta onde os arquivos com os dados de coleta serão armazenados;
- **Frequência de Captura** - Frequência de captura dos dados;
- **Velocidade Mínima** - Velocidade mínima do veículo para dar início ao processo de captura;
- **Tipo Veículo** - O valor informado será utilizado para no log registrar o tipo do veículo que realizou a captura;
- **Consultar como Atributo via API** - Se esta opção estiver marcada, o tipo do veículo será consultado via API no ITTS. Para isso será consultado o item por meio de seu identificador e utilizado o valor do atributo configurado em **_Tipo Veículo._**
- **Envio de Dados** - Permite selecionar quais informações de telemetria serão registradas.

## 5. Log

Permite monitorar o log de eventos do serviço. O Campo **GPS** mostra a última coordenada obtida e o botão **Visualizar** pode ser utilizado para abrir o navegador e apresentar a coordenada no Google Maps.

O campo **Arquivo** apresenta a localização do arquivo de log que será monitorado. Caso a instalação tenha sido feita em um outro local, altere o caminho do arquivo e salve a configuração antes de iniciar o monitoramento.

Para realizar o monitoramento:

- Selecione a aba **Log**;
- Altere o local do arquivo de log se necessário;
- Clique no botão **Monitorar**.

Para parar o monitoramento, clique no botão **Parar**.

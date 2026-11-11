# ITTS TLM – Guia do Usuário

Este documento apresenta o módulo **ITTS TLM** e seus componentes.

---

## 1. Introdução
TLM (Vehycle Telemetry Location System) é o modulo ITTS para Localização e Telemetria de Veículos.

## 1.1. Funcionalidades
- Gestão dos veículos monitorados;
- Localização com GPS;
- Localização com RFID;
- Monitoramento do veículo;
- Monitoramento do motorista;
- Monitoramento de rotas;

## 1.2. Requisitos
- Tags RFID para localização com RFID;
- Leitor RFID IMPINJ R220/R420/R700 para localização com RFID;
- Dispositivo BLE BlueLink para captura de dados de telemetria e ou GPS;
- Tablet com Windows 10 ou superior com recursos de GPS e Acelerômetro para monitoramento dos veículos;
- Aplicativo ITTS Tracker, para coleta de dados de geolocalização, telemetria e monitoramento do piso.

> Importante: Os leitores Impinj R220 ou R420 precisam ter o firmware 6.4.1.240 ou superior.

## 1.3. Veículos
Representa qualquer veículo que será monitorado como um automóvel, um caminhão etc. Cada veículo deverá ser identificado com um ou mais identificadores, podendo ser:

- Tag RFID;
- Beacon BLE.

## 1.4. Eventos de Localização
Representa o registro dos dados de localização de um veículo, contemplando os identificadores registrados e outras informações de detalhamento.

## 1.5. Eventos de Telemetria
Representa o registro dos dados de telemetria de um veículo, enviados a partir do ITTS Tracker, contemplando os identificadores registrados e outras informações de detalhamento.

## 1.6. Acessando o Módulo
Para acessar o módulo, efetuar o login no ITTS com um usuário configurado com as permissões de acesso. Após o login, na tela inicial, selecionar o módulo TLM.
Um painel inicial com as principais opções do módulo será apresentado:

---

# 2. Gestão de Veículos

## 2.1. Configurando Veículos

### 2.1.1. Itens

O ITTS utiliza uma estrutura genérica de itens. Isso significa que seu veículo assim como qualquer coisa monitorada pelo ITTS é um item. Os itens podem conter campos customizados. Para isso você deverá criar um grupo de itens e criar os campos customizados para cada grupo.

### 2.1.2. Configurando um Grupo

Para que você possa ter campos customizados para seu item será necessária a criação de um grupo. Você poderá, por exemplo, criar um grupo "Veículos" e a este grupo adicionar campos como placa, marca, modelo, etc.

Para criar um grupo:

- Na tela inicial ou menu lateral, selecione **Meus Itens**;
- Selecione a aba **Grupos**;
- Selecione **Adicionar**;
- Dê um nome para o grupo;
- Informe um subgrupo se desejar;
- Selecione a opção **Salvar**.

### 2.1.3. Customizando Campos

Você poderá ter campos customizados para seu grupo e assim permitir agregar informações ao item monitorado.

Para criar um campo:

- Após criar o grupo, edite seu registro (botão Ações -> Editar);
- Vá até a seção **Campos Customizados**;
- Selecione **Adicionar**;
- Informe o nome do campo e uma descrição;
- Selecione o tipo de dado aceito pelo campo;
- Altere as configurações do campo conforme desejado;
- Selecione a opção **Salvar**.

### 2.1.4. Configurando um Veículo

Para configurar um novo veículo:

- Na página inicial ou no menu lateral, selecione **Meus Itens**;
- Selecione o botão **Adicionar**;
- Selecione o módulo ao qual o veículo será vinculado;
- Selecione o grupo ao qual o veículo será associado;
- Informe uma identificação;
- Informe um alias se necessário;
- Informe uma descrição e preencha os campos customizados conforme necessário;
- Selecione a opção **Salvar**.

O valor do campo Alias pode ser necessário para determinadas operações.

### 2.1.5. Vinculando Identificadores

Para que um veículo possa ser monitorado é necessário associar identificadores. Para editar os identificadores, na lista de itens, selecione a opção **Editar**. Na parte inferior da tela serão apresentados os identificadores associados:

- Selecione o tipo de identificador, RFID ou BLE;
- Se o identificador for RFID, selecione o modelo do identificador;
- Informe a posição de fixação se desejado;
- Preencha o EPC de 96 bits ou informe o endereço Mac, de acordo com o tipo de identificador selecionado;
- Informe a chave de segurança (TID), disponível apenas para identificadores RFID;
- Clique no botão **Adicionar**.

Se você tiver um leitor RFID configurado poderá fazer a leitura da etiqueta de RFID utilizando o botão **Ler Etiqueta RFID**.

Para configurar um dispositivo de leitura, no menu **Meus Dispositivos**, no dispositivo escolhido, selecione Ações -> Definir como Padrão:

### 2.1.6. Atualização automática de identificadores

O aplicativo ITTS Tracker envia periodicamente dados de heartbeat para a plataforma ITTS. 
Esses dados contém além de outras informações o identificador e alias configurados sendo:

- Identificador - Endereço MAC da interface de rede do dispositivo;
- Alias - Endereço MAC da interface de rede do dispositivo ou valor configurado em arquivo.

O serviço ITTS monitora os dados de heartbeat enviados para criar ou mover os identificadores automaticamente.

Se não existir o identificador para o alias registrado, o identificador será registrado.
Se o identifador existir para um alias diferente do registrado, o identificador será movido para o novo alias.

---

# 3. Localização com GPS e Telemetria

## 3.1. Localização com GPS

A tecnologia **GPS (Global Positioning System)** é uma solução eficaz para localizar, monitorar e rastrear veículos em tempo real, permitindo acompanhar deslocamentos, rotas percorridas e eventos importantes durante a operação. É amplamente utilizada em frotas, logística, segurança veicular e serviços de telemetria, garantindo maior controle operacional, redução de custos e aumento da segurança dos ativos.

A localização com GPS depende dos seguintes elementos:

- Tablet com Sensor GPS;
- Dispositivo Blue Link se o tablet não possuir sensor GPS.
- Aplicativo Tracker configurado para enviar os dados de GPS para a plataforma.

## 3.2. Telemetria

A **coleta de dados de telemetria veicular** permite monitorar em tempo real o desempenho, o comportamento e as condições operacionais de um veículo. Por meio de sensores integrados e sistemas de comunicação como GPS, RFID ou módulos embarcados, é possível registrar informações como velocidade, rota, aceleração, consumo de combustível, status do motor e eventos críticos. Esses dados são essenciais para aumentar a eficiência operacional, melhorar a segurança, otimizar rotas, reduzir custos de manutenção e oferecer maior inteligência às operações de transporte e logística.

## 3.3. Configurando o envio de dados

O aplicativo Tracker deve ser configurado para envio dos dados de GPS e Telemetria. Mais informações sobre a configuração do aplicativo podem ser consultadas no Guia do Usuário do ITTS Tracker Manager.

No aplicativo será necessário configurar como será feita a captura de dados. O padrão é utilizar o GPS Windows + Telemetria com BlueLink. Se o Driver do sensor de GPS entregar os dados apenas pela porta COM será necessário selecionar esta porta. O formato da data e hora dos eventos deve ser Unix Epoch.

Será necessário configurar o tópico para envio dos dados de geolocalização e telemetria conforme as regras da plataforma, além de indicar quais dados de telemetria serão capturados.

O envio de dados será feito conforme o status do motor e de movimentação de acordo com os valores configurados:

- Veículo estacionado - parado com o motor desligado;
  - Neste caso não haverá envio de dados de telemetria.
- Veículo parado - motor ligado, porém parado;
- Veículo em movimento - motor ligado e em movimento.

## 3.4. Histórico de Localização GPS

### 3.4.1. Visualizando histórico de localização GPS

Para visualizar os dados de localização de um ou mais veículos, selecione a aba **Relatório de Localização GPS**. O relatório de localização será apresentado:

O grid deverá apresentar os seguintes dados:

- **Registro** - Data e hora do registro.
- **Veículo** - Identificador descritivo exclusivo configurado para o veículo;
- **Localização GPS** - Dados da localização do veículo.

## 3.5. Histórico de Telemetria

### 3.5.1. Visualizando histórico de telemetria

Para visualizar os dados de telemetria de um ou mais veículos, selecione a aba Histórico de Telemetria. O relatório de telemetria será apresentado:

O grid deverá apresentar os seguintes dados:

- **Veículo** - Identificador descritivo exclusivo configurado para o veículo;
- **Registrado** - Data e hora do registro;
- **Telemetria** - Telemetria registrada.

---

# 4. Localização com RFID

## 4.1. Introdução

### 4.1.1. Como funciona a localização com RFID

A tecnologia **RFID (Radio Frequency Identification)** é uma solução eficiente para identificar e rastrear veículos automaticamente em diversos cenários, como controle de acesso em estacionamentos, pedágios eletrônicos e sistemas de logística.

A localização com RFID depende dos seguintes elementos:

- Conjunto Leitor RFID + Antenas RFID para os pontos onde será feito o monitoramento;
- Tags de RFID fixada nos veículos para identificação.

### 4.1.2. Fluxo de Identificação do Veículo

O processo de identificação é bem simples e segue as seguintes etapas:

- Assim que a etiqueta RFID entra no campo de leitura o sistema registra a chegada do veículo e inicia o seu monitoramento;
- Durante o monitoramento todas as etiquetas RFID do mesmo veículo que forem lidas serão registradas e contabilizadas;
- Assim que todas as etiquetas RFID estiverem fora do campo de leitura por mais de 10 segundos, o evento de saída é registrado com a data e hora da última visualização de qualquer uma das etiquetas.

## 4.2. Configurando Pontos de Leitura

### 4.2.1. Configurando um Ponto de Leitura

O ponto de leitura é o local onde será feita a identificação do veículo. Este local deverá ter um leitor RFID associado e um conjunto de antenas. Atualmente apenas os leitores IMPINJ R220/R420 e R700 estão suportados.

**Para configurar um ponto de leitura:**

- No menu selecione a opção **Pontos de Leitura**;
- Selecione o botão **Adicionar**;
- Informe o nome para o ponto de leitura, por exemplo "Portaria Entrada";
- Selecione o módulo "Telemetria e Localização de Veículos";
- Selecione a operação "Monitoramento de Presença";
- Mantenha a opção "Ativo" selecionada;
- Ative a opção "Habilitar Monitoramento";
- Selecione a opção **Salvar**.

**Para vincular o leitor RFID:**

Após a criação do ponto de leitura é necessário vincular o dispositivo RFID responsável pela leituras das etiquetas de identificação dos veículos e vincular a um local físico previamente cadastrado.

- Para o ponto de leitura desejado, selecione a opção **Editar**;
- Em **Dispositivos** selecione a opção **Adicionar**;
- Selecione o dispositivo RFID fisicamente configurado no ponto de leitura;
- Selecione um local para vincular as leituras;
- Selecione as antenas que serão utilizadas para coleta das leituras;
- Selecione a opção **Salvar**.

> **Importante**: Os leitores IMPINJ devem ter a opção de processamento por SDK habilitado.

## 4.3. Histórico de Localização RFID

### 4.3.1. Visualizando histórico de localização RFID

Para visualizar os eventos de identificação, em "Histórico", selecione a aba Histórico de Localização RFID. O relatório de eventos deverá ser apresentado:

O grid deverá apresentar os seguintes dados:

- **Veículo** - Identificador descritivo exclusivo configurado para o veículo;
- **Identificador** - Identificador exclusivo da Tag do veículo;
- **Local Origem** - Local onde o veículo foi identificado;
- **Modelo Tag** - Modelo da Tag do veículo;
- **Posição** - Posição de fixação da Tag;
- **Chegada** - Data e hora de chegada do veículo no local;
- **Saída** - Data e hora de saída do veículo no local;
- **Anotações** - Apresenta as anotações cadastradas no local.

Para visualizar os detalhes de uma identificação, para o registro desejado selecione o botão **Ações**.

O log conterá informações detalhadas dos eventos como quais identificadores foram processados e a quantidade de eventos para cada um em qual antena.

---

# 5. Cerca Eletrônica

## 5.1. Introdução

### 5.1.1. Cerca eletrônica

A funcionalidade de cerca eletrônica permite definir limites geográficos digitais utilizando coordenadas GPS. Quando um objeto ou veículo monitorado entra ou sai dessas áreas, o sistema registra um evento, que pode ser recebido em tempo real via MQTT, consultado posteriormente por meio de relatórios ou consumido via API.

## 5.2. Locais

### 5.2.1. Configurando um Local

A configuração de um local deve ser feita acessando a opção **Minhas Empresas** no menu lateral ou no menu principal. Deve-se acessar a aba "Locais" e clicar em "Adicionar". A tela de criação deve ser apresentada:

- Selecione um **Tipo**;
- Informe um **Nome**;
- Os demais campos são de preenchimento opcional.

> **Importante**: Um local pode ser de qualquer tipo, exceto Área de Armazenamento.

### 5.2.2. Coletando as Coordenadas de um Local

Navegue até a seção "Geolocalização" da tela:

Com a opção "Coordenadas específicas" selecionada, deve-se preencher os dados de Latitude e Longitude.

A visualização é suportada no modo Street e no modo Satélite por meio da seleção das respectivas opções.

Também é possível determinar a localização via seleção no mapa. Para habilitar a captação da localização via seleção no mapa, deve-se clicar no botão "Selecionar no mapa", que deve alterar sua aparência, conforme:

Quando essa opção estiver selecionada, o mapa será fixado e o ponto em que receber o clique será marcado como localização, conforme:

Após a seleção do local, deve-se clicar no botão "Confirmar". Essa ação irá preencher os campos de Latitude e Longitude conforme determinados pela seleção no Mapa:

Com a opção "Conjunto de coordenadas" selecionada, deve-se fornercer um conjunto de coordenadas conforme formato:

Também é possível determinar a localização via seleção no Mapa:

Para habilitar a seleção no mapa, deve-se clicar no botão "Desenhar no Mapa", que deve alterar sua aparência:

Quando essa opção estiver selecionada, o mapa será fixado e será possível selecionar múltiplos pontos mapa, conforme:

A partir da seleção de 3 pontos, um desenho será plotado, delimitando a area do local. Ao clicar em confirmar, o campo de coordenadas será preenchido com os dados de latitude e longitude de cada ponto selecionado no mapa:

Definidas as características do local conforme preferência, deve-se clicar em "Salvar" para salvar os dados de registro do local.

Exemplo Json de coordenadas:

```json
[
    {
        "name": "collect",
        "position": [
            {
                "alt": 0,
                "lat": -22.821885,
                "lng": -47.241379,
                "name": "P1"
            },
            {
                "alt": 0,
                "lat": -22.822471,
                "lng": -47.240487,
                "name": "P2"
            },
            {
                "alt": 0,
                "lat": -22.821811,
                "lng": -47.239897,
                "name": "P3"
            },
            {
                "alt": 0,
                "lat": -22.821189,
                "lng": -47.240812,
                "name": "P4"
            }
        ]
    }
]
```

## 5.3. Regras de Cerca Eletrônica

As regras permitem definir o comportamento desejado durante a entrada e ou saída de uma área delimitada.

Antes de poder criar as regras será necessário mapear os locais que serão utilizados.

### 5.3.1. Adicionar uma Regra

- Dentro do módulo TLM, selecione a opção **Gestão e Manutenção**;
- Selecione a aba **Regras de Cerca Eletrônica;**
- Selecione **Adicionar**;
- Selecione um local já registrado, contendo as coordenadas da área delimitada;
- Informe uma descrição para facilitar a identificação da regra;
- Selecione o tipo de regra;
- Configure o tempo limite para considerar o evento;
- Selecione a opção **Salvar**.

### 5.3.2. Editando uma Regra

- Dentro do módulo TLM, selecione a opção **Gestão e Manutenção**;
- Selecione a aba **Regras de Cerca Eletrônica;**
- Para o registro desejado, selecione a opção **Editar** no menu **Ações**;
- Altere os dados desejados e selecione a opção **Salvar**.

### 5.3.3. Excluindo uma Regra

- Dentro do módulo TLM, selecione a opção **Gestão e Manutenção**;
- Selecione a aba **Regras de Cerca Eletrônica;**
- Para o registro desejado, selecione a opção **Excluir** no menu **Ações**;
- Confirme a operação de exclusão.

## 5.4. Eventos em Tempo Real

### 5.4.1. Visualizando os Eventos em Tempo Real

A visualização ou consumo dos eventos em tempo real deverá ser feito por MQTT. Para isso cadastre uma aplicação para fazer acesso ao Broker MQTT. Com uma aplicação registrada, faça o subscribe no(s) seguinte(s) tópico(s):

|Tópico|Descrição|
|------|---------|
|prefixo/deviceid/tlm_eletronicfence_event|Eventos de chegada ou partida|
|prefixo/deviceid/tlm_eletronicfence_event/arrival|Eventos de chegada|
|prefixo/deviceid/tlm_eletronicfence_event|Eventos de partida|
|prefixo/+/tlm_eletronicfence_event|Eventos de todos os dispositivos|

Exemplos payload evento chegada:

> Topic: hjapf/ipjr420/tlm_presense_event/arrival

```json
{
	"timestamp":"1753995232",
	"id":"CBFA00000000000000000005",
	"alias":"tracker01",
	"direction":"arrival",
	"place":"Portaria Entrada"
}
```

Exemplos payload evento partida:

> Topic: hjapf/ipjr420/tlm_presense_event/departure

```json
{
	"timestamp":"1753995243",
	"id":"CBFA00000000000000000005",
	"alias":"tracker01",
	"direction":"departure",
	"place":"Portaria Entrada"
}
```

## 5.5. Histórico de Cerca Eletrônica

### 5.5.1. Visualizando o histórico de cerca eletrônica

Para visualizar o histórico de eventos, dentro do módulo TLM, em Histórico, selecione a opção **Histórico de Cerca Eletrônica**. O Histórico de eventos será apresentado

---

# 6. Monitoramento do piso

## 6.1. Introdução

### 6.1.1. Monitoramento do Piso

Por meio desta funcionalidade o ITTS realiza o monitoramento de irregularidades e defeitos no piso com uso de sensores e IA.

### 6.1.2. Funcionalidades

- Classificação dos tipos de inconsistências;
- Registro e manutenção das inconsistências;
- Identificação automática de inconsistências do piso por meio de algoritmo de Machine Learning;
- Dashboard de monitoramento do piso com mapa de calor.

### 6.1.3. Requisitos

Os seguintes requisitos são necessários para operação:

- 1 Tablet com Windows 10 ou superior para mapeamento das inconsistências do piso;
- 1 Tablet com Windows 10 ou superior para cada veículo;
  - Porta TCP 1883 (entrada) permitida no firewall local;
  - Suporte GPS e Acelerômetro.
- Dispositivo BLE BlueLink.

#### 6.1.3.1. Tablet/Computador

O tablet ou computador com Windows executa os aplicativos e serviços ITTS local para a realização de captura de dados e ou monitoramento. 
Os seguintes aplicativos e serviços deverão ser instalados em cada um dos veículos:

- **ITTS Tracker Service** - Aplicativo/Serviço para monitoramento do piso e coleta de outras informações;
- **ITTS Tracker Manager** - Aplicativo de configuração do ITTS Tracker Service.

Todos os aplicativos podem ser descarregados diretamente na página de ajuda do Website ITTS.

Para mais informações consultar a documentação do ITTS Tracker.

Para o mapeamento inicial das inconsistências do piso:

- **ITTS Site Survey** - Aplicativo que permite a identificação e classificação de inconsistências para auxiliar o processo de aprendizado.

Para mais informações consultar a documentação do ITTS Site Survey.

## 6.2. Classificando as inconsistências do piso

Para o registro das inconsistências do piso é necessário realizar a configuração das classificações, permitindo que cada inconsistência tenha uma classificação atribuída.

Estas classificações também estarão disponíveis para o aplicativo Survey por meio da API.

Para visualizar as inconsistências registradas, dentro do módulo TLM, selecione a opção **Gestão e Manutenção** e, em seguida, selecione a aba **Classificação de Inconsistências do Piso**.

### 6.2.1. Configurando uma nova classificação

- Dentro do módulo TLM, selecione a opção **Gestão e Manutenção**;
- Selecione a aba **Classificação de Inconsistências do Piso;**
- Selecione **Adicionar**;
- Informe o Nome, Descrição e marque o registro como ativo para disponibilizar esta classificação;
- Selecione a opção **Salvar**.

### 6.2.2. Editando uma classificação

- Dentro do módulo TLM, selecione a opção **Gestão e Manutenção**;
- Selecione a aba **Classificação de Inconsistências do Piso;**
- Para o registro desejado, selecione a opção **Editar** no menu **Ações**;
- Altere os dados desejados e selecione a opção **Salvar**.

### 6.2.3. Excluindo uma classificação

- Dentro do módulo TLM, selecione a opção **Gestão e Manutenção**;
- Selecione a aba **Classificação de Inconsistências do Piso;**

Para o registro desejado, selecione a opção **Excluir** no menu **Ações**;

- Confirme a operação de exclusão.

## 6.3. Inconsistências do piso

As inconsistências são representadas por uma ou mais coordenadas geográficas e são registradas pelo aplicativo de Survey por meio da API. A ação de registrar uma nova inconsistência deverá ser feita preferencialmente por meio do aplicativo Survey.

Utilize esta funcionalidade para visualização e manutenção dos registros de inconsistência.

Para visualizar as inconsistências registradas, dentro do módulo TLM, selecione a opção **Gestão e Manutenção** e, em seguida, selecione a aba **Inconsistências do Piso**.

### 6.3.1. Configurando uma nova inconsistência

- Dentro do módulo TLM, selecione a opção **Gestão e Manutenção**;
- Selecione a aba **Inconsistências do Piso;**
- Selecione **Adicionar**;
- Informe os dados da inconsistência;
- Selecione a opção **Salvar**.

Dados da inconsistência:

- **Classificação** - Classifica a inconsistência;
- **Descrição** - Uma breve descrição;
- **Coordenadas** - Uma ou mais coordenadas em formato Json;
- **Registro** - Data e hora de registro da inconsistência;
- **Resolução** - Data e hora de registro da resolução da inconsistência;
- **Ativo** - Indica se o registro ainda está ativo.

### 6.3.2. Editando uma inconsistência

- Dentro do módulo TLM, selecione a opção **Gestão e Manutenção**;
- Selecione a aba **Inconsistências do Piso;**
- Para o registro desejado, selecione a opção **Editar** no menu **Ações**;
- Altere os dados desejados e selecione a opção **Salvar**.

### 6.3.3. Excluindo uma inconsistência

- Dentro do módulo TLM, selecione a opção **Gestão e Manutenção**;
- Selecione a aba **Inconsistências do Piso;**
- Para o registro desejado, selecione a opção **Excluir** no menu **Ações**;
- Confirme a operação de exclusão.

### 6.3.4. Identificação automática de inconsistências

A identificação automática das inconsistências é feita por meio do aplicativo ITTS Tracker que é executado como serviço no Tablet.

O aplicativo ITTS possui um algoritmo de identificação automática baseado em Machine Learning e utiliza os dados de telemetria para identificar as inconsistências do piso.

## 6.4. Monitoramento do piso

Para visualizar o dashboard de monitoramento do piso selecionar o menu **Monitoramento** e em seguida selecionar a guia **Monitoramento do Piso**.

---

# 7. Monitoramento de Rotas

## 7.1. Introdução

### 7.1.1. Monitoramento de Rotas

Por meio desta funcionalidade o ITTS realiza o monitoramento de rotas dos veículos.

### 7.1.2. Rotas

As rotas são composta por conjuntos de pontos de coordenadas geográficas que representam uma posição de um veículo em um determinado momento.

## 7.1.3. Monitoramento de Rotas

Para visualizar a funcionalidade de monitoramento de rotas, selecionar o menu **Monitoramento** e em seguida selecionar a guia **Monitoramento de Rotas**.

Deve-se selecionar um veículo e um período para visualizar as rotas correspondentes, se existirem.

Quando uma rota está disponível, o mapa apresenta:

- Ponto inicial;
- Pontos intermediários;
- Pontos final.

Os pontos intermediários agrupam informações, sendo essas:

- Veículo;
- Data;
- Velocidade;
- Status.

Os pontos incial e final são apresentados como círculos de cores verde e vermelha, respectivamente.

Quando há uma velocidade registrada, indicando que o veículo está em movimento, é apresentada uma seta indicando a direção da movimentação.

Quando não há uma velocidade registrada, indicando que o veículo está parado, é apresentado um círculo na cor laranja.

Para visualizar os detalhes basta clicar sobre um ponto no mapa.

## 7.2. Site Survey

### 7.2.1. O que é o Site Survey

Site Survey é o aplicativo utilizado para coletar e enviar informações para o ITTS. Ele pode ser instalado em um computador ou tablet Windows. Após a instalação basta configurar o acesso MQTT e API para que ele possa trocar dados com a plataforma ITTS.

Neste contexto o Survey será utilizado para identificação e classificação das inconsistências no piso e envio destas informações para a plataforma ITTS.

### 7.2.2. Instalação

Para instalar o aplicativo:

- Descarregue o aplicativo a partir da página de ajusta no Website ITTS;
- Execute o arquivo do instalador;
- Assim que o instalado for iniciado, clique no botão **Avançar**;
- Selecione o local de instalação e clique no botão **Avançar**;
- Clique no botão **Avançar** novamente e, em seguida, **Fechar** para concluir.

Para iniciar o aplicativo basta procurar por **ITTS Site Survey** em seu Windows.

### 7.2.3. Configurando o Site Survey

Para que o aplicativo de Survey possa ser utilizado será necessário registrar o acesso MQTT e API. Para isso será necessário registrar um aplicativo no Website ITTS:

- No ITTS, selecione **Meus Aplicativos**;
- Na aba **Aplicativos**, selecione o botão **Adicionar**;
- Dê um nome para o aplicativo, por exemplo "App Survey";
- Configure os dados de acesso para a API e configure quais Apps o aplicativo terá acesso;
- Configure os dados de acesso MQTT;
- Configure o aplicativo como ativo e clique **Salvar**.

Com os dados de acesso configurados, aplique as configurações no aplicativo.

**Acesso MQTT**

Para configurar o acesso MQTT no Survey:

- No menu **Arquivo** selecione **Preferências**;
- Selecione a aba **MQTT**;
- Configure o servidor e a porta de comunicação, normalmente 1883;
- Configure o Id do cliente, usuário e senha registrados no ITTS;
- Clique no botão **Testar Conexão** para checar se as configurações estão válidas;
- Selecione o botão **Salvar** para guardar as configurações.

**Acesso API**

- No menu **Arquivo** selecione **Preferências**;
- Selecione a aba **API**;
- Configure o servidor;
- Configure o usuário e senha registrados no ITTS;
- Clique no botão **Testar Conexão** para checar se as configurações estão válidas;
- Selecione o botão **Salvar** para guardar as configurações.

## 7.2.4. Coletando Inconsistências

Para realizar a coleta das inconsistências, no menu **Modelo** selecione a opção **Mapeamento de irregularidades do Piso**. A tela de coleta de coordenadas será apresentada:

### 7.2.4.1. Conectando o Dispositivo

Você precisará conectar o Survey ao dispositivo receptor de GPS, responsável por fornecer ao Survey as coordenadas de geolocalização.

Após ligar o dispositivo receptor GPS, selecione a porta serial correspondente e clique no botão **Conectar** para estabelecer a comunicação.

Se a conexão for estabelecida, a guia **Dados Recebidos (Serial)** apresentará os dados recebidos do dispositivo.

Os dados NMEA serão apresentados ao lado direito. Utilize o botão **Ver** para abrir o Google Maps com a sua localização atual.

### 7.2.4.2. Recebendo Coordenadas de Correção

Para dar precisão as coordenadas obtidas, será necessário conectar-se ao canal do transmissor GNSS para a recepção de coordenadas de correção. Isso interfere diretamente na qualidade dos dados recebidos. Para isso informe o tópico de correção e clique no botão **Conectar**, conforme exemplo:

Após a conexão a guia Dados Recebidos (MQTT) deverá apresentar os dados recebidos do transmissor GNSS e a qualidade dos dados deverá ser atualizada em poucos segundos para **Rtk**.

É importante que antes de iniciar a coleta que a qualidade de captura de dados seja **Rtk**.

### 7.2.4.3. Coletando uma Inconsistência

Ao abrir o menu de irregularidades do piso a aba **Dados** apresenta as inconsistências já registradas no grid. Uma inconsistência poderá ser editada ou excluída.

Quando uma inconsistência estiver modo de edição poderá ser visualizada no Google Maps selecionando a aba **Visualização**.

### 7.2.4.4. Registrando uma nova Inconsistência

Para inserir uma nova inconsistência:

- Selecione o botão **Novo**;
- Do lado direito da tela na aba **Detalhes**, informe uma descrição e a classificação;
- Na aba **Coordenadas**, utilize o dispositivo de coleta para definir um polígono com as coordenadas ou se for o caso apenas uma coordenada no centro da inconsistência;
- Selecione o botão **Adicionar**.

Se necessário qualquer coordenada pode ser removida. Para remover uma coordenada, selecione a coordenada no grid e utilize o botão **Excluir**.

## 7.2.5. Coletando logs de Monitoramento

A coleta de logs de monitoramento pode ser necessária para alimentar o mecanismo de Machine Learning durante a faze de implantação. Esta coleta será feita com o aplicativo ITTS Tracker executado em um ou mais veículos.

Para habilitar a funcionalidade de coleta de dados no Tracker:

- Atualize o Tracker Manager e Service para a versão mais recente;
- No Tracker Manager, selecione a aba **Monitoramento do Piso**;
- Em **Configuração**, marque a opção **Enviar Dados**;
- Em **Configuração**, marque a opção **Log para Análise**;
- Selecione um **Caminho do Arquivo**, local onde os arquivos serão armazenados;
- Configure a **Frequência de Captura**;
- Configure um valor mínimo de **Velocidade** para iniciar a captura;
- Para identificação do veículo, no campo **Tipo Veículo** indique o atributo do Grupo ITTS que contém esta informação e marque a opção **Consultar como Atributo via API**;
- Marque os dados que devem acompanhar o registro do evento;
- Salve as configurações e reinicie o Tracker Service.

Se a opção **Consultar como Atributo API** não estiver selecionada, será utilizado o valor informado no campo para identificação do tipo de veículo.

Quando o aplicativo estiver em execução e de acordo com as configurações definidas, verifique se os arquivos de log estão sendo gerados na pasta configurada.

Para que a coleta de dados funcione corretamente é necessário que a captura de dados esteja configurada para **GPS Windows + Telemetria via BlueLink**.

Posteriormente estes arquivos deverão ser recolhidos e encaminhados para a etapa de análise e processamento.

---

# 8 - Integração com Display BLE

## 8.1. Integração com Display BLE

Por meio desta funcionalidade o ITTS realiza integração com displays BLE. Para uso desta funcionalidade o Identix Tracker deve estar nas seguintes versões:

- Service 2.6.0 ou superior;
- Manager 2.5.0 ou superior.

## 8.2. Conectividade com Display BLE

A conexão é realizada com o dispositivo BLE mais próximo, combinado com um filtro de RSSI.

O valor padrão do filtro RSSI é de -65 dBm, podendo ser alterado para um valor mais alto ou mais baixo.

Para alterar o valor do filtro RSSI na aba "Notificações" do Tracker Manager, altera o valor do campo "Filtro RSSI".

## 8.3. Notificações via display

Via display, são exibidas notificações em forma de textos com cor e duração definidos pelo usuário. 

Para fazer uso de notificações via display deve-se habilitar a configuração "Notificar no Display", na aba "Notificações" do Tracker Manager.

Com a configuração habilitada as mensagens poderão ser enviadas para o display. Será feita e mantida uma conexão com o dispositivo BLE mais próximo.

O envio das mensagens é feito por meio da API (consulte documentação API).
 
Para esta operação, apenas as cores verde (green), vermelho (red) e amarelo (yellow) são suportadas.

As mensagens são persistidas em histórico por 1 hora do lado do ITTS.

Fluxo de envio de mensagens:

┌──────────────────────────────────────────┐
│ Requisição de envio de mensagem          │
│ API                                      │
└──────────────────────────────────────────┘
                    │
                    ▼
┌──────────────────────────────────────────┐
│ Persistência e log da mensagem           │
│ Service                                  │
└──────────────────────────────────────────┘
                    │
                    ▼
┌──────────────────────────────────────────┐
│ Envio da mensagem para o display         │
│ Service / MQTT                           │
└──────────────────────────────────────────┘
                    │
                    ▼
┌──────────────────────────────────────────┐
│ Exibição da mensagem no display          │
└──────────────────────────────────────────┘
                    │
                    ▼
┌──────────────────────────────────────────┐
│ Remoção da mensagem do display           │
│ após o tempo definido                    │
└──────────────────────────────────────────┘
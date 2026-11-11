# ITTS PDS – Guia do Usuário

O objetivo deste documento é apresentar o módulo **ITTS PDS** e seus componentes.

---

## 1. ITTS PDS

### Introdução
O ITTS PDS (Positioning Detection System) é o modulo ITTS para posicionamento de ativos. Por meio da utilização de tecnologia GNSS de alta precisão é possível monitorar o posicionamento de ativos (RTG, Guindastes, etc) em pátios logísticos. 

### Funcionalidades

- Monitoramento de posicionamento;
- Mapeamento de quadras;
- Registro de eventos de movimentação.

### Requisitos

- Estação Base GNSS;
- Receptor GNSS;
- Tablet/Computador.

### Estação Base GNSS

A estação base GNSS é responsável por coletar as correções dos satélites e transmitir para os receptores GNSS (RTK).

### Receptor GNSS

O receptor GNSS é responsável por receber os sinais dos satélites e as correções da estação base para determinar a posição com precisão centimétrica.

### Tablet/Computador

O tablet ou computador é responsável por executar a aplicação de monitoramento e interface com o usuário.

### Modelo de locais

O modelo de locais representa a estrutura do pátio, composta por Quadras, Colunas e Níveis. Por meio da configuração do modelo de locais o sistema realiza a conversão das coordenadas geográficas para o endereço (slot) do pátio.

### Eventos de movimentação

Representa o registro de movimentação de ativos, sendo:
- Entrada em Quadra;
- Saída de Quadra;
- Mudança de Slot.

### Formato do endereçamento do slot
O endereço do slot é composto por:
Quadra – Coluna – Pilha – Nível

## 2 – Mapeamento de Locais

### Configurando modelo de locais

Para que o sistema realize o endereçamento é necessário realizar o mapeamento das quadras.

**Modelo de locais**
O modelo de locais deve ser configurado no ITTS. Para acessar a configuração do modelo de locais, selecione a opção Meus Itens e em seguida selecione a aba Modelo de Locais.

**Adicionando uma Quadra**
Para adicionar uma nova quadra, selecione o botão Adicionar. Informe os dados da quadra:
- Nome;
- Quantidade de Colunas;
- Quantidade de Pilhas;
- Quantidade de Níveis;
- Largura da Coluna;
- Largura da Pilha;
- Altura do Nível.

**Deslocamento da antena do RTG**
Caso o receptor GNSS não esteja centralizado com o ativo, é necessário configurar o deslocamento (offset) da antena. 

**Recarregando o modelo**
Sempre que houver alteração no modelo de locais é necessário realizar a recarga do modelo no serviço de monitoramento. Para recarregar o modelo, selecione a opção Recarregar Modelo.

## 3 – Site Survey

### Site Survey

**O que é o Site Survey**
O Site Survey é a aplicação utilizada para realizar a coleta das coordenadas geográficas das quadras.

**Instalação**
Para realizar a instalação, execute o arquivo de instalação (setup.exe). Siga as instruções do assistente de instalação:
- Selecione o idioma e clique no botão OK.
- Clique no botão Próximo.
- Selecione a pasta de instalação e clique no botão Próximo.
- Clique no botão Instalar.
- Após a instalação clique no botão Concluir.

**Configurando o Site Survey**
Ao abrir o Site Survey, selecione a opção Configurações.
Informe os dados de configuração:
- Host – Endereço da API do ITTS;
- Login – Usuário de acesso;
- Senha – Senha de acesso.

### Obtendo as coordenadas da Quadra

Para obter as coordenadas da quadra é necessário que o receptor GNSS esteja conectado ao computador e recebendo as correções da estação base.

**Conectando o dispositivo**
Na tela principal, selecione a opção Conectar. Selecione a porta serial do receptor GNSS e clique no botão Conectar.

**Recebendo coordenadas de correção**
Verifique se o receptor GNSS está recebendo as correções da estação base. O status do receptor deve ser RTK Fixed.

**Coletando coordenadas**
Para coletar as coordenadas da quadra, posicione o receptor GNSS em cada um dos cantos da quadra e selecione a opção Coletar Ponto.
Repita o processo para os 4 cantos da quadra.

**Visualizando os dados coletados**
Após coletar os 4 pontos, a quadra será desenhada no mapa.

**Aplicando as configurações**
Para enviar as coordenadas para o ITTS, selecione a opção Enviar Configurações.

## 4 – Monitoramento

### Monitorando Quadras

**Configurando o Monitoramento**
Para realizar o monitoramento das quadras, selecione a opção Monitoramento no menu lateral.
Selecione as quadras que deseja monitorar.

**Realizando o Monitoramento**
Na tela de monitoramento é possível visualizar a posição do ativo em tempo real. O sistema irá destacar a quadra e o slot onde o ativo está posicionado.

## 5 – RTG Tracker Manager

### Introdução
**RTG Tracker Manager**
O RTG Tracker Manager é a aplicação utilizada para configurar e monitorar o serviço de rastreamento de RTG.

### Instalação

Para realizar a instalação, execute o arquivo de instalação (setup.exe). Siga as instruções do assistente de instalação.

### Configurando MQTT

Na tela de configurações, selecione a guia MQTT. Informe os dados do Broker MQTT:
- Host;
- Porta;
- Usuário;
- Senha.

### Configurando Web API

Na guia Web API, informe os dados da API do ITTS:
- Host;
- Login;
- Senha.

## 6 – RTG Tracker Service

### Instalação e Configuração do Serviço

O RTG Tracker Service é o serviço responsável por processar as coordenadas geográficas e gerar os eventos de movimentação.
Abra os Serviços do Windows e localize o serviço Identix Itts RTG Tracker.
Clique com o botão direito no serviço e selecione a opção Propriedades.
Na aba Recuperação marque as ações de recuperação de falha.
Isso irá garantir que o serviço sempre seja reiniciado em caso de alguma falha.
Para iniciar ou parar o serviço, basta utilizar o botão direito sobre o serviço escolher uma das opções.
O log do serviço poderá ser visualizado em um arquivo de log localizado na pasta Logs.

### Conectividade com a plataforma ITTS

O RTG Tracker Service implementa um cliente MQTT para estabelecer conectividade com a plataforma ITTS para:
- Recepção de coordenadas no formato NMEA;
- Recepção de comandos;
- Enviar eventos de posição e movimentação;
- Enviar eventos de heartbeat.

O modelo de dados das quadras é descarregado por meio da consulta a API RestFull.
As configurações de conectividade devem ser realizadas por meio do aplicativo Tracker Manager.

### Recepção de comandos

O RTG Tracker Service implementa suporte para processamento de comandos enviados via MQTT para o tópico command. Os seguintes comandos são suportados:
- get_model – Ao receber este comando o RTG Tracker Service carrega o modelo de dados por meio da consulta a API RestFull. Exemplo de payload: { "get_model" : {}}
- set_offset – Ao receber este comando o RTG Tracker Service calcula o deslocamento entre a posição da antena e a quadra. Exemplo de payload: {"set_offset" : {"zone":"zone_name"}}
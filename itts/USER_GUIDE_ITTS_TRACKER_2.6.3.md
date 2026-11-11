# ITTS Tracker – Guia do Usuário

Este documento apresenta o aplicativo **ITTS Tracker** e seus componentes.

---


## 1. Introdução ao Tracker

Tracker é uma ferramenta de coleta de dados de telemetria e geolocalização para fins de rastreabilidade com integração com a plataforma ITTS. Os dados podem ser coletados com o auxílio do dispositivo periférico BlueLink.

**BlueLink** é um pequeno dispositivo BLE capaz de conectar-se ao barramento CAN (Controller Area Network) do veículo (J1939, gateway FMS) e/ou J1708 Bus (J1587) usando cabo WLI JBus para expor os parâmetros recebidos do veículo, via serviços BLE.

## 2. Arquitetura

A aplicação foi desenvolvida utilizando-se a tecnologia .NET Framework 4.8 e está dividida nos seguintes componentes:

- **Tracker Manager** \- Aplicação de configuração e monitoramento;
- **Tracker Service -** Serviço de coleta e processamento de dados.

## 3. Instalação

### 3.1. Tracker Manager

O Tracker Manager é a ferramenta de configuração e monitoramento. Permite configurar a conectividade com a plataforma ITTS, os modos de operação e monitoramento do log do serviço.

1. Para a instalação, execute o arquivo instalador.
2. Selecione o botão **Avançar**.
3. Selecione a pasta de instalação e clique no botão **Avançar**.
4. Confirme a instalação clicando no botão **Avançar.**
5. Após a instalação clique no botão **Fechar**.

### 3.2. Tracker Service

O Tracker Service é responsável pela captura, processamento e envio dos dados para a plataforma ITTS.

1. Para a instalação, execute o arquivo instalador.
2. Selecione o botão **Avançar**.
3. Selecione a pasta de instalação e clique no botão **Avançar**.
4. Confirme a instalação clicando no botão **Avançar.**
5. Após a instalação clique no botão **Fechar**.

Antes de iniciar o serviço, realize todas as configurações utilizando **Tracker Manager**.

Para iniciar o serviço, abra o gerenciador de serviços do Windows e localize **Identix Itts Tracker**. Clique com o botão direito sobre o serviço e selecione **Iniciar**.

Opcionalmente você poderá configurar o serviço para reiniciar automaticamente caso ocorra alguma falha. Para isso configure as seguintes opções de recuperação do serviço.

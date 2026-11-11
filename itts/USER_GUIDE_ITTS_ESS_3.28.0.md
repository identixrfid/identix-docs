# ITTS ESS – Guia do Usuário

O objetivo deste documento é apresentar o módulo **ITTS ESS** e seus componentes.

## 1. Introdução

### Introdução
**ITTS ESS**
ESS (Electronic Seals Security System) é o modulo ITTS para Controle e Rastreabilidade de Lacres Eletrônicos.

### Funcionalidades:
- Registro e identificação de Lacres.
- Pontos de Leitura;
- Eventos de Lacre.

### Requisitos:
- Leitor RFID IMPINJ R220/R420;
- Gateway RFID Cassia X1000/E1000.

### Lacres
Representa o lacre físico que será monitorado. Cada lacre deverá ser identificado no sistema com as seguintes informações:
- Nome ou descrição;
- EPC;
- Chave de Segurança.

### Pontos de Leitura
Os pontos de leitura são locais configurados com leitores RFID para identificação de lacres.

### Eventos de Lacres
Representa o registro de identificação de lacres, sendo:
- Integridade (lacre fechado);
- Violação (lacre aberto).

## Autenticação

### Conectando-se a interface do sistema
Aponte seu navegador para a tela de autenticação do sistema.
Na tela de autenticação, informe os dados de acesso do usuário cadastrado.
Após informar seus dados de acesso, selecione o botão **Entrar** para realizar o login no sistema.
Se seus dados estiverem corretos a **Tela Inicial** do sistema será apresentada.

## Acessando o Módulo
Os módulos disponíveis estarão visíveis com uma cor destacada na parte superior da tela principal.
Após o login, na tela inicial, selecione o módulo ESS.
Ao acessar o módulo as funcionalidades disponíveis serão apresentadas.

## Vinculando Identificadores
Para que um lacre possa ser monitorado é necessário associar identificadores.
Para editar os identificadores, na lista de lacres, selecione a opção **Editar**.
Na parte inferior da tela serão apresentados os identificadores associados ao lacre:
- Selecione o tipo de identificador RFID;
- Selecione o modelo do identificador;
- Preencha o EPC de 96 bits de acordo com o tipo de identificador selecionado;
- Informe a chave de segurança (TID), disponível para identificadores RFID;
- Clique no botão **Adicionar**.

Se você tiver um leitor RFID configurado poderá fazer a leitura da etiqueta de RFID utilizando o botão **Ler Etiqueta RFID**.

> Importante:
O leitor RFID configurado para ser utilizado para registrar os identificadores deverá enviar os dados para o tópico “read”, exemplo: abcd/devicer420/read.
Para configurar um dispositivo de leitura, navegue até a tela **Meus Dispositivos**, localize o dispositivo desejado, selecione a opção **Ações** e em seguida selecione a opção **Definir como Padrão**.

## Configurando Pontos de Leitura

### Adicionando um Ponto de Leitura
Um ponto de leitura requer a configuração de locais e dispositivos.
Na página **Home**, selecione a opção **Pontos de Leitura** disponível no menu lateral ou no painel central.
Ao acessar a página os pontos de leituras já registrados serão apresentados.
Seleciona o botão **Adicionar** para incluir um novo ponto de leitura.
Forneça as informações básicas:
- **Nome** – Descritivo e único.
- **Módulo** – Electronic Seals Security.
- **Operação** – Monitoramento de Localização.
- **Ativo** – Habilita ou desabilita o ponto de monitoramento.
Informe os dados e selecione a opção **Salvar**.

### Configurando um Ponto de Leitura
Após a configuração dos locais e dispositivos, selecione a aba **Pontos de Leitura**. Selecione o botão de **Ações** e em seguida a opção **Editar**.
Adicione o Dispositivo de Leitura:
- **Dispositivo** – Leitor desejado.
- **Local** – Local mapeado no sistema.
- **Direção** – Nenhuma.
- **Antenas** – Antenas que farão a leitura do local desejado.

Para registrar um novo local no ITTS, selecione o menu **Minha Empresa**, em seguida, selecione a aba **Locais**.
Note que além do local é necessário vincular ao local o leitor RFID ou Gateway que fará as leituras.

## Visualizando os Eventos

### Visualizando os eventos de lacre
Para visualizar os eventos de lacres, selecione a opção **Histórico**.
Em seguida navegue até a aba **Histórico de Lacres**. O relatório de eventos será apresentado.
O grid deverá apresentar os seguintes dados:
- **Nome ou Descrição** – Campo descritivo do lacre;
- **Identificador** – EPC;
- **Registro** – Data e Hora do registro no sistema;
- **Evento** – Integridade ou Violação.

## 2 - Tag Activator

### Introdução
**ITTS Tag Activator**
O ITTS Tag Activator é uma aplicação Android utilizada para a ativação de lacres eletrônicos. Através da leitura do QR Code do lacre, a aplicação realiza a associação do EPC e Chave de Segurança (TID) ao item no sistema ITTS.

### Instalação
Para realizar a instalação, copie o arquivo de instalação (.apk) para o seu dispositivo Android.
- Selecione o arquivo para iniciar a instalação.
- Se solicitado, permita a instalação de fontes desconhecidas.
- Clique no botão **Instalar**.
- Após a instalação clique no botão **Concluído** ou **Abrir**.

### Acessando o Tag Activator
Após concluir a instalação abra o aplicativo, a tela inicial será exibida.

### Configurando Tag Activator
Na tela inicial, selecione a opção **Configurar** para que a janela de configurações seja exibida:
Informe os dados de configuração:
- **Host** – Endereço da API do módulo ESS (host/api/itts);
- **Login** – API ClientId da aplicação;
- **Senha** – Senha da aplicação.
Note que é necessário a configuração de um aplicativo da tela integrações do ITTS.
Salve os dados para concluir a configuração.

### Ativando um lacre
Na tela principal, realize a leitura do QrCode com a câmera do dispositivo.
Após a leitura do QrCode selecione a opção **Ativar Tag** para processar a ativação.
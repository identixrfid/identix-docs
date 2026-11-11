# ITTS AMS – Guia do Usuário

O objetivo deste documento é apresentar o módulo **ITTS AMS** e seus componentes.

---

## 1. Introdução

### Introdução
**ITTS AMS**
AMS (Attendance Monitoring System) é o modulo ITTS para Monitoramento de Presença de Pessoas.

### Funcionalidades
- Registro e identificação de Pessoas.
- Pontos de Monitoramento;
- Eventos de Identificação de Entrada e Saída de Pessoas.

### Requisitos
- Leitor RFID IMPINJ xArray.

### Pessoa
Representa uma pessoa que será monitorada. Cada pessoa deverá ser identificada no sistema com as seguintes informações:
- Nome ou descrição;
- EPC;
- Chave de Segurança.

### Pontos de Leitura
Os pontos de leitura são locais configurados com leitores RFID para identificação de pessoas.

### Eventos de Pessoas
Representa o registro de identificação de pessoas, sendo:
- Entrada;
- Saída.

Os eventos de identificação podem ser gerados com base em dois tipos de operação:
1. **Monitoramento de Localização - Identificação simples:** evento é gerado com base na leitura da pessoa em um ponto de leitura.
2. **Monitoramento de Entrada e Saída – Transição:** evento é gerado quando uma pessoa realiza a transição entre locais mapeados em um ponto de leitura. Requer múltiplas leituras em ambos os sentidos (entrada e saída).

## Autenticação

### Conectando-se a interface do sistema
Aponte seu navegador para a tela de autenticação do sistema.
Na tela de autenticação, informe os dados de acesso do usuário cadastrado.
Após informar seus dados de acesso, selecione o botão **Entrar** para realizar o login no sistema.
Se seus dados estiverem corretos a **Tela Inicial** do sistema será apresentada.

## Acessando o Módulo
Os módulos disponíveis estarão visíveis com uma cor destacada na parte superior da tela principal.
Após o login, na tela inicial, selecione o módulo AMS.
Ao acessar o módulo as funcionalidades disponíveis serão apresentadas.

## Adicionando Pessoas
Para adicionar uma nova pessoa, acesse a página inicial do ITTS e no menu lateral, selecione a opção **Meus Itens**.
Os itens serão apresentados, selecione a opção **Monitoramento de Presença** no filtro do módulo para ver todos os itens cadastrados para o módulo AMS (Monitoramento de Presença).
Selecione o botão **Adicionar** para incluir uma nova pessoa.
Informe os dados da pessoa e clique no botão **Salvar**.

## Vinculando Identificadores
Para que uma pessoa possa ser monitorada é necessário associar identificadores.
Para editar os identificadores, na lista de pessoas, selecione a opção **Editar**.
Na parte inferior da tela serão apresentados os identificadores associados a pessoa:
- Selecione o tipo de identificador RFID;
- Selecione o modelo do identificador;
- Preencha o EPC de 96 bits de acordo com o tipo de identificador selecionado;
- Informe a chave de segurança (TID), disponível para identificadores RFID;
- Clique no botão **Adicionar**.

Se você tiver um leitor RFID configurado poderá fazer a leitura da etiqueta de RFID utilizando o botão **Ler Etiqueta RFID**.

> Importante
O leitor RFID configurado para ser utilizado para registrar os identificadores deverá enviar os dados para o tópico “read”, exemplo: abcd/devicer420/read.

Para configurar um dispositivo de leitura, navegue até a tela **Meus Dispositivos**, localize o dispositivo desejado, selecione a opção **Ações** e em seguida selecione a opção **Definir como Padrão**.

## Configurando Pontos de Leitura

### Adicionando um Ponto de Leitura
Um ponto de leitura requer a configuração de locais e dispositivos.
A configuração do ponto de leitura é diferente de acordo com o tipo de operação desejada.
Na página **Home**, selecione a opção **Pontos de Leitura** disponível no menu lateral ou no painel central.
Ao acessar a página os pontos de leituras já registrados serão apresentados.
Seleciona o botão **Adicionar** para incluir um novo ponto de leitura.
Forneça as informações básicas:
* **Nome** – Descritivo e único.
* **Módulo** – Monitoramento de Presença.
* **Operação** – Monitoramento de Entrada e Saída ou Monitoramento de Localização.
* **Ativo** – Habilita ou desabilita o ponto de monitoramento.
Informe os dados e selecione a opção **Salvar**.

### Configurando um Ponto de Leitura para Operação
Após a configuração dos locais e dispositivos, selecione a aba **Pontos de Leitura**. Selecione o botão de **Ações** e em seguida a opção **Editar**.

Para **Monitoramento de Entrada e Saída**, adicione o Dispositivo de Leitura:
- **Dispositivo** – Leitor desejado.
- **Local** – Local mapeado no sistema.
- **Direção** – Entrada ou saída.
- **Antenas** – Antenas que farão a leitura na direção informada.

Para **Monitoramento de Localização**, adicione o Dispositivo de Leitura:
- **Dispositivo** – Leitor desejado.
- **Local** – Local mapeado no sistema.
- **Direção** – Nenhuma.
- **Antenas** – Antenas que farão a leitura do local desejado.

Para registrar um novo local, selecione o menu **Minha Empresa** e a aba **Locais**. É necessário vincular ao local o leitor RFID ou Gateway (atualmente apenas o leitor IMPINJ xArray é suportado).

## Visualizando os Eventos

### Visualizando Eventos de Entrada e Saída
Selecione a opção **Histórico** e navegue até a aba **Histórico de Presença**. O grid apresentará:
- **Nome ou Descrição** – Campo descritivo da pessoa;
- **Identificador** – EPC;
- **Registro** – Data e Hora;
- **Etapa** – Entrada ou saída.

### Visualizando Eventos de Localização
Selecione a opção **Histórico** e navegue até a aba **Histórico de Localização**. O grid apresentará:
- **Nome ou Descrição** – Campo descritivo da pessoa;
- **Identificador** – EPC;
- **Registro** – Data e Hora;
- **Local** – Local mapeado no sistema.
# ITTS Mobile – Guia do Usuário

O objetivo deste documento é apresentar o aplicativo **ITTS Mobile** e seus componentes.

---

## 1 – Introdução

### 1.1 – Introdução

**1.1.1 – ITTS Mobile**
O ITTS Mobile é o aplicativo coletor de dados da plataforma ITTS para rastreabilidade de itens com etiquetas RFID UHF. Com ele, o operador cadastra, consulta, movimenta e confere itens diretamente no local da operação. Todas as operações são registradas na plataforma ITTS.

### 1.2 – Funcionalidades:
- Cadastro de Item
- Consulta de Item
- Movimentação de itens (Avulsa, por Atividade e por Ordem de Produção)
- Substituição de Etiqueta
- Embarque (Criação e Conferência de Embarque)
- Conferência por Local
- Coleta de Dados
- Localizador RFID
- Gravação de Etiqueta
- Configurações, Personalização e Atualização do app

### 1.3 – Requisitos:
- Coletor Urovo DT50P com leitor RFID UHF e leitor de código de barras integrados;
- Sistema Android;
- Conexão de rede (Wi-Fi ou dados móveis) com acesso ao servidor da plataforma ITTS;
- Usuário e senha de acesso (aplicativo de negócios) à plataforma ITTS;

### 1.4 – Cadastro de Item
Registro de novos itens na plataforma, com leitura do EPC da etiqueta RFID e preenchimento das informações do grupo.

### 1.5 – Consulta de Item
Consulta dos dados de um item a partir do EPC da etiqueta: descrição, grupo, status, etapa, local e imagem.

### 1.6 – Movimentação
Registro de eventos de movimentação dos itens lidos, informando a etapa e o local de destino.

### 1.7 – Substituir Etiqueta
Troca da etiqueta RFID de um item já cadastrado, mantendo o histórico do item.

### 1.8 – Embarque
Criação de embarques com seus pedidos e conferência dos produtos embarcados por leitura RFID.

### 1.9 – Conferência por Local
Verificação, por leitura RFID, dos itens que a plataforma registra em um determinado local.

### 1.10 – Coleta de Dados
Captura das leituras RFID para análise técnica, com exportação das leituras em arquivo.

### 1.11 – Localizador RFID
Localização física de um item pela intensidade do sinal da sua etiqueta. A etiqueta procurada pode ser informada pela ordem, pelo EPC ou pela lista de itens das telas de conferência.

### 1.12 – Gravação de Etiqueta
Gravação de um novo EPC em uma etiqueta RFID.

### 1.13 – Acessando o Aplicativo
Ao abrir o app, a tela de abertura é apresentada por alguns segundos. Em seguida, a tela inicial apresenta o nome do app, a versão instalada e um botão para cada funcionalidade habilitada.
O botão **"Configurações"** fica sempre disponível no fim da tela inicial.

> **Importante:** Na primeira utilização, configure o acesso à plataforma em **Configurações** antes de utilizar as funcionalidades (ver seção 2.2).

As funcionalidades visíveis na tela inicial podem ser escolhidas na tela **Personalizar** (ver seção 2.4).

---

## 2. Configurações

### 2.1 – Configurações

Para acessar, selecione a opção **"Configurações"** na tela inicial. A tela apresenta quatro áreas:
- Acesso a WebAPI;
- Configurações RFID;
- Personalizar;
- Atualização do app.

### 2.2 – Acesso a WebAPI

Permite informar os dados de acesso à plataforma ITTS.

Informe os dados obrigatórios:
- **Host** – Endereço do servidor da plataforma (exemplo: `https://ittsh.synergy.com.br`);
- **Login** – Usuário de acesso à plataforma;
- **Senha** – Senha do usuário.

Selecione a opção **"Salvar"**. O app valida os dados com o servidor antes de gravá-los:
- Em caso de sucesso, a mensagem **"Configuração salva com sucesso!"** será apresentada;
- Em caso de falha, a mensagem **"Credenciais inválidas ou API indisponível."** será apresentada e os dados não serão gravados.

> **Dica:** Se alguma tela apresentar o alerta **"Sem conexão com a API"**, utilize o botão **"Ir para Configurações"** do alerta para revisar os dados de acesso.

### 2.3 – Configurações RFID

Define a potência padrão do leitor RFID, utilizada em todas as leituras do app.

1. Selecione a opção **"Configurações RFID"**;
2. Ajuste a potência no controle deslizante, de 1 dBm a 33 dBm (padrão: 30 dBm);
3. Selecione a opção **"Salvar"**.

Mensagens apresentadas:
- **"Potência salva e aplicada ao leitor."** – a nova potência já está em uso;
- **"Potência salva. Será aplicada na próxima leitura RFID."** – a potência será aplicada quando o leitor for iniciado.

> **Nota:** Várias telas de leitura possuem um controle deslizante de potência próprio. Esse ajuste vale apenas enquanto a tela estiver aberta. Ao abrir a tela novamente, a potência volta ao valor definido em Configurações RFID.

### 2.4 – Personalizar

Permite escolher o que aparece no app e configurar parâmetros de integração. Selecione a opção **"Personalizar"** em Configurações.

A tela é dividida nas seções:

**2.4.1 – Funcionalidades**
Marque as funcionalidades que aparecerão na tela inicial. Para as funcionalidades com submenu (Movimentação e Embarque):
- Marcar o item principal marca todas as suas opções;
- Desmarcar o item principal desmarca todas as suas opções;
- Marcar uma opção marca também o item principal;
- Desmarcar a última opção desmarca o item principal.

Deve haver pelo menos uma funcionalidade marcada.

**2.4.2 – Local inicial (Cadastro de Item)**
Na linha do Cadastro de Item, é possível definir:
- **Local inicial** – local padrão do evento gerado no cadastro do item. Utilize o ✕ para deixar sem local padrão;
- **Permitir alterar o local no cadastro** – quando marcado, o operador pode trocar o local no cadastro e o app começa pelo último local usado. Quando desmarcado, o cadastro usa sempre o local padrão (ou nenhum local, se não houver padrão), sem opção de troca.

**2.4.3 – Etapas**
Define as etapas apresentadas no campo **"ETAPA"** da Movimentação. A seção possui campo de busca e as opções **"Marcar todas"** e **"Desmarcar todas"**. Deve haver pelo menos uma etapa marcada.

**2.4.4 – Integração**
- **Identificador do Modelo da Atividade** – código do modelo de atividade usado ao salvar a Conferência por Local. Esse código é fornecido pelo responsável pelo sistema.

> **Atenção:** O modelo de atividade informado deve estar cadastrado na plataforma **sem "Nova etapa"**. Caso contrário, salvar a conferência movimentará os itens lidos.

**2.4.5 – Grupos**
Apresenta a situação da personalização dos campos por grupo, definida na plataforma web (tela "Configuração de Grupos - Mobile"). Essa personalização define a ordem, os rótulos e a visibilidade dos campos do Cadastro de Item e as colunas da Conferência por Local.
- Selecione **"Atualizar personalização dos grupos"** para baixar a configuração mais recente;
- A data da última atualização é apresentada na seção (**"Atualizado em ..."**).

> **Importante:** O app não atualiza essa personalização automaticamente. Sempre que a configuração for alterada na plataforma, selecione **"Atualizar personalização dos grupos"** no coletor. Em caso de falha, a personalização anterior é mantida.

**2.4.6 – Rodapé**
- **Salvar** – grava as alterações. As mudanças valem ao retornar à tela inicial;
- **Restaurar padrão** – reaplica a configuração inicial: todas as funcionalidades e etapas, sem modelo de atividade e sem local padrão.

### 2.5 – Atualização do app

Permite instalar a versão mais recente do ITTS Mobile.

1. Na tela Configurações, na área **"Atualização do app"**, a versão instalada é apresentada;
2. Selecione a opção **"Verificar atualização"**;
3. Se houver uma versão mais nova, o app pergunta se deseja baixar e instalar. Confirme para iniciar o download. O progresso é apresentado na tela e o download pode ser interrompido com **"Cancelar download"**;
4. Ao final do download, confirme a instalação na tela do Android.

Se o app já estiver atualizado, a mensagem **"Você já está na versão mais recente"** será apresentada.

> **Permissão necessária:** Na primeira atualização, o Android pode solicitar a permissão para que o ITTS instale apps. Conceda a permissão, volte ao app e selecione novamente **"Verificar atualização"**.

---

## 3. Itens

### 3.1 – Cadastro de Item

Para acessar, selecione a opção **"Cadastro de Item"** na tela inicial.

**3.1.1 – Cadastrando um item**
1. Informe o **Grupo de Item**. Há duas formas:
   - Digite parte do nome no campo de busca e selecione o grupo na lista;
   - Com o campo de busca em foco, leia o código de barras do produto. O app localiza o grupo pelo SKU.
2. Confira a **Descrição**. O campo é preenchido com o nome do grupo e pode ser alterado (de 3 a 100 caracteres);
3. Leia o **EPC** da etiqueta pelo leitor RFID (botão de leitura ou gatilho) ou digite o EPC manualmente;
4. Preencha as **Informações do Grupo**, que são os campos específicos do grupo selecionado (ver seção 3.1.4);
5. Se for o caso, preencha os campos opcionais: **Ordem**, **Alias**, **Lote**, **Fabricação**, **Validade** e **Local esperado**;
6. Confira o **Local inicial (opcional)**, no fim da tela;
7. Selecione a opção **"Salvar"**.

Em caso de sucesso, uma mensagem de confirmação será apresentada. Em caso de erro, a mensagem indicará o campo ou o motivo da falha.

Para recomeçar o preenchimento, selecione a opção **"Limpar"**. O Local inicial é mantido, para facilitar o cadastro de vários itens no mesmo local; para cadastrar sem local, utilize o ✕ ao lado do campo.

> **Dica:** A leitura do código de barras sempre preenche o **campo de texto em foco**. Para preencher um campo pelo scanner, toque no campo e, em seguida, faça a leitura. Se nenhum campo de texto estiver em foco, a leitura é ignorada.

**3.1.2 – Grupo pelo código de barras**
- A leitura só localiza o grupo quando o campo Grupo está vazio. Para trocar o grupo, utilize o ✕ ou a opção **"Limpar"**;
- Se o código não corresponder a nenhum grupo, um aviso orienta a seleção manual;
- Se mais de um grupo tiver o mesmo SKU, os grupos são apresentados na lista para que o operador escolha.

**3.1.3 – Campos obrigatórios e opcionais**
- **Grupo** – Obrigatório;
- **Descrição** – Obrigatória, de 3 a 100 caracteres;
- **EPC** – Obrigatório;
- **Ordem** – Opcional, até 20 caracteres. Corresponde ao código do pedido;
- **Alias** – Opcional, de 3 a 30 caracteres;
- **Lote** – Opcional, até 30 caracteres;
- **Fabricação** e **Validade** – Opcionais. A validade não pode ser anterior à fabricação;
- **Local esperado** – Opcional. Local onde o item deve ficar;
- **Local inicial** – Opcional. Local onde o item está no momento do cadastro.

> **Nota:** Os campos Alias, Lote, Fabricação, Validade e Local esperado só aparecem quando estão habilitados na personalização do grupo, na plataforma.

**3.1.4 – Campos do grupo**
Após a escolha do grupo, o app carrega os campos configurados para ele na plataforma. Os tipos de campo suportados são:
- Texto curto, texto longo e link;
- Número;
- Valor monetário – preenchido da direita para a esquerda; os dois últimos dígitos são os centavos (ex.: `123` vira `1,23`);
- CPF e CNPJ – formatados ao sair do campo;
- Lista de opção única e Estado (UF);
- Múltipla escolha;
- Sim/Não;
- Data – vazia até que seja selecionada pela opção **"Selecionar data"**. O ✕ limpa a data.

Campos obrigatórios não preenchidos são indicados com a mensagem **"Informe o campo {Nome}"**. Todos os campos são validados ao salvar, para que todas as correções sejam feitas de uma só vez.

> **Importante:** Um campo de tipo não suportado pelo coletor aparece em cinza com a indicação "tipo não suportado no coletor". Se esse campo for obrigatório, o item deve ser cadastrado pela plataforma web.

Se a carga dos campos do grupo falhar, um aviso vermelho será apresentado e o cadastro ficará bloqueado. Toque no aviso para tentar novamente.

**3.1.5 – Testando a etiqueta**
Após preencher o EPC, é possível verificar se a etiqueta está sendo lida corretamente:
1. Selecione a opção **"Testar Tag"**;
2. Posicione-se a aproximadamente 1 metro da etiqueta;
3. Selecione a opção **"Iniciar teste"**;
4. O app tenta ler a etiqueta por até 3 segundos e apresenta o resultado.

Para repetir o teste, selecione **"Testar novamente"**. Os dados já preenchidos no formulário não são alterados pelo teste.

**3.1.6 – Potência de leitura**
O controle deslizante de potência da tela vale apenas para a leitura do EPC. O teste da etiqueta utiliza sempre uma potência fixa.

### 3.2 – Consultar Item

Para acessar, selecione a opção **"Consultar Item"** na tela inicial.

**3.2.1 – Consultando um item**
1. Informe o EPC do item:
   - Selecione **"Ler RFID"** ou pressione o gatilho, aproximando a etiqueta do coletor. A primeira etiqueta lida preenche o campo; ou
   - Digite o EPC e confirme pelo teclado.
2. A consulta é executada automaticamente e os dados do item são apresentados.

As informações apresentadas são:
- Grupo;
- Descrição;
- Código;
- EPC;
- Peso;
- Status – situação atual do item (ex.: Criado, Ativo, Em Estoque);
- Etapa – etapa atual do item (ex.: Criação, Armazenamento, Expedição);
- Local – local atual do item;
- Imagem – imagem do item, quando cadastrada.

> **Nota:** O campo Local vazio indica um item cadastrado sem local e que ainda não foi movimentado.

Se o EPC não estiver cadastrado, uma mensagem informará que o item não foi encontrado. Para uma nova consulta, selecione a opção **"Limpar"**.

### 3.3 – Substituir Etiqueta

Utilizada quando a etiqueta de um item cadastrado está danificada ou precisa ser trocada. A plataforma passa a reconhecer o item pela nova etiqueta.

Para acessar, selecione a opção **"Substituir Etiqueta"** na tela inicial.

1. Em **EPC Atual**, selecione **"Ler RFID"** e leia a etiqueta antiga, ou digite o EPC;
2. Em **Novo EPC**, selecione **"Ler RFID"** e leia a etiqueta nova, ou digite o EPC;
3. Selecione a opção **"Substituir"**.

Regras:
- Os dois EPCs são obrigatórios;
- O novo EPC deve ser diferente do EPC atual;
- Se a etiqueta antiga não estiver cadastrada, a mensagem **"EPC da etiqueta antiga não encontrado."** será apresentada.

Para reiniciar a operação, selecione a opção **"Limpar"**.

> **Importante:** A Substituir Etiqueta atualiza a plataforma, mas não grava nada na etiqueta. Para gravar um EPC em uma etiqueta, utilize a **Gravação de Etiqueta** (seção 9.1).

---

## 4. Movimentação

### 4.1 – Movimentação

Permite registrar a movimentação de itens para uma etapa e um local. Para acessar, selecione a opção **"Movimentação"** na tela inicial e escolha o tipo:

- **Avulsos** – movimentação livre dos itens lidos;
- **Atividade** – execução de uma atividade liberada na plataforma;
- **Ordem de Produção** – movimentação dos itens de uma ordem.

### 4.2 – Movimentação Avulsa

1. Selecione a opção **"Avulsos"**;
2. Inicie a leitura pelo botão da tela ou pelo gatilho. Cada etiqueta lida é incluída em **EPCS IDENTIFICADOS**, sem repetição, e o contador **Itens lidos** é atualizado;
3. Selecione a opção **"MOVIMENTAR"** (é necessário pelo menos um item lido);
4. Na tela **Dados da Movimentação**, informe a **ETAPA** e o **LOCAL** de destino e selecione **"Continuar"**;
5. Na tela **Confirmar Movimentação**, revise o tipo, a etapa, o local e o total de EPCs;
6. Selecione a opção **"Confirmar Movimentação"**. Para corrigir os dados, selecione **"Voltar"**.

Ao final, a tela **Resultado da Movimentação** apresenta o resultado da operação. Selecione **"Voltar ao início"** para retornar à tela inicial.

> **Nota:** As etapas apresentadas no campo ETAPA são as habilitadas em Configurações › Personalizar › Etapas.

### 4.3 – Movimentação por Atividade

As atividades são criadas e liberadas na plataforma. O modelo da atividade define a etapa e o local da movimentação.

1. Selecione a opção **"Atividade"**. A lista de atividades liberadas será apresentada, com a data agendada. Utilize **"ATUALIZAR"** para recarregar a lista;
2. Selecione a atividade desejada;
3. Na tela **Leitura da Atividade**, realize a leitura dos itens. A data e hora da primeira leitura são registradas como início da atividade;
4. Selecione a opção **"FINALIZAR"** (é necessário pelo menos um item lido);
5. Na tela **Confirmar Movimentação**, revise a atividade, a OP e o total de EPCs;
6. Selecione a opção **"Confirmar Movimentação"**.

Ao confirmar, a atividade é concluída na plataforma com os itens lidos.

### 4.4 – Movimentação por Ordem de Produção

1. Selecione a opção **"Ordem de Produção"**;
2. Informe o **número da Ordem de Produção** e selecione **"Obter"**. Se a ordem não existir ou não tiver itens, uma mensagem será apresentada;
3. A tela apresenta os itens esperados da ordem, com o **STATUS**, a **DESCRIÇÃO** e o **EPC**, além dos contadores **Total esperado** e **Itens lidos**;
4. Selecione **"INICIAR"** (ou pressione o gatilho) e leia as etiquetas. Cada item esperado lido é marcado como lido. Selecione **"PARAR"** para interromper a leitura;
5. Selecione a opção **"Continuar"** (é necessário pelo menos um item lido);
6. Na tela **Dados da Movimentação**, informe a **ETAPA** e o **LOCAL** e selecione **"Continuar"**;
7. Na tela **Confirmar Movimentação**, revise o total esperado, os itens lidos e os pendentes;
8. Selecione a opção **"Confirmar Movimentação"**.

Regras:
- Etiquetas que não pertencem à ordem são ignoradas e não são movimentadas;
- É possível confirmar com itens pendentes. Nesse caso, a mensagem **"A movimentação será confirmada parcialmente."** será apresentada e somente os itens lidos serão movimentados.

**4.4.1 – Localizando um item da ordem**
Com a leitura parada, toque na linha do item para localizá-lo pelo **Localizador RFID** (ver seção 8.1.4). Ao retornar, os itens já lidos são mantidos.

---

## 5. Embarque

### 5.1 – Embarque

Um embarque é composto por um número e uma lista de pedidos. Cada pedido representa um grupo de produtos e a quantidade esperada.

Para acessar, selecione a opção **"Embarque"** na tela inicial e escolha a operação:
- **Criar novo embarque**;
- **Conferência de Embarque**.

### 5.2 – Criar novo embarque

1. Selecione a opção **"Criar novo embarque"**;
2. Informe o **Número do Embarque**;
3. Selecione a opção **"+ Adicionar Pedido"**. A janela **Adicionar Pedido** será apresentada;
4. Informe o **Grupo do Produto** (digite para filtrar e selecione o grupo) e a **Quantidade** esperada;
5. Selecione a opção **"Incluir"**. O pedido será incluído na lista **PEDIDOS**;
6. Repita os passos 3 a 5 para cada pedido;
7. Selecione a opção **"Salvar Embarque"**.

A tela **Resultado do Embarque** apresenta o resultado. Selecione **"Concluir"** para retornar à tela inicial ou **"Conferir embarque"** para iniciar a conferência do embarque criado, com o número já preenchido.

Regras do pedido:
- O grupo é obrigatório e deve ter SKU cadastrado na plataforma;
- A quantidade deve ser um número inteiro maior que zero;
- O mesmo grupo não pode ser incluído duas vezes no embarque.

Regras do embarque:
- O número do embarque é obrigatório;
- O embarque deve ter pelo menos um pedido.

**5.2.1 – Removendo um pedido**
Toque duas vezes no pedido desejado e confirme a remoção.

Para descartar o embarque em montagem, selecione a opção **"Cancelar"**.

### 5.3 – Conferência de Embarque

Permite conferir fisicamente, por leitura RFID, os produtos de um embarque registrado e salvar o resultado.

**5.3.1 – Localizando o embarque**
1. Selecione a opção **"Conferência de Embarque"**;
2. Informe o **Número do Embarque** e selecione **"Pesquisar"**;
3. Se o embarque for encontrado, um cartão com o número, a situação, a **Quantidade total** e o **Destino** será apresentado. Selecione **"Abrir Embarque"**.

Se o embarque não for encontrado, a mensagem **"Embarque não encontrado."** será apresentada. Utilize **"Limpar"** para iniciar uma nova pesquisa.

> **Importante:** Um embarque Concluído ou Cancelado é aberto somente para consulta. Nesse caso, não é possível realizar leituras nem salvar.

**5.3.2 – Conferindo os produtos**
A tela apresenta os pedidos do embarque com as colunas:
- **Grupo** – grupo do produto;
- **Esperado** – quantidade esperada;
- **Conferido** – quantidade lida.

1. Selecione **"Iniciar leitura"** ou pressione o gatilho;
2. A cada etiqueta válida lida, o valor **Conferido** do grupo correspondente é atualizado;
3. Selecione **"Pausar leitura"** para conferir os números na tela. Nada do que já foi conferido é perdido.

A linha fica **verde** quando a quantidade conferida é igual à esperada e **amarela** quando ultrapassa a esperada. Uma mesma etiqueta nunca é contada duas vezes. Os totais **Total esperado** e **Total conferido** são apresentados no rodapé.

Durante a leitura, as mensagens abaixo podem ser apresentadas:
- **Item não registrado** – a etiqueta não está cadastrada no sistema;
- **Não esperado** – o produto está cadastrado, mas pertence a um grupo que não faz parte do embarque;
- **Falha de conexão ao validar a leitura** – o coletor está sem comunicação com o servidor.

**5.3.3 – Linha "Não esperado"**
Os produtos cadastrados que não pertencem ao embarque são somados na linha **Não esperado**, destacada em amarelo. Essa linha só aparece após a primeira leitura desse tipo e serve apenas como contagem: esses itens não entram na conferência salva.

**5.3.4 – Finalizando a conferência**
- **Salvar Conferência** – registra a conferência com os itens conferidos;
- **Reiniciar** – zera os contadores e as leituras, mantendo o embarque aberto;
- **Cancelar** – descarta a conferência e retorna à pesquisa.

Ao selecionar **"Salvar Conferência"**:
1. Se houver divergência entre o conferido e o esperado, os grupos divergentes serão listados e o app perguntará se deseja continuar. É possível voltar e ler novamente ou confirmar assim mesmo;
2. A conferência é registrada e a tela **Resultado da Conferência** apresenta o número do embarque e o total de itens conferidos;
3. Selecione **"Concluir"** para retornar à tela inicial.

> **Importante:** É necessário ter pelo menos um item conferido para salvar. Ao salvar, os itens conferidos são registrados na etapa **Expedição**, vinculados ao número do embarque.

---

## 6. Conferência por Local

### 6.1 – Conferência por Local

Permite verificar, por leitura RFID, se os itens que a plataforma registra em um local estão realmente presentes, identificar itens divergentes e registrar o resultado.

> **Antes de começar:** Para salvar a conferência, o **Identificador do Modelo da Atividade** deve estar preenchido em Configurações › Personalizar › Integração.

**6.1.1 – Selecionando o local**
1. Selecione a opção **"Conferência"** na tela inicial;
2. Em **LOCAL A CONFERIR**, selecione o local;
3. Selecione a opção **"Continuar"**. O app carrega os itens registrados no local.

**6.1.2 – Selecionando os grupos**
A tela **GRUPOS A CONFERIR** apresenta os grupos dos itens do local, com a quantidade de itens de cada um.
- **Todos os grupos** – opção padrão: confere todos os itens do local;
- Um ou mais grupos – confere somente os itens dos grupos marcados.

Selecione a opção **"Continuar"**.

> **Nota:** Se o local não tiver itens registrados, a conferência ainda identifica os itens divergentes. Se a carga dos itens falhar, a mensagem indicará o motivo; toque na mensagem para tentar novamente.

**6.1.3 – Realizando a conferência**
A parte superior da tela apresenta o local, os grupos selecionados e o controle de potência. Abaixo, quatro cartões resumem a conferência:
- **ESPERADOS** – total de itens a conferir;
- **CONFERIDOS** – itens lidos, com o percentual em relação aos esperados;
- **PENDENTES** – itens esperados ainda não lidos;
- **DIVERGENTES** – etiquetas lidas que não pertencem ao local.

1. Selecione **"Iniciar leitura"** ou pressione o gatilho;
2. Percorra o local com o coletor. Os contadores são atualizados a cada leitura;
3. Selecione **"Parar leitura"** para interromper.

Toque em um cartão para visualizar a lista correspondente. Na lista, os itens conferidos aparecem em verde. Para fechar a lista, toque novamente no cartão ou no ✕. A leitura continua enquanto a lista está aberta.

As colunas da lista seguem a personalização do grupo definida na plataforma. Sem personalização, são apresentadas as colunas STATUS, DESCRIÇÃO e EPC. Utilize a rolagem horizontal para ver todas as colunas.

> **Nota:** Com filtro de grupos, os itens do local que pertencem a grupos não selecionados são ignorados e contados em **"Outros grupos"**. Eles não são divergentes, pois estão no local correto.

**6.1.4 – Localizando um item da lista**
Nas listas **ESPERADOS**, **CONFERIDOS** e **PENDENTES**, com a leitura parada, toque na linha do item para localizá-lo pelo **Localizador RFID** (ver seção 8.1.4). Ao retornar, a conferência continua como estava. Selecione **"Iniciar leitura"** para prosseguir.

**6.1.5 – Divergentes**
Ao abrir a lista de **DIVERGENTES**, o app consulta cada etiqueta na plataforma e apresenta a situação:
- Descrição e EPC – item cadastrado em outro local;
- **não cadastrado** – a etiqueta não está cadastrada na plataforma;
- **não consultado** – não foi possível consultar a etiqueta (falha de conexão);
- **outro grupo** – item cadastrado, de grupo fora do filtro selecionado.

Selecione **"Consultar pendentes"** para consultar novamente as etiquetas ainda não consultadas.

**6.1.6 – Consolidar divergentes**
A opção **"Consolidar divergentes"** movimenta os itens divergentes para o local conferido, na etapa Armazenamento.
- Etiquetas não cadastradas e itens de outros grupos não são movimentados;
- A confirmação e o resultado informam quantos itens foram movimentados e quantos foram ignorados, por motivo;
- A tela **Resultado da Consolidação** apresenta o resultado. Selecione **"Concluir"** para retornar.

**6.1.7 – Salvar conferência**
A opção **"Salvar conferência"** registra a conferência na plataforma como uma atividade concluída, que pode ser consultada no portal:
- Itens conferidos – esperados que foram lidos;
- Itens ausentes – esperados que não foram lidos;
- Itens divergentes – lidos que não pertencem ao local.

Durante o salvamento, a mensagem "Salvando..." é apresentada. Ao final:
- **"Conferência salva com sucesso!"** – a conferência foi registrada;
- **"Conferência registrada, mas não pode ser completada com sucesso. Verifique o histórico de conferência."** – a conferência foi criada mas não concluída. Selecione **"Salvar conferência"** novamente para concluí-la, sem gerar duplicidade.

> **Importante:**
> - Salvar a conferência não movimenta os itens (desde que o modelo da atividade não tenha "Nova etapa");
> - Todas as etiquetas divergentes devem estar consultadas antes de salvar;
> - Após salvar, a leitura é bloqueada. Para iniciar uma nova conferência, selecione **"Reiniciar"**.

**6.1.8 – Saindo da conferência**
- **Reiniciar** – inicia uma nova conferência no mesmo local;
- **Cancelar** – retorna à seleção de grupos.

Se houver leituras não salvas, o app solicitará confirmação antes de sair: "Sair descarta a conferência em andamento. Continuar?".

---

## 7. Coleta de Dados

### 7.1 – Coleta de Dados

Funcionalidade técnica para captura e análise das leituras RFID, utilizada, por exemplo, em testes de leitura e avaliação de etiquetas. As leituras não são enviadas à plataforma.

Para acessar, selecione a opção **"Coleta de Dados"** na tela inicial.

**7.1.1 – Capturando leituras**
1. Ajuste a potência, se necessário;
2. Inicie a leitura pelo botão da tela ou pelo gatilho;
3. As leituras são apresentadas no grid com as colunas:
   - **HORA** – hora da leitura;
   - **EPC** – código da etiqueta;
   - **LISTA** – lista TOI à qual o EPC pertence;
   - **RSSI** – intensidade do sinal, em dBm. Quanto mais perto de zero, mais forte o sinal.
4. Pare a leitura pelo botão ou pelo gatilho.

Os contadores **Leituras** e **EPCs distintos** são apresentados acima do grid. O grid apresenta no máximo as últimas 500 leituras.

Opções da tela:
- **Leitura única** – apresenta cada EPC uma só vez no grid. O arquivo exportado continua com todas as leituras;
- **Ver EPCs fora das listas** – disponível quando há listas TOI selecionadas. Desmarcada, oculta do grid e do arquivo os EPCs que não pertencem às listas;
- **TOI** – abre as listas de tags de interesse;
- **Limpar** – descarta as leituras capturadas;
- **Exportar** – gera o arquivo com as leituras e abre o menu de compartilhamento do Android.

> **Nota:** As opções "Leitura única" e "Ver EPCs fora das listas" ficam bloqueadas durante a leitura e valem a partir da leitura seguinte.

**7.1.2 – Arquivo exportado**
O arquivo `leituras_AAAAMMDD_HHMMSS.txt` é gravado na pasta **Downloads** do coletor e pode ser compartilhado ou copiado por USB. Cada linha do arquivo corresponde a uma leitura, com: data e hora, EPC, RSSI (dBm), fase do sinal, frequência (kHz) e canal.

### 7.2 – Listas de Tags de Interesse (TOI)

Uma lista TOI é um conjunto de EPCs identificado por um nome, criado no próprio coletor. As listas permitem filtrar e acompanhar a Coleta de Dados. Acima do grid da Coleta, o app apresenta o percentual de leitura de cada lista selecionada (EPCs distintos lidos em relação ao total da lista).

Para acessar, selecione a opção **"TOI"** na tela Coleta de Dados.

**7.2.1 – Criando uma lista**
1. Selecione a opção **"NOVA LISTA"**;
2. Informe o **Label da lista** (até 20 caracteres, ex.: ESTOQUE-A);
3. Realize a leitura das etiquetas que farão parte da lista. Os EPCs repetidos são desconsiderados. Utilize o ✕ para remover um EPC da lista;
4. Selecione a opção **"Salvar"**.

**7.2.2 – Utilizando as listas**
Marque as listas que serão usadas na coleta de dados. A seleção vale de imediato.

**7.2.3 – Editando e excluindo**
Utilize as opções **"Editar"** e **"Excluir"** da lista desejada.

---

## 8. Localizador RFID

### 8.1 – Localizador RFID

Ajuda a encontrar fisicamente um item pela intensidade do sinal da sua etiqueta.

Para acessar, selecione a opção **"Localizador RFID"** na tela inicial. O Localizador também pode ser aberto pela lista de itens das telas de conferência (ver seção 8.1.4).

**8.1.1 – Escolhendo o método de pesquisa**
Em **Pesquisar por**, selecione o método:
- **ORDEM** – o app busca na plataforma o item da ordem informada;
- **EPC** – o operador informa diretamente o EPC da etiqueta.

O app abre com o último método utilizado. Na primeira utilização, o método é **ORDEM**.

> **Nota:** O método não pode ser trocado durante a leitura. Ao trocar o método, a etiqueta procurada é desmarcada; o texto digitado em cada método é mantido.

**8.1.2 – Pesquisando pela Ordem**
1. Informe o código da **Ordem** e selecione **"Buscar"**;
2. O app apresenta o item e o **EPC Procurado**;
3. Selecione o botão de leitura ou pressione o gatilho para iniciar a busca;
4. Caminhe pelo local observando o indicador do radar. O percentual e o ícone crescem à medida que o coletor se aproxima da etiqueta.

**8.1.3 – Pesquisando pelo EPC**
1. Selecione **EPC**;
2. Informe o EPC da etiqueta e selecione **"Usar EPC"**;
3. O app apresenta o **EPC Procurado**;
4. Selecione o botão de leitura ou pressione o gatilho para iniciar a busca e siga o indicador do radar.

Regras do EPC:
- Use apenas os caracteres 0-9 e A-F. Espaços são removidos e as letras são convertidas para maiúsculas;
- O EPC deve ter um número de caracteres múltiplo de 4 (ex.: 24);
- A pesquisa pelo EPC não consulta a plataforma: funciona sem conexão de rede e localiza também etiquetas não cadastradas.

Mensagens apresentadas:
- **"Informe o EPC."** – o campo está vazio;
- **"Use apenas 0-9 e A-F."** – o EPC tem caracteres inválidos;
- **"O EPC deve ter um múltiplo de 4 caracteres (ex.: 24)."** – o tamanho do EPC é inválido.

**8.1.4 – Localizando a partir de uma lista**
Nas telas **Movimentação por Ordem de Produção** e **Conferência por Local**, é possível localizar um item da lista:
1. Com a leitura parada, toque na linha do item;
2. Uma janela apresenta a descrição do item e o EPC. Selecione **"Localizar tag RFID"**;
3. O Localizador é aberto com o **Item** e o **EPC Procurado** já preenchidos;
4. Selecione o botão de leitura ou pressione o gatilho para iniciar a busca;
5. Para retornar à conferência, utilize o botão voltar. Os itens já lidos são mantidos.

> **Nota:** Durante a leitura, o toque na linha não tem efeito. A opção só está disponível quando o Localizador RFID está marcado em Configurações › Personalizar › Funcionalidades.

Indicações apresentadas:
- **PROCURANDO ITEM** / **ITEM ENCONTRADO** – estado da busca;
- **Longe** – sinal abaixo de 40%;
- **Próximo** – sinal entre 40% e 70%;
- **Muito Próximo** – sinal acima de 70%.

Quando a etiqueta deixa de ser lida, o sinal diminui gradualmente até zero.

> **Dica:** Movimente o coletor lentamente e em diferentes direções para identificar onde o sinal é mais forte.

---

## 9. Gravação de Etiqueta

### 9.1 – Gravação de Etiqueta

Permite gravar um novo EPC em uma etiqueta RFID.

> **Importante:** A Gravação de Etiqueta altera somente a etiqueta física e não atualiza a plataforma. Para trocar a etiqueta de um item cadastrado, utilize a **Substituir Etiqueta** (seção 3.3).

> **Nota:** Nas instalações atualizadas de versões anteriores, a funcionalidade vem desmarcada. Para exibi-la na tela inicial, marque-a em Configurações › Personalizar.

Para acessar, selecione a opção **"Gravação de Etiqueta"** na tela inicial.

1. Aproxime a etiqueta a gravar e realize a leitura. O EPC lido é apresentado em **Etiqueta alvo**;
2. Informe o **Novo EPC**, em hexadecimal;
3. Se necessário, utilize **"← Zeros à esquerda"** ou **"Zeros à direita →"** para completar o EPC até 24 caracteres;
4. Selecione a opção **"Gravar"** e confirme a gravação;
5. O resultado da gravação é apresentado em uma janela, com sucesso ou falha.

Regras:
- O novo EPC deve ter de 4 a 24 caracteres hexadecimais, em múltiplos de 4;
- Após a gravação, o app relê a etiqueta para confirmar o novo EPC. A gravação só é considerada bem-sucedida após essa confirmação;
- Em caso de falha, a mensagem apresenta o código do erro.

> **Atenção:** O app grava na primeira etiqueta lida. Com várias etiquetas próximas, confira se o EPC em **Etiqueta alvo** é da etiqueta correta. Reduza a potência no controle deslizante ou afaste as demais etiquetas para isolar a etiqueta desejada.

Para reiniciar a operação, selecione a opção **"Limpar"**.

---

## 10 – Boas Práticas

### 10.1 – Antes de Iniciar:

- Verifique se o acesso à plataforma está configurado em Configurações.
-  Confirme que o coletor está conectado à rede.
-  Atualize a personalização dos grupos sempre que houver mudança na plataforma.
-  Verifique se a bateria do coletor é suficiente para a operação.

### 10.2 – Durante a Leitura:

- Pause a leitura antes de conferir os totais na tela.
- Ajuste a potência para a distância de leitura desejada: potências menores evitam a leitura de etiquetas vizinhas.
- Aguarde a conclusão das operações antes de sair da tela.

### 10.3 – Após a Conclusão:

- Verifique o resultado final da operação.
- Em caso de falha de conexão, verifique a rede e repita a operação.

---

## 11 – Resolução de Problemas

### 11.1 – "Sem conexão com a API"
- Verifique a conexão de rede do coletor.
- Confira o Host, o Login e a Senha em Configurações.
- Utilize o botão "Ir para Configurações" do alerta.

### 11.2 – "Credenciais inválidas ou API indisponível."
- Confira o usuário e a senha informados.
- Verifique se o endereço do Host está correto.
- Confirme que o servidor está disponível.

### 11.3 – O código de barras aparece duplicado no campo
- A saída por teclado do scanner está ativa. No aplicativo de configuração do scanner do coletor, ative a saída por Intent e desative a saída por teclado.

### 11.4 – A leitura do código de barras não preenche o campo
- Toque no campo de texto desejado antes de fazer a leitura.
- Verifique se o campo não é somente leitura.

### 11.5 – Uma funcionalidade não aparece na tela inicial
- Verifique se a funcionalidade está marcada em Configurações › Personalizar › Funcionalidades.

### 11.6 – O toque na linha não abre a opção "Localizar tag RFID"
- Pare a leitura antes de tocar na linha.
- Verifique se o Localizador RFID está marcado em Configurações › Personalizar › Funcionalidades.

### 11.7 – O Localizador RFID não encontra a etiqueta pelo EPC
- Confira se o EPC informado é igual ao da etiqueta.
- Aumente a potência em Configurações RFID e percorra o local lentamente.

### 11.8 – Os campos do Cadastro de Item não seguem a configuração da plataforma
- Selecione "Atualizar personalização dos grupos" em Configurações › Personalizar.

### 11.9 – "Informe o Identificador do Modelo da Atividade em Personalizar." ao salvar a Conferência por Local
- Preencha o Identificador do Modelo da Atividade em Configurações › Personalizar › Integração.

### 11.10 – "A consulta dos itens do local demorou mais de 30 segundos."
- Verifique a qualidade da conexão de rede.
- Toque na mensagem para tentar novamente.

### 11.11 – As etiquetas não são lidas
- Aumente a potência no controle deslizante da tela ou em Configurações RFID.
- Aproxime o coletor das etiquetas.
- Feche e abra novamente o app.

### 11.12 – Falha na atualização do app
- Conceda a permissão para o ITTS instalar apps e toque novamente em "Verificar atualização".
- Verifique a conexão de rede.
- Se persistir, entre em contato com o suporte técnico.